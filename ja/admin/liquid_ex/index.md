# Liquid拡張タグ

{% raw %}

本システムで追加されたLiqudのタグとフィルタです。

## タグ

### paginate

配列またはRelationオブジェクトのイテレートで、ページネートを追加します。

~~~
{% paginate site.articles per 10 %}  
    {% for article in paginate.collection %}  
    <li>{{ article.title }}</li>  
    {% endfor %}  
{% endpaginate %}
~~~

### cache

ブロック内の出力をキャッシュすることで高速に表示します。

引数にはキャッシュキーとしてオブジェクトや文字列を指定します。カンマ区切りで複数指定できます。`max_ttl` オプションで最大の有効時間（分）を指定できます。

例）キャッシュキーに固定の文字列を指定することで、常にキャッシュされた結果を出力します。この例では600秒（10分）でキャッシュはリセットされ、最新の結果が出力されます。

~~~
{% cache "cache-key", max_ttl: 600 %}  
    〜  
{% endcache %}
~~~

例）人気のタグ一覧をキャッシュして出力します。キャッシュキーとしてsiteオブジェクトを指定しているので、記事が追加、更新されるのなどサイト情報が更新されるとキャッシュは自動的にリセットされ最新情報が出力されます。

~~~
{% cache site, "site-popular-tags" %}  
    {% assign tags = site.popular_tags | limit: 20 %}  
    {% for t in tags %}  
    <a href="{{ t.path }}" class="btn btn-default btn-sm">  
    <span class="fa fa-tag fa-lg text-muted"></span>  
    {{ t.name }} ({{ t.num_articles | format_number }})</a>  
    {% endfor %}  
{% endcache %}
~~~

### file

[ファイル](../design/#files)のURLを出力します。

~~~
<img src="{% file "/logo.png" %}" alt="Logo">
~~~

### form

[フォーム](../design/#forms)を読み込みます。

~~~
{% form "vote1" %}  
~~~

### widget

[ウィジェット](../design/#widgets)を読み込みます。2つ目以降の引数でローカル変数を引き渡すことができます。

~~~
{% widget "google_analytics" %}  
{% widget "article_ad1", permalink: article.url %}
~~~

### render

[パーシャルテンプレート](../design/#templates)を読み込みます。2つ目以降の引数でローカル変数を引き渡すことができます。

~~~
{% assign ranking_articles = site.weekly_popular_articles | limit: 5 %}  
{% render "ranking", articles: ranking_articles %}
~~~

## フィルタ

### format_number

数字3桁ごとにカンマを挿入します。

~~~
{{ 12345 | format_number }}
~~~

### render_markdown

MarkdownをHTMLに変換します。

~~~
{{ user.bio | render_markdown }}
~~~

### choose_random

配列からランダムに1件または複数件取得します。

例）新着記事10件からランダムに1件を取得：

~~~
{% assign article = site.articles | limit: 10 | choose_random %}
~~~

例）新着記事10件からランダムに3件を配列で取得：

~~~
{% assign articles = site.articles | limit: 10 | choose_random: 3 %}
~~~

### shuffle

配列の要素をランダムに並べ替えます。

~~~
{% assign articles = site.articles | limit: 10 | shuffle %}
~~~

### match

正規表現とのパターンマッチを行います。マッチしたときは、マッチした部分の位置を整数で返します。マッチしなかったら、nilを返します。

~~~
{% assign secured = item.url | match: '^https:' %}
~~~

### replace_regexp

文字列の中で正規表現のパターンにマッチした部分をすべて指定の文字列に置換します。

~~~
{% assign domain = item.url | replace_regexp: '^https?://(.*?)/', '\1' %}
~~~

### auto_link

文字列中のURLをHTMLのリンクに変換します。

~~~
{{ user.bio | auto_link }}
~~~

### unescape

文字列中のHTML実体参照を元の文字列に置換します。

### where

Relationオブジェクトを指定の条件で検索して絞り込みます。

例）記事種別=1の記事を取得：

~~~
{% assign articles = site.articles | where: "article_kinds.code = '1'" %}
~~~

変数を与える場合はプレースホルダを使用してください。

~~~
{% assign articles = site.articles | where: "article_kinds.code = ?", kind_code %}
~~~

### or

Relationオブジェクトの検索条件を結合します。

例）カテゴリ「hoge」または「fuga」の記事を取得：

~~~
{% assign hoge_articles = site.articles | where: "categories.name = 'hoge'" %}  
{% assign fuga_articles = site.articles | where: "categories.name = 'fuga'" %}  
{% assign articles = hoge_articles | or: fuga_articles %}
~~~

### find_by

Relationオブジェクトから指定のフィールド値に該当する1件のオブジェクトを取得します。

例）key=xxxxxの記事を取得：

~~~
{% assign article = site.articles | find_by: 'key', 'xxxxx' %}
~~~

### limit

Relationオブジェクトの先頭から指定数を取得します。

~~~
{% assign articles = site.articles | limit: 10 %}
~~~

### offset

Relationオブジェクトの先頭から指定数より後ろを取得します。

~~~
{% assign articles = site.articles | offset: 10 %}
~~~

### order

Relationオブジェクトの並び順を変更します。

例）公開記事を更新日時の降順で取得：

~~~
{% assign articles = site.articles | order: 'last_published_at DESC' %}
~~~

### next_to

指定オブジェクトのRelationオブジェクト内における次のオブジェクトを取得します。（現在は記事オブジェクトのみ対応しています）

例）記事詳細ページでカテゴリ内公開日時降順での1つ古い記事へのリンク：

~~~
{% assign next_article = article.category.articles | next_to: article %}  
<a href="{{ next_article.path }}">前の記事</a>
~~~

### prev_to

指定オブジェクトのRelationオブジェクト内における前のオブジェクトを取得します。（現在は記事オブジェクトのみ対応しています）

例）記事詳細ページでカテゴリ内公開日時降順で1つ新しい記事へのリンク：

~~~
{% assign previous_article = article.category.articles | prev_to: article %}  
<a href="{{ previous_article.path }}">次の記事</a>
~~~

### to_array

Relationオブジェクトを明示的に配列に変換します。

### attribute

記事の拡張項目に登録されている情報を返します。

例）拡張項目「会場」の内容を表示：

~~~
{{ article | attribute: "会場" }}
~~~

### search_by_attribute

記事のRelationから拡張項目の情報を検索して絞り込みます。

例）拡張項目の完全一致で検索：

~~~
{% assign articles = site.articles | search_by_attribute: "会場", "東京都" %}
~~~

第三引数で検索式を指定できます。

~~~
{% assign articles = site.articles | search_by_attribute: "開催日", "2019-01-01", ">= ?" %}
~~~

### order_by_attribute

記事の拡張項目の情報で並び順を変更します。

例）拡張項目の降順で取得：

~~~
{% assign articles = site.articles | order_by_attribute: "開催日", "DESC" %}
~~~

### search

記事のRelationからキーワード検索します。

~~~
{% assign articles = site.articles | search: request.params["q"] %}
~~~

{% endraw %}

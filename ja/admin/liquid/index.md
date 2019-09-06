# テンプレート言語Liquid

{% raw %}

テンプレートおよびページではテンプレート言語Liquidを使用することができます。

## マークアップ

このテンプレート言語には、「出力」と「タグ」という２つの種類のマークアップがあります。

出力

```
{{ 2重の中括弧で括られます }}
```

タグ

```
{% 中括弧とパーセント記号で括られます %}
```

## 出力

出力の簡単な例を示します。

```
Hello {{name}}
Hello {{user.name}}
Hello {{ 'tobi' }}
```

### 出力の拡張「フィルタ」

出力マークアップにはフィルタを適用することができます。フィルタはシンプルなメソッドです。最初のパラメータはフィルタの左側の出力です。そのフィルタの結果がさらに次のフィルタに引き渡されます。すべてのフィルタを通ると、その結果が返されます。

```
Hello {{ 'tobi' | upcase }}
Hello tobi has {{ 'tobi' | size }} letters!
Hello {{ '*tobi*' | textilize | upcase }}
Hello {{ 'now' | date: "%Y %h" }}
```

#### 標準フィルタ

- **date** – 日時の書式を指定する。
- **capitalize** – アルファベット頭文字を大文字に変換する。
- **downcase** – アルファベットをすべて小文字に変換する。
- **upcase** – アルファベットをすべて大文字に変換する。
- **first** – 配列の最初の要素を取り出す。
- **last** – 配列の最後の要素を取り出す。
- **join** – 配列の要素を区切り文字でつなげる。
- **sort** – 配列の要素をソートする。
- **map** – 配列をmap/collectする。
- **size** – 配列または文字列のサイズを返す。
- **escape** – 文字列をHTMLエスケープする。
- **escape_once** – すでにエスケープ済みの要素を除いて文字列をHTMLエスケープする。
- **strip_html** – 文字列からHTML要素を削除する。
- **strip_newlines** – 文字列から改行（\n）を削除する。
- **newline_to_br** – 文字列の改行（\n）を`<br>`に変換する。
- **replace** – 文字列置換。 e.g. `{{ 'foofoo' | replace:'foo','bar' }}` #=> 'barbar'
- **replace_first** – 最初の1つだけ文字列置換。 e.g. `{{ 'barbar' | replace_first:'bar','foo' }}` #=> 'foobar'
- **remove** – 文字列削除。 e.g. `{{ 'foobarfoobar' | remove:'foo' }}` #=> 'barbar'
- **remove_first** – 最初の1つだけ文字列削除。 e.g. ``{{ 'barbar' | remove_first:'bar' }}`` #=> 'bar'
- **truncate** – 指定文字数で文字列を切り取る。
- **truncatewords** – 指定単語数で文字列を切り取る。
- **prepend** – 先頭に文字列を付加する。 e.g. `{{ 'bar' | prepend:'foo' }}` #=> 'foobar'
- **append** – 末尾に文字列を付加する。 e.g. `{{ 'foo' | append:'bar' }}` #=> 'foobar'
- **minus** – 引き算。 e.g. `{{ 4 | minus:2 }}` #=> 2
- **plus** – 足し算。 e.g. `{{ '1' | plus:'1' }}` #=> '11', `{{ 1 | plus:1 }}` #=> 2
- **times** – 掛け算。 e.g. `{{ 5 | times:4 }}` #=> 20
- **divided_by** – 割り算。 e.g. `{{ 10 | divided_by:2 }}` #=> 5
- **round** - 自身ともっとも近い整数もしくは実数を返す。
- **split** - マッチングパターンで文字列を分割する。 e.g. `{{ "a~b" | split:"~" }}` #=> ['a','b']
- **modulo** - 余り。 e.g. `{{ 3 | modulo:2 }}` #=> 1

## タグ

タグは、テンプレートにロジックを記述するために使用されます。

標準で次のタグを使用することができます。

- **assign** – 変数に値を代入する。
- **capture** – タグで囲んだ範囲を変数に代入するブロックタグ。
- **case** – 標準的なcase〜when文を表現するブロックタグ
- **comment** – テキストをコメントアウトするためのブロックタグ。
- **cycle** – 色やDOMのclassを設定する用途などで複数の値を順番に切り替えるために使用される。
- **for** – forループ。
- **break** - ループを抜ける。
- **continue** 現在のループをスキップして次のループへ進む。
- **if** – 標準的なif/elseブロック。
- **include** – 部分的なテンプレートなど、他のテンプレートファイルを埋め込む。
- **raw** - 構文の衝突を避けるために、一時的にタグ処理を無効にする。
- **unless** – ifの否定文。

### コメント

`comment` はシンプルなタグです。コンテンツを飲み込んで無効化するだけです。

```
我々は今年、1億円 {% comment %} の損失 {% endcomment %} を生み出した。
```

### raw

`raw` はタグ処理を一時的に無効にします。構文が衝突するコンテキストの生成（例 Mustache, Handlebars）で役立ちます。

```
{&#37; raw &#37;}
    Handlebarsで、 {{ this }} はHTMLエスケープされます、しかし {{{ that }}} ではされない。
{&#37; endraw &#37;}
```

### if / else

`if` / `else` は、あらゆるプログラミング言語でおなじみの構文です。ifまたはunlessに簡単な式を書くことができます。（オプションで`elsif`と`else`も）

```
{% if user %}
    Hello {{ user.name }}
{% endif %}
```

```
# これも同じ
{% if user != null %}
    Hello {{ user.name }}
{% endif %}
```

```
{% if user.name == 'tobi' %}
    Hello tobi
{% elsif user.name == 'bob' %}
    Hello bob
{% endif %}
```

```
{% if user.name == 'tobi' or user.name == 'bob' %}
    Hello tobi or bob
{% endif %}
```

```
{% if user.name == 'bob' and user.age > 45 %}
    Hello old bob
{% endif %}
```

```
{% if user.name != 'tobi' %}
    Hello non-tobi
{% endif %}
```

```
# これも同じ
{% unless user.name == 'tobi' %}
    Hello non-tobi
{% endunless %}
```

```
# 配列のサイズをチェック
{% if user.payments == empty %}
    you never paid !
{% endif %}
```

```
{% if user.payments.size > 0  %}
    you paid !
{% endif %}
{% if user.age > 18 %}
    Login here
{% else %}
    Sorry, you are too young
{% endif %}
```

```
{% if user.age > 18 %}
    Login here
{% else %}
    Sorry, you are too young
{% endif %}
```

```
# array = 1,2,3
{% if array contains 2 %}
    array includes 2
{% endif %}
```

```
# string = 'hello world'
{% if string contains 'hello' %}
    string includes 'hello'
{% endif %}
```

### case文

さらに多くの条件分岐が必要なら、`case` 文を使うことができます。

```
{% case condition %}
{% when 1 %}
    hit 1
{% when 2 or 3 %}
    hit 2 or 3
{% else %}
    ... else ...
{% endcase %}
```

例:

```
{% case template %}
{% when 'label' %}
    // {{ label.title }}
{% when 'product' %}
    // {{ product.vendor | link_to_vendor }} / {{ product.title }}
{% else %}
    // {{ page_title }}
{% endcase %}
```

### cycle

しばしば、異なる色や似たタスクを交互に切り替えたい場合があります。そのために `cycle` タグを用意しています。

```
{% cycle 'one', 'two', 'three' %}
{% cycle 'one', 'two', 'three' %}
{% cycle 'one', 'two', 'three' %}
{% cycle 'one', 'two', 'three' %}
```

結果）

```
one
two
three
one
```

サイクルグループに名前を指定しない場合は、同じパラメータを持つ複数の呼び出しが1つのグループであるとみなされます。

サイクルグループを操作したい場合は、グループに名前を指定することができます。これは変数でも良いです。

```
{% cycle 'group 1': 'one', 'two', 'three' %}
{% cycle 'group 1': 'one', 'two', 'three' %}
{% cycle 'group 2': 'one', 'two', 'three' %}
{% cycle 'group 2': 'one', 'two', 'three' %}
```

結果）

```
one
two
one
two
```

### forループ

配列を使った `for` ループを行うことができます。

```
{% for item in array %}
    {{ item }}
{% endfor %}
```

ハッシュのイテレートでは item[0] にはキー、item[1] には値が入ります。

```
{% for item in hash %}
    {{ item[0] }}: {{ item[1] }}
{% endfor %}
```

ループの中では次のヘルパー変数を使用することができます。

```
forloop.length      # => ループの長さ
forloop.index       # => 現在のインデックス
forloop.index0      # => 現在のインデックス（0始まり）
forloop.rindex      # => 残り項目数
forloop.rindex0     # => 残り項目数（0始まり）
forloop.first       # => 最初のイテレーション？
forloop.last        # => 最後のイテレーション？
```

指定できるいくつかの属性があります。

- **limit:int** 項目の最大数  
- **offset:int** 開始インデックス位置

```
# array = [1,2,3,4,5,6]
{% for item in array limit:2 offset:2 %}
    {{ item }}
{% endfor %}
# 結果) 3,4
```

ループを反転させる。

```
{% for item in collection reversed %}
    {{item}}
{% endfor %}
```

既存のコレクションの代わりに、数値範囲の定義でループすることもできます。範囲はリテラルまたは変数のどちらでも定義することができます。

```
# if item.quantity is 4...
{% for i in (1..item.quantity) %}
    {{ i }}
{% endfor %}
# 結果) 1,2,3,4
```

ループでは項目がなかった時に表示するテキストブロック`else`の指定ができます。

```
# items => []
{% for item in items %}
    {{ item.title }}
{% else %}
    There are no items!
{% endfor %}
```

### 変数の割り当て

出力マークアップや他のタグで使用するために、変数にデータを保存することができます。変数を作るための最も簡単な方法は`assign`タグです。とても簡単な文法です。

```
{% assign name = 'freestyle' %}

{% for t in collections.tags %}{% if t == name %}
    <p>Freestyle!</p>
{% endif %}{% endfor %}
```

他の方法としては、`true` / `false`を変数に割り当てることです。

```
{% assign freestyle = false %}

{% for t in collections.tags %}{% if t == 'freestyle' %}
{% assign freestyle = true %}
{% endif %}{% endfor %}

{% if freestyle %}
    <p>Freestyle!</p>
{% endif %}
```

多くの文字列を結合して変数に取り込みたい場合は、`capture`タグを使用することができます。このタグは、その中でレンダリングされることなら何でも「キャプチャ」して、画面に表示する代わりに指定の変数に代入します。

```
{% capture attribute_name %}{{ item.title | handleize }}-{{ i }}-color{% endcapture %}

<label for="{{ attribute_name }}">Color:</label>
<select name="attributes[{{ attribute_name }}]" id="{{ attribute_name }}">
<option value="red">Red</option>
<option value="green">Green</option>
<option value="blue">Blue</option>
</select>
```

{% endraw %}

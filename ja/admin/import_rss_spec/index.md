# 外部記事受け入れRSS仕様

対応フォーマットはRSS 2.0です。

## 必須項目

- rss/channel/item/link
- rss/channel/item/title
- rss/channel/item/description（または content:encoded）

`rss/channel/item/content:encoded`がある場合は、`rss/channel/item/description`は使用されません。

## 推奨項目

- rss/channel/item/pubDate
- rss/channel/item/enclosure[@url]

`rss/channel/item/enclosure`は記事を代表する画像のURLを指定してください。記事一覧のサムネイル等で使用されます。この項目がない場合は、記事本文中の最初のimg要素から抽出します。

## 例

~~~
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">
    <channel>
    <title>サイト名</title>
    <link>http://example.com/</link>
    <description>サイトの説明</description>
    <item>
        <title>記事２の見出し</title>
        <link>http://example.com/article/2.html</link>
        <guid>A002</guid>
        <pubDate>Tue, 24 Feb 2015 00:00:00 +0900</pubDate>
        <description>
        <![CDATA[<p>記事２の全文HTML</p>]]>
        </description>
        <enclosure url="http://example.com/article/2.jpg">
    </item>
    <item>
        <title>記事１の見出し</title>
        <link>http://example.com/article/1.html</link>
        <guid>A001</guid>
        <pubDate>Tue, 24 Feb 2015 00:00:00 +0900</pubDate>
        <description>
        <![CDATA[<p>記事１の全文HTML</p>]]>
        </description>
        <enclosure url="http://example.com/article/1.jpg">
    </item>
    ・・・・
    </channel>
</rss>
~~~

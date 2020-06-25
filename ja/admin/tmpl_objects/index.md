# オブジェクトリファレンス

テンプレートやページで参照できるオブジェクトとメソッドです。

## Article（記事）

記事をあらわすオブジェクトです。

記事詳細ページでは`article`で表示中の記事を参照できます。

### add_favorite_path

お気に入りへ追加する処理のURLパス。

### category

記事にカテゴリが指定されていれば、Categoryオブジェクト。

### comments

記事へ投稿された公開済みのCommentオブジェクトのRelation。

### comments_path

コメントページのURLパス。

### description

記事説明。

### distributor

外部から配信された記事であれば、配信元Distributorオブジェクト。

### image_is_empty

記事画像が登録されていなければtrue。

### image_large_url

記事画像のURL（1280px）。

### image_medium_url

記事画像のURL（640px）。

### image_small_url

記事画像のURL（320px）。

### image_square_url

記事画像のURL（150x150px正方形）。

### image_thumbnail_url

記事画像フルURL（75x75px正方形）。

### is_favorite

閲覧者（自分）がお気に入り登録済みであればtrue。

### is_published

公開中の記事であればtrueを返す。

### items

記事項目の配列。

### kinds

記事種類コードの配列。

### new_comment_path

コメント投稿ページのURLパス。

### num_comments

公開済みのコメントの数。

### num_favorites

お気に入り登録数。

### num_views

閲覧数（PV）。

### ordered_tags

記事に結び付けられたTagオブジェクトの配列。（指定順）

### path

記事のURLパス。

### permalink

Permalink ID（記事ページURLの固有文字列）。

### published_at

公開日時。

### relevance_articles

関連する記事ArticleオブジェクトのRelation。

### remove_favorite_path

お気に入りから解除する処理のURLパス。

### source_url

外部から配信された記事であれば、元記事のURL。

### tags

記事に結び付けられたTagオブジェクトの配列。（多く使われている順）

### title

記事タイトル

### updated_at

改訂日時。

### url

記事のフルURL。

### user

記事作成者のUserオブジェクト。

## AttributeField（記事拡張項目）

記事拡張項目をあらわすオブジェクトです。

`site.attribute_fields`ですべての拡張項目を参照できます。

### name

項目名。

### options

選択項目の選択肢の文字列配列。

### type

項目種類。

## Category（カテゴリ）

カテゴリをあらわすオブジェクトです。

カテゴリページ（トップページでカテゴリを選択した状態）では`category`で表示中のカテゴリを参照できます。

### ancestors

祖先カテゴリ。上位階層のすべてのCategoryオブジェクトの配列。

### articles

記事ArticleオブジェクトのRelationを記事公開日時の降順で取得。

### children

サブカテゴリ。1階層下のCategoryオブジェクトの配列。

### comments

カテゴリに属する記事へ投稿された公開済みのCommentオブジェクトのRelation。

### daily_popular_articles

記事ArticleオブジェクトのRelationを24時間以内のページビューの多い順に取得。

### descendants

子孫カテゴリ。階層下のすべてのCategoryオブジェクトの配列。

### description

カテゴリ説明。

### icon_path

アイコン画像のURLパス。

### icon_url

アイコン画像のURL。

### image_large_url

カテゴリ画像のURL（1280px）。

### image_medium_url

カテゴリ画像のURL（640px）。

### image_small_url

カテゴリ画像のURL（320px）。

### image_square_url

カテゴリ画像のURL（150x150px正方形）。

### image_thumbnail_url

カテゴリ画像のURL（75x75px正方形）。

### monthly_popular_articles

記事ArticleオブジェクトのRelationを1ヶ月以内のページビューの多い順に取得。

### name

名称

### num_articles

記事の数。

### num_comments

カテゴリに属する記事へ投稿された公開済みのコメントの数。

### parent

親カテゴリ。1階層上のCategoryオブジェクト。

### path

カテゴリページのURLパス。

### permalink

Permalink ID（カテゴリページURLの固有文字列）。またはカテゴリ名（name）。

### popular_tags

このカテゴリでよく使われているタグTagオブジェクトの配列。

### private_articles

非公開記事ArticleオブジェクトのRelationを公開日時の降順で取得。

### reserved_articles

公開日前の記事のArticleオブジェクトのRelationを公開日時の昇順で取得。

### url

カテゴリページのフルURL。

### weekly_popular_articles

記事ArticleオブジェクトのRelationを1週間以内のページビューの多い順に取得。

## Collection（コレクション）

コレクションをあらわすオブジェクトです。

### name

コレクションの一意キーとなる名前

### label

コレクションの名称

### items

コレクション子要素. CollectionItemオブジェクトのRelation。

## CollectionItem（コレクションアイテム）

コレクションの子要素をあらわすオブジェクトです。

### article

コレクションアイテム（記事）が指定されている場合は、Articleオブジェクト。

### caption

コレクションアイテムのキャプション、HTML本文など

### image_small_path

コレクションアイテム画像のパス（320px）

### image_small_url

コレクションアイテム画像のURL（320px）

### image_large_path

コレクションアイテム画像のパス（1280px）

### image_large_url

コレクションアイテム画像のURL（1280px）

### image_medium_path

コレクションアイテム画像のパス（640px）

### image_medium_url

コレクションアイテム画像のパURL（640px）

### image_square_path

コレクションアイテム画像のパス（150x150px正方形）

### image_square_url

コレクションアイテム画像のパURL（150x150px正方形）

### image_thumbnail_path

コレクションアイテム画像のパス（75x75px正方形）

### image_thumbnail_url

コレクションアイテム画像のパスURL（75x75px正方形）

### image_path

コレクションアイテム画像のパス（オリジナルサイズ）

### image_url

コレクションアイテム画像のURL（オリジナルサイズ）

### label

コレクションアイテムの名称、タイトルなど

### path

コレクションアイテムのパス

### type

コレクションアイテムの種類（CollectionItemArticle, CollectionItemImageなど）

### url

コレクションアイテムのURL

## Controller（コントローラ）

すべてのテンプレートおよびページから`controller`で参照できます。

### breadcrumbs

パンくずリスト要素の配列を取得します。

### render_breadcrumbs

パンくずリスト描画HTMLを取得。

### response_status

HTTPステータスコードを返す。

### signed_in

ログイン中であればtrueを返す。


## Comment（コメント）

記事へのコメントをあらわすオブジェクトです。

### body

コメント本文。

### created_at

コメントの投稿日時。

### sender

投稿者のニックネーム。

## Distributor（記事受け入れ配信元）

外部記事配信元をあらわすオブジェクトです。

### image_path

ロゴ画像URLパス。

### image_url

ロゴ画像フルURL。

### name

名称。

### url

配信元サイトURL。

## Item（記事項目）

記事項目をあらわすオブジェクトです。

### render

描画HTMLを取得。

## Site（サイト）

サイトをあらわすオブジェクトです。

すべてのテンプレートおよびページから`site`で参照できます。

### accept_comment

記事にコメントを受け付ける設定になっていればtrue。

### all_categories

子を含むすべてのCategoryオブジェクトのRelation。

### articles

記事ArticleオブジェクトのRelationを、記事公開日時の降順で取得。

### attribute_fields

すべての記事拡張項目AttributeFieldオブジェクトのRelation。

### categories

最上位階層のカテゴリCategoryオブジェクトの配列。

### comments

記事へ投稿された公開済みのCommentオブジェクトのRelation。

### curators

ライターであるUserオブジェクトのRelation。

### collections

コレクションであるCollectionオブジェクトのRelation。

### daily_popular_articles

記事ArticleオブジェクトのRelationを24時間以内のページビューの多い順に取得。

### daily_popular_users

UserオブジェクトのRelationを、作成記事の24時間以内のページビューの多い順に取得。

### description

サイト説明。

### favicon_path

faviconのURLパス。

### favicon_url

faviconのフルURL。

### image_large_url

サイト画像のURL（1280px）。

### image_medium_url

サイト画像のURL（640px）。

### image_small_url

サイト画像のURL（320px）。

### image_square_url

サイト画像のURL（150x150px正方形）。

### image_thumbnail_url

サイト画像URL（75x75px正方形）。

### logo_mobile_small_url

スマホ用ロゴ画像のURL。

### logo_small_url

PC用ロゴ画像のURL。

### manageable

閲覧者（自分）がサイト管理者であればtrue。

### monthly_popular_articles

記事ArticleオブジェクトのRelationを1ヶ月以内のページビューの多い順に取得。

### monthly_popular_tag_pages

タグオブジェクトのRelationを1ヶ月以内のページビューの多い順に取得。

### monthly_popular_users

UserオブジェクトのRelationを、作成記事の1ヶ月以内のページビューの多い順に取得。

### name

名称

### num_comments

記事へ投稿された公開済みのコメントの数。

### path

サイトのURLパス。

### popular_articles

記事ArticleオブジェクトのRelationを1週間以内のページビューの多い順に取得。

### popular_tags

3ヶ月以内に投稿された記事に付けられた記事につけられたタグTagオブジェクトのRelationを、記事の多い順で取得。

### private_articles

非公開記事ArticleオブジェクトのRelationを記事作成日時の降順で取得。

### reserved_articles

公開日前の記事のArticleオブジェクトのRelationを公開日時の昇順で取得。

### tags

登録されているタグTagオブジェクトのRelation。

### title

サイトタイトル。

### top_title

トップページ用のサイトタイトル。

### total_popular_articles

記事ArticleオブジェクトのRelationを全期間のページビューの多い順に取得。

### touch_icon_url

スマホアイコン画像のフルURL。

### url

サイトトップページのURL。

### weekly_popular_articles

記事ArticleオブジェクトのRelationを1週間以内のページビューの多い順に取得。

### weekly_popular_users

UserオブジェクトのRelationを、作成記事の1週間以内のページビューの多い順に取得。

## Tag（タグ）

タグをあらわすオブジェクトです。

### ancestors

祖先タグ。上位階層のすべてのTagオブジェクトの配列。

### articles

タグに紐づく、記事のRelation。

### children

サブタグ。1階層下のTagオブジェクトの配列。

### daily_popular_articles

記事ArticleオブジェクトのRelationを24時間以内のページビューの多い順に取得。

### descendants

子孫タグ。階層下のすべてのTagオブジェクトの配列。

### description

タグ説明。

### has_image

タグに画像が設定されていればtrueを返す。

### image_large_url

タグ画像のURL（1280px）。

### image_medium_url

タグ画像のURL（640px）。

### image_small_url

タグ画像のURL（320px）。

### image_square_url

タグ画像のURL（150x150px正方形）。

### image_thumbnail_url

タグ画像URL（75x75px正方形）。

### monthly_popular_articles

記事ArticleオブジェクトのRelationを1ヶ月以内のページビューの多い順に取得。

### name

タグ名

### num_articles

記事の数

### path

カテゴリページのURLパス。

### parent

親タグ。1階層上のTagオブジェクト。

### private_articles

非公開記事ArticleオブジェクトのRelationを公開日時の降順で取得。任意のタグに紐づいた公開記事が1つ以上あることで、オブジェクトを取得可能。

### reserved_articles

公開日前の記事のArticleオブジェクトのRelationを公開日時の昇順で取得。

### url

カテゴリページのURL。

### related_tags

関連するタグの配列。（対象のタグが付けられた記事でよく使われる他のタグ）

### weekly_popular_articles

記事ArticleオブジェクトのRelationを1週間以内のページビューの多い順に取得。

## Request（HTTPリクエスト）

HTTPリクエストをあらわすオブジェクトです。

すべてのテンプレートおよびページから`request`で参照できます。

### current_page

現在のページ番号を取得。

### fullpath

クエリー文字列を含むリクエストパス

### is_desktop

is_mobileとis_tabletの両方がfalseの時にtrueを返す。

### is_mobile

スマートフォンからのアクセスの時にtrueを返す。

### is_tablet

タブレットからのアクセスの時にtrueを返す。

### url

リクエストURL

### path

リクエストパス

## system（システム）

システムをあらわすオブジェクトです。

### domain

ドメイン名（ホスト名）

### root_path

システムのトップページURLパス

### url

システムのトップページURL

## User（ユーザー）

ユーザーをあらわすオブジェクトです。

### add_follower_path

ユーザーをフォローする処理へのURLパス。

### articles

ライターに紐づく、記事のRelation。

### bio

自己紹介。

### email

メールアドレス。

### favorite_articles

お気に入りの記事のRelation。

### followees

フォローされているユーザーのRelation。

### followers

フォローしているユーザーのRelation。

### image_medium_url

ユーザー画像のURL（256x256px正方形）。

### image_small_url

ユーザー画像のURL（48x48px正方形）。

### is_admin

特権管理者ならtrue。

### is_curator

ライターならtrue。

### is_follower

フォローしていればtrue。

### is_official

公式アカウントならtrue。

### name

表示用の名前。nicknameが登録されていればnickname、登録されていなければemailの@の前部分。

### nickname

ニックネーム。

### num_views

ユーザーの記事のPV数。site.*_popular_usersで取得したUserオブジェクトでのみ使用可能。

### path

ユーザーページのURLパス。

### private_articles

ライターに紐づく非公開記事のRelationを公開日時の降順で取得。

### reserved_articles

記事のArticleオブジェクトのRelationを公開日時の昇順で取得。

### remove_follower_path

ユーザーのフォローを解除する処理へのURLパス。

### url

ユーザーページのフルURL。

### user_kinds

ユーザー種別コードの配列。

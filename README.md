# Clipkitガイド : 公式ドキュメント

## 公開サイトへのデプロイ

`gh-pages` ブランチ内のファイルを更新すると、自動的にビルドされ、以下のURLにデプロイされます。

[https://clipkit.co/docs/](https://clipkit.co/docs/)

## Dockerによるローカル環境

準備

```
% git clone git@github.com:ragru/docs.git
% cd docs
```

起動

```
% docker-compose up
```

http://localhost:4000/docs/ でアクセスできます。

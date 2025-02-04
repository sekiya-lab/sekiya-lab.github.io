# Sekiya Lab WebSite

## システム構成
- Jekyll
  - コンテンツ管理
- GitHub Pages
  - ホスティングサービス

## ディレクトリ構成
- `_includes` (Jekyll の include ファイル)
  - `footer.html` (ページフッター)
  - `head.html` (HTML head 部分)
  - `header.html` (ページヘッダー)
  - `home-cards.html` (TOPページのカラム表示部分)
  - `page-nav.html` (ナビゲーション付きページ用)
- `_layouts` (Jekyll のレイアウトファイル)
  - `base.html` (共通レイアウト)
  - `home.html` (TOPページ用レイアウト)
  - `page-with-nav.html` (ナビゲーション付きページ用レイアウト)
  - `page.html` (通常のページ用レイアウト)
- `_posts` (ブログポストコンテンツ)
- `assets` (画像/JS/CSS)
- `_config.yml` (Jekyll 設定ファイル)
- `index.md` (TOPページ)
- `*.md` (各ページ)
- `404.html` (404ページ)

## 更新方法
### ページ更新/追加
各ページは `.md` ファイルとして Markdown 形式で編集できます。

各 md ファイルの最初に Front Matter でページで利用するレイアウトやページ名などのメタデータを設定します。
```md
---
layout: page
title: ページ名
---
```

Front Matter で定義できる設定は以下を参照してください。
- https://jekyllrb.com/docs/front-matter/

### TOPページカラム
TOPページカラム部分は `index.md` ではなく、`_config.yml` で編集できます。

`_config.yml` の `home_cards` に以下のフォーマットで各カラムの内容を記述できます。
```yaml
home_cards:
  - title: カラムのタイトル
    description: カラム内のコンテンツ
    links:
      - title: リンク名 (画像の alt に利用)
        url: http://example.com (リンク先のURL)
        image: sample.png (画像)
```
カラムの表示は `_includes/home-cards.html` によって制御されます。

### ヘッダーナビゲーション
ヘッダーナビゲーションは `_config.yml` で編集できます。

`_config.yml` の `header_pages` にヘッダーナビゲーションに表示するページのファイル名を記載します。
出力されるヘッダーナビゲーションの HTML には、各ファイルの Front Matter で定義されたページ名や URL を利用します。

```yaml
header_pages:
  - index.md
  - contacts.md
```

### ナビゲーション付きページ用レイアウト
ナビゲーション付きページ用レイアウトを利用することで、ページ内ナビゲーションを追加できます。

`page-with-nav` レイアウトを指定すると、ページ内のリンクリストが自動生成されます。
```md
# page-a.md
---
layout: page-with-nav
title: ページ名
---
```

ナビゲーションのリンク一覧は `_config.yml` の `page_navs` で設定できます。
`page_navs` にナビゲーション付きページ用レイアウトを利用するページのファイル名の項目を追加して、
その下に title / id の一覧を追加するとページ内のリンクリストとして表示されます。

```yaml
# _config.yml
page_navs:
  page-a: (ナビゲーション付きページ用レイアウトを利用するページのファイル名)
    - title: 見出し1
      id: example-1 (リンク先の HTML の id)
    - title: 見出し2
      id: example-2
  page-b:
    ...
```


## デプロイ
GitHub Actions を利用して `main` ブランチに push すると、GitHub Pages に自動デプロイされます。
```sh
$ git push origin main
```

GitHub Actions のワークフローは以下のファイルで管理されています。

- GitHub Action Workflow
  - [jekyll.yml](.github/workflows/jekyll.yml)


## 開発環境
### Requirements
- Ruby 3.4.1 (ref: [.ruby-version](.ruby-version) )
- Jekyll

### Install
- install gems
```sh
$ bundle install --path vendor/bundle
```

### Build & Test
- コンテンツを編集
  - `*.md` (Markdown 形式)

- HTML をビルド
```sh
$ bundle exec jekyll build
```

- ローカルサーバーを起動
  - http://localhost:4000/ で確認可能
```sh
$ bundle exec jekyll server
```


## 参考URL
### Jekyll
- ドキュメント
  - https://jekyllrb.com/docs/

### GitHub Pages
- GitHub Pages について
  - https://docs.github.com/ja/pages/getting-started-with-github-pages/about-github-pages
- カスタムドメイン設定
  - https://docs.github.com/ja/pages/configuring-a-custom-domain-for-your-github-pages-site

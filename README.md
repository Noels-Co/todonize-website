# Todonize Website

公開サイト [todonize.noelsandco.com](https://todonize.noelsandco.com) のソース。

## 内容

- `index.md` — トップページ
- `legal/` — Privacy Policy / Terms of Service (ja/en)
- `_config.yml` — Jekyll 設定
- `CNAME` — Custom domain (todonize.noelsandco.com)
- `HOSTING_SETUP.md` — GitHub Pages + DNS の初期セットアップ手順

## デプロイ

`main` ブランチに push すると GitHub Pages が自動的に再ビルドして公開します。
GitHub Settings → Pages で `main` / `/(root)` をソースに設定済み。

## ローカルプレビュー (任意)

```bash
bundle install
bundle exec jekyll serve
```

`http://localhost:4000` でアクセス可能。

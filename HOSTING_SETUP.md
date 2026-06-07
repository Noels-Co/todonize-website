# GitHub Pages ホスティング セットアップ手順

この repo (`Noels-Co/todonize-website`) を `todonize.noelsandco.com` で公開する手順です。

## 0. 前提
- リポジトリ: `Noels-Co/todonize-website` (Public, GitHub Pages 利用可)
- 公開ディレクトリ: repo の root
- 独自ドメイン: `todonize.noelsandco.com` (`noelsandco.com` から切り出し)
- Jekyll で MD → HTML 変換 (GitHub Pages 標準)

## 1. GitHub 側設定 (ブラウザで実施、約 2 分)

1. https://github.com/Noels-Co/todonize-website/settings/pages を開く
2. **Source** で「Deploy from a branch」を選択
3. **Branch**: `main` / フォルダ: `/(root)` を選択 → **Save**
4. Custom domain 欄に `todonize.noelsandco.com` を入力 → **Save**
5. しばらく待ち、「Enforce HTTPS」がチェック可能になったらオン

## 2. DNS 設定 (`noelsandco.com` の DNS 管理画面で)

| Type | Name | Value | TTL |
|---|---|---|---|
| **CNAME** | `todonize` | `noels-co.github.io.` | 3600 (1時間) |

末尾の `.` は DNS プロバイダによっては不要 (自動付与される)。

### A レコード方式 (代替、CNAME が使えない場合)
```
Type  Name        Value
A     todonize    185.199.108.153
A     todonize    185.199.109.153
A     todonize    185.199.110.153
A     todonize    185.199.111.153
```

## 3. 動作確認 (5-30 分後)

DNS 伝播後:

- https://todonize.noelsandco.com/ → トップページ
- https://todonize.noelsandco.com/legal/privacy/ja/ → プライバシーポリシー (ja)
- https://todonize.noelsandco.com/legal/privacy/en/ → Privacy Policy (en)
- https://todonize.noelsandco.com/legal/terms/ja/ → 利用規約 (ja)
- https://todonize.noelsandco.com/legal/terms/en/ → Terms of Service (en)
- 鍵マークが付いて HTTPS で表示される

## 4. トラブルシューティング

### 「Improperly configured」と GitHub Pages に出る
- DNS 伝播が未完了 (`dig todonize.noelsandco.com` で CNAME が返るか確認)
- Custom domain 欄から削除して、保存後、もう一度設定し直す

### HTTPS が有効化できない
- 「Enforce HTTPS」のチェックボックスがグレー: TLS 証明書発行待ち、5-30 分待つ
- 1 時間以上待ってもダメな場合は、Custom domain 欄を一旦消して再設定

### 404 になる
- `_config.yml` で `baseurl` が空 (`baseurl: ""`) であることを確認
- 各 .md の permalink が正しいか確認

### Jekyll ビルドエラー
- GitHub Actions タブで build log を確認
- ローカルで `bundle exec jekyll build` でテスト可能

## 5. 将来の他サービス追加

別アプリの公開サイトを追加する場合:

```
新しい repo: Noels-Co/<nextapp>-website
DNS: <nextapp>.noelsandco.com  CNAME → noels-co.github.io.
```

→ 完全に独立した運用が可能。

## 6. 会社サイト (noelsandco.com ルート) を作る場合

別 repo (例: `Noels-Co/website`) を作成し:

```
DNS: noelsandco.com         A レコード → GitHub Pages IP (185.199.108-111.153)
     www.noelsandco.com     CNAME → noels-co.github.io.
```

サブドメインの Todonize 用設定とは完全独立。

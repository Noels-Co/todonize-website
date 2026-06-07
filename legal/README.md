# Legal documents for Todonize App Store release

このディレクトリには、App Store リリースに必要な以下の法務文書のドラフトが含まれます。

## ファイル一覧

| ファイル | 内容 | 言語 |
|---|---|---|
| `privacy-policy-en.md` | Privacy Policy | 英語 |
| `privacy-policy-ja.md` | プライバシーポリシー | 日本語 |
| `terms-en.md` | Terms of Service (利用規約 + サブスク規約) | 英語 |
| `terms-ja.md` | 利用規約 (利用規約 + サブスク規約) | 日本語 |

サブスクリプション利用条件 (Apple Guideline 3.1.2 要件) は Terms of Service 内の Section 4 に統合しています。独立した EULA ドキュメントは不要です。

## ホスティング手順 (デプロイ前タスク)

1. **TBD 項目を埋める**:
   - 連絡先メールアドレス
   - 施行日 (App Store リリース日)
2. **ホスティング先決定**: GitHub Pages 推奨 (`https://noels-works.github.io/todonize/...`)
3. **Markdown → HTML 変換**: GitHub Pages の Jekyll もしくは `pandoc`、もしくはサイトジェネレータで HTML 化
4. **URL 確定後の作業**:
   - App Store Connect の Privacy Policy URL に登録 (#43 E3)
   - `PaywallView` の placeholder URL を実 URL に置換 (`Terms of Service` / `Privacy Policy` リンク先)
   - README にリンク追記
5. **公開**: PR レビュー後に main へ merge、GitHub Pages を有効化

## 注意

- **法務確認推奨**: 弁護士チェックを受けることが望ましい (特に責任制限・準拠法条項)
- **App Review**: Apple Reviewer は Privacy Policy URL が有効か実際にチェックします
- **将来の更新**: 「最終更新日」を変更し、必要に応じてユーザーに通知

## 参考

- [Apple App Store Review Guideline 3.1.2 (Subscriptions)](https://developer.apple.com/app-store/review/guidelines/#3.1.2)
- [Apple App Store Review Guideline 5.1.1 (Data Collection and Storage)](https://developer.apple.com/app-store/review/guidelines/#5.1.1)
- [Apple's Privacy Best Practices](https://developer.apple.com/app-store/user-privacy-and-data-use/)

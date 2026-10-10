# Unfold Kit

2026 年秋の App Store と iPhone Duo の変更に備えるための、無料・登録不要のブラウザツール集です。ビルド不要の静的 HTML だけでできています。フォルダを使わない構成なので、GitHub のブラウザ画面からファイルを選ぶだけでアップロードできます。`vercel.json` の `cleanUrls` で `/asset-press` のような URL になります。

## ツール

### Asset Press(`asset-press.html` → `/asset-press`)

App Store の新しいクリエイティブ素材と iPhone Duo のスクリーンショットを作ります。

- プロダクトページヘッダー 3840×1646(21:9)
- 検索結果アセット 3840×2560(3:2)
- ユニバーサルアセット 5244×2950(16:9、PNG のみ)
- App内イベント カード 1920×1080 / 詳細 1080×1920
- iPhone Duo スクリーンショット 外側 1398×2034・内側 2007×2853(縦横)

特徴

- PNG は **アルファチャンネルなしの RGB** で書き出し(ブラウザ標準の書き出しは RGBA になるため、独自のエンコーダーを内蔵)
- Apple 公式 Sketch テンプレートの「ART SAFE AREA」を実測した範囲を表示し、文字を自動でその中に収める
- 価格・URL・著作権記号・Apple の表彰表記・他プラットフォーム名などを提出前に警告
- 画像処理はすべてブラウザ内。サーバーへ送信しない

### Fold Planner(`fold-planner.html` → `/fold-planner`)

アプリの種類(17 種)と特徴を選ぶと、iPhone Duo の 6 つのポーズ(閉じた状態、開いた状態の横・縦、半開きのブック・テーブルトップ、Split View)での推奨レイアウトを同じ縮尺の図で示し、API 名つきの実装チェックリストを出します。チェックリストは Markdown でコピー・保存できます。

## 公開方法

### GitHub Pages

1. このフォルダを GitHub の公開リポジトリに push
2. Settings → Pages → Branch を `main` / `(root)` に設定

### Vercel

```sh
npx vercel --prod
```

Framework Preset は「Other」、Build Command と Output Directory は空のままで動きます。

## ローカルで動かす

```sh
npx serve .
# または
python3 -m http.server 8000
```

## 出典と注意

- サイズ・ルールは Apple の App Store Connect Help(Screenshot specifications / Creative assets specifications)、Human Interface Guidelines「Designing for iPhone Duo」、および [Blake Crosley 氏のまとめ](https://blakecrosley.com/blog/app-store-product-page-marketing-2026) をもとにしています(2026 年 10 月時点)。
- セーフエリアは Apple が数値を公表していないため、公式テンプレートからの実測値です。最終確認は App Store Connect のプレビューツールで行ってください。
- iPhone Duo 内側ディスプレイのポイント値(669×951)は、スクリーンショット寸法からの推定です。
- Apple、App Store、iPhone は Apple Inc. の商標です。このプロジェクトは Apple とは関係のない非公式ツールです。

## ライセンス

MIT

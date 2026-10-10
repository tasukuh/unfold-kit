# Unfold Kit

Free, sign-up-free browser tools for the fall 2026 App Store changes and iPhone Duo. Available in English, Japanese, Korean and German.

The site is plain static HTML with no build step and no folders, so you can upload it from the GitHub web UI. `vercel.json` turns on `cleanUrls`, which serves the tools at `/asset-press` and `/fold-planner`.

[日本語は下にあります](#日本語)

## Tools

### Asset Press (`asset-press.html` → `/asset-press`)

Makes the App Store's new creative assets and iPhone Duo screenshots.

- Product page header 3840×1646 (21:9)
- Search results asset 3840×2560 (3:2)
- Universal asset 5244×2950 (16:9, PNG only)
- In-app event card 1920×1080 and details 1080×1920
- iPhone Duo screenshots: outer 1398×2034 and inner 2007×2853, portrait or landscape

Features

- Exports PNGs as **RGB with no alpha channel**. Browsers write RGBA by default, so the tool ships its own PNG encoder.
- Shows the "ART SAFE AREA" measured from Apple's Sketch template and fits text inside it automatically.
- Warns before submission about prices, URLs, copyright symbols, Apple recognitions and other platforms' names, in all four languages.
- All image processing happens in the browser. Nothing is uploaded.

### Fold Planner (`fold-planner.html` → `/fold-planner`)

Pick an app category (17 types) and what applies to your app. It draws recommended layouts for six iPhone Duo poses at the same scale: closed; open in landscape and portrait; half-folded as a book and on a tabletop; and Split View. It also generates an implementation checklist with API names, which you can copy or save as Markdown in the selected language.

## Languages

Each page detects the language from `?lang=` (`ja`, `en`, `ko`, `de`), then from the last choice saved in the browser, then from the browser's language. It falls back to English. The selector in the header switches language and keeps the choice across pages.

## Deploy

**Vercel**: Import the repository, choose Framework Preset "Other" and leave the build command and output directory empty.

**GitHub Pages**: Settings → Pages → Branch `main` / `(root)`.

## Run locally

```sh
npx serve .
```

## Sources and caveats

- Sizes and rules come from Apple's App Store Connect Help (screenshot and creative asset specifications), the Human Interface Guidelines page "Designing for iPhone Duo", and [Blake Crosley's write-up](https://blakecrosley.com/blog/app-store-product-page-marketing-2026), as of October 2026.
- Apple doesn't publish safe areas in pixels. The values here are measured from Apple's template, so confirm the final result with the preview tool in App Store Connect.
- The inner display's point size (669×951) is inferred from the screenshot dimensions.
- The Korean and German translations were machine-assisted. Corrections are welcome as issues or pull requests.
- Apple, App Store and iPhone are trademarks of Apple Inc. This project is unofficial and not affiliated with Apple.

## License

MIT

---

## 日本語

2026 年秋の App Store と iPhone Duo の変更に備えるための、無料・登録不要のブラウザツール集です。日本語・英語・韓国語・ドイツ語に対応しています。

- **Asset Press**(`/asset-press`): プロダクトページヘッダー、検索結果アセット、ユニバーサルアセット、App内イベント画像、iPhone Duo スクリーンショットを、規定サイズのアルファなし PNG で書き出します。Apple テンプレートのセーフエリア表示と、提出前チェックの機能があります。画像の処理はすべてブラウザ内で行い、サーバーには送りません。
- **Fold Planner**(`/fold-planner`): アプリの種類を選ぶと、iPhone Duo の 6 つのポーズでの推奨レイアウトを同じ縮尺の図で示し、API 名つきの実装チェックリストを出します。チェックリストは Markdown でコピー・保存できます。

言語は URL の `?lang=ja` などで指定できます。指定がなければ、前回選んだ言語、ブラウザの言語の順に決まります。

注意: セーフエリアは公式テンプレートからの実測値で、内側ディスプレイのポイント値はスクリーンショット寸法からの推定です。Apple、App Store、iPhone は Apple Inc. の商標で、このプロジェクトは Apple とは関係のない非公式ツールです。

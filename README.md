# zenn-to-pdf
This tool uses puppeteer to export zenn article as PDF.
In order to use the top-level `await` feature, you need to use Node version newer than `14.8.0`.

## install

```
$ npm install
```

## set environment variables

以下が`ZENN_PAGE_URL`を取得する方法になります。
> ちなみに隠し機能的な感じですが、本のURLの末尾を/printにすると印刷用のページが開きます。無料の本や、購入した本であれば、1ページにすべてのチャプターが表示されます。
> https://github.com/zenn-dev/zenn-roadmap/issues/82#issuecomment-699568915

`dotenv`を利用しているので、カレントファイルに`.env`ファイルを作成し、以下の環境変数を設定してください。
IS_TWO_FAはデフォルトが`true`になっています。Zennのログインに利用するGoogleアカウントの2FAを有効にしていない場合は、`IS_TWO_FA`を`false`で設定してください。

```
$ mv .env.tmplate .env
GOOGLE_EMAIL=<GOOGLE_EMAIL>
GOOGLE_PASSWORD=<GOOGLE_PASSWORD>

# zenn article print page url
ZENN_PAGE_URL=https://zenn.dev/zenn/books/how-to-create-book/print

# option: default is `prod.pdf`.
PDF_PATH=prod.pdf

# option: default is `true`. If your google account has enabled 2FA, this option must be true.
IS_TWO_FA=true

# option: Default is `APP`. You can choose `APP` or `SMS`.
TWO_FA_TOOL=APP

# option: Default is `true`. If you have an issue to run the export, you can disable `headless` mode and see the broser window.
HEADLESS=true
```

## export

2FAを有効にしている場合は`G-code`を入力する必要があります。

```
$ npm run export

> zenn-to-pdf@1.0.0 export /Users/ganezasan/repos/private/zenn-to-pdf
> node export.mjs

Opening chromium browser...
Access zenn.dev ...
Enter email ...
Enter password ...
Use 2FA with challengetype: APP
Enter your G-code: ******
Enter 2FA code...
Access Zenn page...
Access artile print page...
Export PDF...
The article was successfully exported to PDF 🎉
export: /Users/ganezasan/repos/private/zenn-to-pdf/prod.pdf
```

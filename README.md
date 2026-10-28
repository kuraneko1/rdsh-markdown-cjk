# rdsh-markdown-cjk

> [English](README.en.md)

URL の直後に日本語が続いても、リンクが壊れないようにする DSH Web プラグインです。
`**https://example.com**（メモ）` のような太字も正しく閉じます。

## インストール

```sh
dsh plugin --profile web add github:kuraneko1/rdsh-markdown-cjk
```

追加したあと DSH を再起動してください。

無効にするときは、プロファイルの `cordis.patch.yml` で
`config: { enabled: false }`、または環境変数 `RDSH_MARKDOWN_CJK=0`。

## 変更前 / 変更後

| 変更前 | 変更後 |
| --- | --- |
| ![before](docs/before.png) | ![after](docs/after.png) |

## 動作の仕組み

フロントエンドの vendor チャンクを配信時にパッチして /markdown-cjk/v1/ から返します。DSH のビルドやパッチ版が変わると URL も変わるため、古い成果物が残りません。形が合わないチャンクは無加工で配信し、標準の描画を保ちます。

## 関連プロジェクト

[dsh-mobile-maxxing](https://github.com/kuraneko1/dsh-mobile-maxxing) は、モバイル UX・通知・表・日本語化を独立したコンポーネントとして提供するプロジェクトです。PC の Markdown 描画を変えない方針を保つため、CJK の自動リンク修正は統合版には含めず、このパッケージとして独立して維持しています。

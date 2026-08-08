# clock-weather-widget

iPhone 6 (iOS 12, Wi-Fiのみ) の常時表示用「時刻+気温」ページ。

## 公開URL

https://hiroshindo.github.io/clock-weather-widget/

## 機能

- 時刻: `HH:mm` 形式、1秒ごとに更新
- 気温・湿度・風速: `nn.n℃ nn% n.nm` 形式(気温はマイナスの時だけ `-` を付与、風速はゼロパディングなし)、気象庁アメダスから取得、10分ごとに更新
- 観測点は吹田市に最も近いアメダス「豊中」(観測点コード62051)に固定
- オフライン時(`navigator.onLine === false`)はfetchをスキップし「オフライン」表示
- iOS 12 Safari互換(fetch, padStartのみ使用、ES5構文中心)
- `apple-mobile-web-app-capable` 対応でホーム画面追加時にフルスクリーン起動

## セットアップ

1. GitHubにpush → GitHub Pages (branch: main, path: /) で自動公開
   - 気象庁アメダスAPIはキー不要・登録不要のため、他の準備は不要
   - 観測点を変える場合は `index.html` 内の `AMEDAS_STATION` を
     https://www.jma.go.jp/bosai/amedas/const/amedastable.json で調べたコードに変更

## iPhone側の設定

1. **Safariで**URLを開く(Chromeで追加するとフルスクリーンにならないので注意。`apple-mobile-web-app-capable` はSafari専用の仕様で、Chrome経由のホーム画面追加ではURLバー付きのまま起動してしまう)
2. 共有ボタン → 「ホーム画面に追加」
3. 追加したアイコンから起動するとフルスクリーン表示

## 注意点

- `file://` で直接開くとfetchがブロックされる可能性が高いため、GitHub Pages経由での利用が前提
- アメダスは10分おきの定時観測のみで、観測点コードが存在しない・欠測の場合は「取得失敗」表示になる

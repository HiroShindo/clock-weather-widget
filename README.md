# clock-weather-widget

iPhone 6 (iOS 12, Wi-Fiのみ) の常時表示用「時刻+気温」ページ。

## 公開URL

https://hiroshindo.github.io/clock-weather-widget/

## 機能

- 時刻: `HH:mm` 形式、1秒ごとに更新
- 気温: `nn.n℃` 形式(マイナスの時だけ `-` を付与)、OpenWeatherMapから取得、10分ごとに更新
- 緯度経度は吹田市付近に固定(LAT=34.7615, LON=135.5158)
- オフライン時(`navigator.onLine === false`)はfetchをスキップし「オフライン」表示
- iOS 12 Safari互換(fetch, padStartのみ使用、ES5構文中心)
- `apple-mobile-web-app-capable` 対応でホーム画面追加時にフルスクリーン起動

## セットアップ

1. https://openweathermap.org/api でアカウント作成し、無料APIキーを取得
   - 発行直後は有効化まで最大2時間ほどかかることがある(すぐ401が出ても待てば通る)
2. `index.html` 内の `API_KEY` にキーを設定
3. GitHubにpush → GitHub Pages (branch: main, path: /) で自動公開

## iPhone側の設定

1. **Safariで**URLを開く(Chromeで追加するとフルスクリーンにならないので注意。`apple-mobile-web-app-capable` はSafari専用の仕様で、Chrome経由のホーム画面追加ではURLバー付きのまま起動してしまう)
2. 共有ボタン → 「ホーム画面に追加」
3. 追加したアイコンから起動するとフルスクリーン表示

## 注意点

- リポジトリはpublicのため、`index.html` 内のAPIキーもソースとして公開される。OpenWeatherMap無料キーの実害は小さいが、他人に使われるとレート制限を消費する可能性がある
- `file://` で直接開くとfetchがブロックされる可能性が高いため、GitHub Pages経由での利用が前提

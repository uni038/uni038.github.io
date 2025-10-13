# Web API
[Web API | MDN](https://developer.mozilla.org/ja/docs/Web/API)

## (Attributioin Reporting API)⚠️
## (Audio Output Devices API)⚠️

## (Background Fetch API)⚠️
## Background Synchronization API
オフラインのときに処理を延期し、オンラインになったときにサービスワーカーで実行する

## Background Tasks API
タスクをキューに入れ、空き時間があるときに実行できる

## Badging API
バッジを表示する

## (Barcode Detection API)⚠️
バーコード、QRコードを画像内から読み取る

## Battery Status API
バッテリーの情報を取得する

## Beacon API
ビーコン（サーバーに非同期＆ノンブロッキングで送信する、レスポンスを求めないリクエスト）を送る

## (Web Bluetooth API)⚠️
## Broadcast Channel API
`BroadcastChannel`オブジェクトを通じて、オリジンが同じであるブラウズコンテキスト間で基本的な通信ができる

## CSS Custom Highlight API
## CSS Font Loading API
## (CSS Painting API)⚠️
## CSS Properties and Values API
## CSS Typed Object Model API
## CSS Object Model (CSSOM)
## ⭐️Canvas API
`<canvas>`要素に2Dグラフィックを描画する
```js
const canvas = document.getElementById("my-house");
const ctx = canvas.getContext("2d");
ctx.fillRect(130, 190, 40, 60);
```

## Channel Messaging API
同じドキュメントにアタッチされた2つのブラウズコンテキスト間で通信できる？

## Clipboard API
```js
navigator.clipboard
  .readText()
  .then(
    (clipText) => (document.querySelector(".editor").innerText += clipText),
  );
```

## Compression Streams API
データの圧縮

## (Compute Pressure API)⚠️
## Console API
`console.log()`など

## (Contact Picker API)⚠️
## (Content Index API)⚠️
## Cookie Store API
クッキーを管理する

## Credential Management API
アカウントなどの資格情報の管理

## ⭐️Document Object Model (DOM)
DOM一般

## Device Memory API
端末のRAM情報

## Device orientation events
端末の方向や動きの検知
- 画面の方向とは別。

## (Device Posture API)⚠️
## (Document Picture-in-Picture API)⚠️

## (EditContext API)⚠️
## Encoding API
文字エンコーディング

## Encrypted Media Extensions API
## (EyeDropper API)⚠️

## (Federated Credential Management (FedCM) API)⚠️
## (Fenced Frame API)⚠️
## ⭐️Fetch API
リソースの取得
`fetch()`, `Request,` `Response`

## File API
file型の`<input>`要素かドラッグドロップによってファイルが利用可能になったときにファイルにアクセスできる。
```js
const fileInput = document.querySelector("input[type=file]");
const output = document.querySelector(".output");

fileInput.addEventListener("change", () => {
  const [file] = fileInput.files;
  if (file) {
    const reader = new FileReader();
    reader.addEventListener("load", () => {
      output.innerText = reader.result;
    });
    reader.readAsText(file);
  }
});
```

## File System API
端末のファイルシステム上のファイルにアクセスする

## File and Directory Entries API
ファイルシステムのシミュレート？

## (Force Touch events)⚠️
## ⭐️Fullscreen API (フルスクリーンAPI)

## Gamepad API
## Geolocation API (位置情報API)
`navigator.geolocation`

## Geometry interfaces
画像を操作するための幾何学的インターフェース

## ⭐️The HTML DOM API
HTMLのDOM

## HTML Drag and Drop API (HTMLドラッグドロップAPI)
HTML要素をドラッグ・ドロップ操作できる。

## (HTML Sanitizer API)⚠️
## History API
ブラウザの履歴にアクセスする

## Houdini APIs
CSSを拡張できるAPIらしい

## (Idle Detection API)⚠️
## MediaStream Image Capture API
映像デバイスから画像・動画をキャプチャする

## IndexedDB API
大量のデータをクライアント側で保存するための低レベルAPI

## (Ink API)⚠️
## (InputDeviceCapabilities API)⚠️
## (Insertable Streams for MediaStreamTrack API)⚠️
## Intersection Observer API
2つの要素の相対的な可視状態を検出する

## Invoker Commands API

## (JS Self-Profiling API)⚠️

## (Keyboard API)⚠️

## (Launch Handler API)⚠️
## (Local Font Access API)⚠️

## Media Capabilities API
デバイスのメディアに対する対応状況を取得する

## Media Capture and Streams API (MediaStream)
メディアストリーム

## Media Session API
## Media Source API
## MediaStream Recording API

## (Navigation API)⚠️
## Network Information API
ネットワーク接続情報

## Page Visibility API
ページが現在見えているかを取得する

## (Payment Handler API)⚠️
## Payment Request API
## Performance APIs
Webアプリの動作パフォーマンス測定を行う

## (Web Periodic Background Synchronization API)⚠️
## Permissions API
APIの利用許可状態を確認する

## Picture-in-Picture API
ピクチャーインピクチャー（動画を他のページの上に表示し続ける）
- ブラウザの外にも表示できる...

## Pointer events
マウス以外のポインティングデバイスに対応する

## Pointer Lock API
カーソルの絶対位置だけでなく動作を検出できる

## Popover API
ポップオーバー（他のページの上に表示するコンテンツ）

## (Presentation API)⚠️
## Prioritized Task Scheduling API
## Push API
Webアプリがサーバーからメッセージ（Push）を受信する

## Remote Playback API
リモートデバイス上でのメディア再生を制御する

## Reporting API
## Resize Observer API
要素のリサイズを検出する

## SVG API
## ⭐️Screen Capture API (画面キャプチャAPI)
ウィンドウや画面全体をキャプチャする

## Screen Orientation API (画面方向API)
## Screen Wake Lock API (画面起動ロックAPI)
端末が画面を暗くしたりロックするの防ぐ方法を提供する

## Selection API
ユーザーが選択している部分を取得する

## Sensor APIs
端末のセンサー

## ⭐️Server-sent events
サーバーからページにプッシュ送信する
```js
const evtSource = new EventSource("ssedemo.php");
evtSource.onmessage = (event) => {
  const newElement = document.createElement("li");
  const eventList = document.getElementById("list");

  newElement.textContent = `message: ${event.data}`;
  eventList.appendChild(newElement);
};
```
- Push APIはサービスワーカーなのでページを開いていなくても通信できる、SSEはページを開いている必要がある、という違いらしい

## ⭐️Service Worker API
サービスワーカー（オリジン固有のプロキシ）
- ウェブワーカーの一種

## (Shared Storage API)⚠️
## (Speculation Rules API)⚠️
## Storage API
IndexedDB API、Cache API、Web Storage APIなどのウェブサイト用に格納されたデータを管理する

## Storage Access API
クロスオリジンなコンテンツがファーストパーティストレージにアクセスする方法を提供する
- サードパーティクッキーの代替手段

## Streams API
データのストリーミング

## (Summarizer API)⚠️

## (Topics API)⚠️
## Touch events
## (Translator and Language Detector APIs)⚠️
## Trusted Types API
XSS対策用のサニタイジング

## UI Events
UIイベント

## URL API
URL

## URL Fragment Text Directives
## URL Pattern API
URLパターンマッチャー

## (User-Agent Client Hints API)⚠️

## Vibration API
端末のバイブレーション

## View Transition API
ビュー遷移時のアニメーション

## (VirtualKeyboard API)⚠️
## Visual Viewport API

## ⭐️Web Animations API
DOM要素のアニメーション

## Web Audio API
音声全般

## Web Authentication API
Credential Management APIの拡張。認証を行う

## Web Components
## Web Crypto API
低レベルな暗号化機能

## Web Locks API
ロック機構の提供

## Web MIDI API
## (Web NFC API)⚠️
## ⭐️Notifications API (通知API)
システムレベルの通知機能へのアクセス

## (Web Serial API)⚠️
## ⭐️Web Share API
いわゆる「コンテンツの共有」機能

## Web Speech API
音声認識

## Web Storage API
クライアントにキーと値のペアを格納できる。Cookieと違い、サーバーには明示的に送信しない限り送信されない
- `Window.sessionStorage`
  - セッション中持続する保存領域
  - Cookieよりも容量が大きい(最大5MB)
- `Window.localStorage`
  - ブラウザを閉じても持続する保存領域

## ⭐️Web Workers API
ウェブワーカー（バックグラウンドスレッド）
- 時間がかかる処理を移す
- サービスワーカーはウェブワーカーの一種である

## WebCodecs API
## ⭐️WebGL: 2D and 3D graphics for the web
## WebGPU API
## (WebHID API)⚠️
## (WebOTP API)⚠️
## ⭐️WebRTC API
ブラウザー間で直接通信する

## ⭐️The WebSocket API (WebSockets)
ブラウザとサーバ間で対話的な通信をする

## WebTransport API
## (WebUSB API)⚠️
## (WebVR API)⚠️
## WebVTT API
## (WebXR Device API)⚠️
## (Window Controls Overlay API)⚠️
## (Window Management API)⚠️

## XMLHttpRequest API

## (fetchLater() API)⚠️



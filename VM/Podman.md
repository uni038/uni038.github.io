# Podman

> https://docs.podman.io/en/latest/


## イメージ
- `podman build` イメージをビルドする
- `podman commit` 変更されたコンテナから新しいイメージを生成する
- `podman history` イメージのヒストリを表示する
- `podman image` イメージ管理
- `podman images` ローカルのイメージを一覧する
- `podman load` tarからイメージをロードする
- `podman login` コンテナレジストリにログインする
- `podman logout` コンテナレジストリからログアウトする
- `podman pull` レジストリからイメージをpullする
- `podman push` イメージをどこかにpushする
- `podman rmi` ローカルのイメージを削除する
- `podman save` イメージをアーカイブに保存する
- `podman search` レジストリからイメージを探す
- `podman tag` ローカルのイメージに名前を付ける
- `podman untag` tagの逆


## コンテナ
- `podman container` コンテナ管理
  - _
- `podman attach` 実行中のコンテナにアタッチする
- `podman auto-update` コンテナを自動アップデートする
- `podman create` コンテナを生成する
- `podman healthcheck`　コンテナのヘルスチェック管理
- `podman init` コンテナを初期化する
- `podman kill` 実行中のコンテナにシグナルを送りkillする
- `podman logs` コンテナのログを取得する
- `podman port` コンテナのポートマッピングを一覧する
- `podman ps` コンテナを一覧する
- `podman rename` 存在しているコンテナをリネームする
- `podman restart` コンテナをリスタートする
- `podman rm` コンテナを削除する
- `podman start` コンテナをスタートする
- `podman stats` コンテナのリソース消費統計を表示する
- `podman stop` コンテナを停止する
- `podman update` 存在しているコンテナをアップデートする

## コンテナ内プロセス
- `podman exec` 実行中のコンテナ内でプロセスを実行する
- `podman pause` コンテナ内のすべてのプロセスを一時停止する
- `podman unpause` pauseの逆
- `podman run` 新しいコンテナでコマンドを実行する
- `podman top` コンテナで実行中のプロセスを表示する
- `podman wait` コンテナをブロックする

## コンテナのファイル
- `podman cp` ローカルとコンテナの間でファイルをコピーする
- `podman diff` コンテナまたはイメージのファイルの差分を取る
- `podman export` コンテナのファイルをtarにエクスポートする
- `podman import` tarからインポート
- `podman mount` コンテナのファイルシステムをホストにマウントする？
- `podman unmount` mountの逆

## Podman
- `podman events` podmanのシステムイベントを表示する
- `podman info` podmanのシステム情報を表示する


## ?
- `podman farm`
- `podman generate`　
- `podman inspect` IDで指定したオブジェクトの設定を表示する
- `podman kube`
- `podman machine` 仮想マシン管理
- `podman manifest`
- `podman network` ネットワーク管理
- `podman pod` pod管理
- `podman secret` 機微情報の管理
- `podman system` podmanの管理
- `podman unshare` 修正したuser namespaceでコマンドを実行する？
- `podman version` podmanのバージョン情報を表示する
- `podman volume` ボリュームの管理

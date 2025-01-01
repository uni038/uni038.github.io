# Docker Compose
> https://docs.docker.com/compose/

> CLI Reference\
> https://docs.docker.com/reference/cli/docker/compose/


## イメージ
- `docker compose images` 生成済みのコンテナが使用しているイメージを一覧する
- `docker compose pull` サービスのイメージをpullする
- `docker compose push` サービスのイメージをpushする

## サービス
- `docker compose build` サービスをビルドする
- `docker compose down` コンテナとネットワークを停止・削除する
- `docker compose up` コンテナを生成・開始する
- `docker compose start` サービスを開始する
- `docker compose stop` サービスを終了する
- `docker compose restart` サービスのコンテナをリスタートする
- `docker compose pause` サービスを一時停止する
- `docker compose unpause` サービスを再開する
- `docker compose wait` 指定したサービスのコンテナが終了するまでブロックする

## コンテナ関連
- `docker compose ps` コンテナを一覧する
- `docker compose cp` ファイルをローカルからサービスのコンテナにコピーする
- `docker compose create` サービス用のコンテナを生成する
- `docker compose events` コンテナからリアルタイムイベントを受信する
- `docker compose exec` 実行中のコンテナ内でコマンドを実行する
- `docker compose kill` サービスのコンテナをキルする
- `docker compose logs` コンテナからの出力を見る
- `docker compose rm` 停止済みのサービスのコンテナを削除する

- `docker compose run` ワンオフなコマンドをサービス上で実行する


## 情報
- `docker compose config` composeファイルの正規化
- `docker compose ls` 実行中のcompose projectを一覧する
- `docker compose alpha` 試験的なコマンド
- `docker compose top` 実行中のプロセスを表示する
- `docker compose port` ポートバインディング中のパブリックポートを表示する
- `docker compose version` Docker Composeのバージョンを表示する
- `docker compose watch` ？

## compose.yaml
> Compose file reference
> https://docs.docker.com/reference/compose-file/

- `name`
- `services`
  - `image`
  - `build`
  - `volume`
  - `ports`
  - `expose`
  - `depends_on`
  - `environment`
  - `env_file`
  - `networks`
  - `configs`
  - `container_name`
  - `init`
  - `restart`
- `networks`
- `volumes`
- `configs`
- `secrets`

# nginx
```
/etc/nginx
├ nginx.conf        # メイン設定
├ mime.types        # MIMEタイプ定義
├ fastcgi_params    # 
├ uwsgi_params      # 
├ scgi_params       # 
├ conf.d/           # 追加設定
│ └ *.conf
├ sites-available/  # 使用可能な設定
│ └ …
└ sites-enabled/    # 有効化されている設定
  └ …
```

- ルートブロック
  - (main)
    - `user`, `worker_processes`, `error_log`, `env` など
  - events
    - コネクションに関する設定
  - http
    - HTTPに関する設定 (Webサーバ)
    - `upstream`
    - `server`
      - `listen`
      - `server_name`
        - ホスト名。リクエストのHostヘッダを見てマッチするserverで処理する
        - 完全一致>先頭ワイルドカード>末尾ワイルドカード>正規表現>デフォルト の順でマッチする
      - `ssl_certificate`
      - `location`
        - `root` ドキュメントルート
        - `index` デフォルトのファイル
        - `access_log`, `error_log`
        - `error_page`
        - `proxy_pass`
        - `return`
        - `limit_except`
        - `internal`
  - mail
    - メールプロキシとしての設定
  - stream
    - TCP/UDPレベルのプロキシ、ロードバランサなど

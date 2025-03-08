# sshdのセットアップ
> OpenSSH: Manual Pages\
> https://www.openssh.com/manual.html


## サーバ
1. sshdをインストール
2. sshd_configを編集する
  - 各種認証方法を許可する
  - 必要ならリモートルートログインを許可する
3. クライアントの公開鍵をサーバに登録する。
  - `~/.ssh/authorized_keys`
4. sshdを再起動する


## クライアント
1. 鍵がなければ生成する。
2. 鍵をサーバに登録する。
3. 必要なら `~/.ssh/config` にSSH接続設定を書く。
4. 必要なら `~/.ssh/known_hosts` を整理する。


## トラブルシュート
- sshdに認証方式を設定したか
- rootの場合、リモートルートログインを許可しているか
- サーバに公開鍵を登録しているか
- sshdは再起動したか
- クライアント側の PreferredAuthentication は想定した設定になっているか
- 古いサーバ指紋が残ってないか
- ローカルの秘密鍵のパーミッションは適切か

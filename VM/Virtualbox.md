# Virtualbox
## ネットワークアダプタ
||ゲスト→外部|ゲスト間|ゲスト→ホスト||
|-|-|-|-|-|
|<font color="blue">NAT</font>|O|X|※|「ルーターモード」
|ブリッジアダプター|O|O|O|「ブリッジモード」？
|<font color="green">内部ネットワーク</font>|X|O|X|「内部ネットワーク」
|<font color="green">ホストオンリーアダプター</font>|X|O|O|「プライベートネットワーク」
|汎用ドライバ|?|?|?|
|<font color="blue">NATネットワーク</font>|O|O|※|「ルーターモード」

### NAT
- ゲストからNATで外部と通信する
- 外部からのアクセスはホストでポートフォワーディングが必要
- ゲスト間通信不可（→NATネットワーク）
- IP固定？
- 完全に隠蔽されるわけではないらしい

### ブリッジアダプター (OKだが要IPアドレス採番)
- ホストと同じサブネットのアドレスを割り当てる

### 内部ネットワーク (OK)
- 内部ネットワークを作成しゲスト間で通信
- 外部接続不可

### ホストオンリーアダプター
- ホスト上に仮想NICを新規に作成し、ゲスト - ホスト間通信が可能
- ゲスト間通信も可能
- ゲスト - 外部通信は不可

### 汎用ドライバ

### NATネットワーク
- ゲスト間通信できるNAT (ゲスト側でネットワーク設定は必要)

## その他
- 自動インストールはスキップする

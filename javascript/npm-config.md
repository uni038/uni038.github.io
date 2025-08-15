# npm config (.npmrc)
https://docs.npmjs.com/cli/v11/configuring-npm/npmrc

```sh
npm config set <key>=<value> [<key>=<value> ...]
npm config get [<key> [<key> ...]]
npm config delete <key> [<key> ...]
npm config list [--json]
npm config edit
npm config fix
```
alias: c

## npmrc file
- 場所
  - プロジェクト: /path/to/my/project/.npmrc
  - ユーザー: $HOME/.npmrc
  - グローバル: $PREFIX/etc/npmrc
  - ビルトイン（システム）: /path/to/npm/npmrc
- 形式は以下
  ```txt
  key = value
  ```
  配列は`[]`を付ける
  ```txt
  key[] = "first value"
  key[] = "second value"
  ```
- 環境変数使用可 (`${ENV}`)
- 行頭の`#`または`;`はコメント
- ローカルでのみ適用される。レジストリやインストール先では適用されない




# npm (Node Package Manager)
version: 11.5.2

- Node.jsに同梱されている
- npm public registry https://registry.npmjs.org/


## パッケージ指定規則
```
[<@scope>/]<pkg>
[<@scope>/]<pkg>@<tag>
[<@scope>/]<pkg>@<version>
[<@scope>/]<pkg>@<version range>
```


## コマンド
"*"はワークスペースに紐づかないコマンド。
- プロジェクト (package.json)
  - npm init
  - npm dist-tag : 配布用タグの編集
  - npm pkg : package.jsonの管理
  - npm version : パッケージのバージョンを上げる
- インストール関連のコマンド
  - npm ci : クリーンインストール
  - npm edit  * : インストールされているパッケージをエディタで開く
  - npm explore  * : インストールされているパッケージのディレクトリを見る
  - npm install
  - npm install-ci-test
  - npm install-test
  - npm link : パッケージのリンクの作成
  - npm ls
  - npm outdated : インストールされているパッケージが古いかどうかレジストリに確認する
  - npm rebuild
  - npm uninstall
  - npm update
- レジストリ関連のコマンド
  - ~~npm access~~  *
  - npm adduser  *
  - npm deprecate / npm undeprecate  * : レジストリのパッケージを更新しdeprecatedにする
  - npm login  *
  - npm logout  *
  - npm ping  *
  - npm profile  *
  - npm publish / npm unpublish
  - npm star / npm unstar / npm stars  *
- パッケージ関連のコマンド
  - npm bugs : パッケージのバグトラッカーをブラウザで開く
  - npm diff : パッケージのdiffを取る
  - npm docs : パッケージのドキュメントをブラウザで開く
  - npm pack : パッケージのtarballを作成
  - npm repo : パッケージのリポジトリをブラウザで開く
  - npm search  *
  - npm view : レジストリからパッケージの情報を取得して表示
- 依存関係関連のコマンド
  - npm audit : 依存パッケージのセキュリティ監査
  - npm dedupe
  - npm explain
  - npm find-dupes
  - npm prune
  - npm query
  - npm shrinkwrap  *
- 実行
  - npm exec : パッケージからコマンドを実行する
  - npm restart
  - npm run
  - npm start
  - npm stop
  - npm test
  - npx
- ユーティリティ
  - npm cache  *
  - npm completion  *
  - npm config  *
  - npm doctor  * : npmのインストールが正しくされているか確認する
  - npm fund
  - npm help  *
  - npm help-search  *
  - npm org  *
  - npm owner : パッケージのオーナーを変更する
  - npm prefix  * : 現在のpackage.jsonの親ディレクトリのパスを取得
  - npm root  * : 現在のnode_modulesのパスを取得
  - npm sbom
  - npm team  *
  - npm token  *
  - npm whoami  *

### コマンドのconfig指定
- コマンドラインで `--foo bar` とすると、`foo`というconfigを`bar`に設定する。
- コマンドラインで `--foo` とすると、`foo`という設定を `true` に設定する。
- `--` で、以降の引数をコマンドに渡す。


### `npm access` *
### `npm adduser` *
レジストリに新しいユーザーを作成し、クレデンシャルを .npmrc に保存する。

### `npm audit`
### `npm bugs`
### `npm cache` *
### `npm ci`
クリーンインストールする
- package-lock.json または npm-shrinkwrap.json が必須。
- プロジェクト全体のインストールのみ可能。個別インストール不可
- 既存の node_modules は削除される

### `npm completion` *
### `npm config` *
```sh
npm config set <key>=<value> [<key>=<value> ...]
npm config get [<key> [<key> ...]]
npm config delete <key> [<key> ...]
npm config list [--json]
npm config edit
npm config fix
```
- alias: c

### `npm dedupe`
### `npm deprecate` *
レジストリのパッケージを更新しdeprecatedにする。
```sh
npm deprecate <package-spec> <message>
```

- `npm undeprecate`

### `npm diff`
### `npm dist-tag`
### `npm docs`
### `npm doctor` *
### `npm edit` *
### `npm exec`
```sh
npm exec -- <pkg>[@<version>] [args...]
npm exec --package=<pkg>[@<version>] -- <cmd> [args...]
npm exec -c '<cmd> [args...]'
npm exec --package=foo -c '<cmd> [args...]'
```
- alias: x
- 

### `npm explain`
print the chain of dependencies causing a given package to be installed in the current project
```sh
npm explain <package-spec>
```
- alias: why

### `npm explore` *
### `npm find-dupes`
### `npm fund`
### `npm help` *
### `npm help-search` *

### `npm init`
package.jsonの作成
```sh
npm init <package-spec> (same as `npx create-<package-spec>`)
npm init <@scope> (same as `npx <@scope>/create`)
```
- aliases: create, innit
- オプション
  - `--init-author-name`
  - `--init-author-url`
  - `--init-license`
  - `--init-module`
  - `--init-type`
    - package.jsonのtypeの値。デフォルトはcommonjs
  - `--init-version`
  - `--init-private`
    - package.jsonのprivate。デフォルトはfalse
  - `--yes`
  - `--force`
  - `--scope`
  - `--workspace`
  - `--workspaces`
  - `--workspaces-update`
  - `--include-workspace-root`


### `npm install` / `npm uninstall`
```sh
npm install [<package-spec> ...]
```
- aliases: add, i, in, ins, inst, insta, instal, isnt, isnta, isntal, isntall
- パッケージをインストールする。
- インストールされるパッケージに以下のファイルがある場合はそれに従う。（上が優先）
  - `npm-shrinkwrap.json`
  - `package-lock.json`
  - `yarn.lock`
- パッケージとは以下のものを指す。
  - `package.json`のあるディレクトリ (a)
  - (a)を含むtarball (b)
  - (b)を指すURL (c)
  - (c)というURLでレジストリにpublishされている`<name>@<version>` (d)
  - (d)を指す`<name>@<tag>` (e)
  - (e)にlatestタグがある場合、`<name>`
  - (a)を指すgitリモートURL
- コマンド
  - `npm install`
    - パッケージのディレクトリ内で実行すると、package.jsonのdependenciesに書かれているパッケージをnode_modulesディレクトリにインストールする。
    - `--production`を付けると、devDependenciesはインストールしない
  - `npm install <folder>`
    - folderが現在のプロジェクトのルートにあるなら、そのdependenciesをプロジェクトのトップレベルにインストールする
    - そうでないなら、folderへのsymlinkを作る
  - `npm install [@<scope>/]<name>`
    - `<name>@<tag>`をインストールする。tagはconfigから取る。
    - scopeはレジストリを識別する文字列。
    - `-P, --save-prod` : dependenciesに入れる。デフォルト
    - `-D, --save-dev` : devDependenciesに入れる
    - `--save-peer` : peerDependenciesに入れる
    - `-O, --save-optional` : optionalDependenciesに入れる
    - `--no-save` : dependenciesに入れない
  - `npm install [<@scope>/]<name>@<tag>`
  - `npm install [<@scope>/]<name>@<version>`
  - `npm install [<@scope>/]<name>@<version range>`
  - `npm install <git-remote-url>`
    - git-remote-urlの形式は以下。protocolは`git`, `git+ssh`, `git+http`, `git+https`, `git+file`
      ```
      <protocol>://[<user>[:<password>]@]<hostname>[:<port>][:][/]<path>[#<commit-ish> | #semver:<semver>]
      ```
  - `npm install <githubname>/<githubrepo>[#<commit-ish>]`
  - `npm install github:<githubname>/<githubrepo>[#<commit-ish>]`
    - https://github.com/githubname/githubrepoからクローンしてインストールする。
- コマンドラインフラグ
  - `save` (true) : dependenciesに追加する
  - `save-exact` (false): dependenciesに正確なバージョンで追加する
  - `global` (false) : グローバルにインストールする

- `npm uninstall`


### `npm install-ci-test`
npm ci & npm test

### `npm install-test`
npm install & npm test

### `npm link`
パッケージのリンク
```sh
npm link [<package-spec>]
```
- alias: ln
- パッケージフォルダで引数なし実行した場合、現在のパッケージへのリンクをグローバルに作成する。
- グローバルのパスは`npm prefix -g`で確認できる
- `npm link <package-spec>`
  - 現在のディレクトリの node_modules に、グローバルへのリンクを作成する

### `npm login` *
### `npm logout` *
### `npm ls`
list installed packages
```sh
npm ls <package-spec>
```
alias: list

### `npm org` *
### `npm outdated`
### `npm owner`
### `npm pack`
create a tarball
### `npm ping` *

### `npm pkg`
manage your `package.json`
```sh
npm pkg set <key>=<value> [<key>=<value> ...]
npm pkg get [<key> [<key> ...]]
npm pkg delete <key> [<key> ...]
npm pkg set [<array>[<index>].<key>=<value> ...]
npm pkg set [<array>[].<key>=<value> ...]
npm pkg fix
```


### `npm prefix` *
package.jsonを含む親ディレクトリで一番近いものを探索し、そのパスを表示する。
```sh
npm prefix
```
- `--global, -g`

### `npm profile` *
### `npm prune`
### `npm publish`
  - `npm unpublish`
### `npm query`
### `npm rebuild`
### `npm repo`
### `npm restart`
### `npm root` *
display npm root
```sh
npm root
```

### `npm run`
package.jsonの `"scripts"` プロパティのコマンドを実行する。
```sh
npm run <command> [-- <args>]
```
- aliases: run-script, rum, urn


### `npm sbom`
### `npm search` *
### `npm shrinkwrap` *
### `npm star` *
  - `npm unstar`
### `npm stars` *
### `npm start`
runs a predefined command specified in the "start" property of a package's "scripts" object
```sh
npm start [-- <args>]
```

### `npm stop`
runs a predefined command specified in the "stop" property of a package's "scripts" object
```sh
npm stop [-- <args>]
```

### `npm team` *
### `npm test`
runs a predefined command specified in the "test" property of a package's "scripts" object
```sh
npm test [-- <args>]
```
- aliases: tst, t

### `npm token` *
### `npm update`
update all the packages
```sh
npm update [<pkg>...]
```
- aliases: up, upgrade, udpate

### `npm version`
### `npm view`
view registry info

### `npm whoami` *
Display npm username

### `npx`

# pnpm

# yarn

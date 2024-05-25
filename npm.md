- [全般](#全般)
  - [`npm`](#npm)
  - [`npx`](#npx)
  - [`npm exec` / `npm x` - ローカルまたはリモートのパッケージを実行する](#npm-exec--npm-x---ローカルまたはリモートのパッケージを実行する)
  - [`npm doctor` - npm環境を検証する](#npm-doctor---npm環境を検証する)
- [ローカル](#ローカル)
  - [`npm init`](#npm-init)
  - [`npm pkg` - package.jsonのマネージ](#npm-pkg---packagejsonのマネージ)
  - [`npm start` - startスクリプトを実行する](#npm-start---startスクリプトを実行する)
  - [`npm stop` - stopスクリプトを実行する](#npm-stop---stopスクリプトを実行する)
  - [`npm test` - testスクリプトを実行する](#npm-test---testスクリプトを実行する)
  - [`npm restart` - restartスクリプトを実行する](#npm-restart---restartスクリプトを実行する)
  - [`npm run-script` / `npm run` - 任意のスクリプトを実行する](#npm-run-script--npm-run---任意のスクリプトを実行する)
  - [`npm version` - バージョンを変更する](#npm-version---バージョンを変更する)
- [レジストリ](#レジストリ)
  - [`npm adduser`](#npm-adduser)
  - [`npm login`](#npm-login)
  - [`npm logout`](#npm-logout)
  - [`npm diff` - レジストリにあるファイルとローカルのdiffを取る](#npm-diff---レジストリにあるファイルとローカルのdiffを取る)
  - [`npm ping`](#npm-ping)
  - [`npm hook`](#npm-hook)
  - [`npm star`](#npm-star)
  - [`npm unstar`](#npm-unstar)
  - [`npm stars`](#npm-stars)
  - [`npm search` - パッケージを探す](#npm-search---パッケージを探す)
  - [`npm view` - レジストリの情報を見る](#npm-view---レジストリの情報を見る)
  - [`npm profile`](#npm-profile)
- [依存パッケージ](#依存パッケージ)
  - [インストール / アンインストール](#インストール--アンインストール)
    - [`npm install` - インストール](#npm-install---インストール)
    - [`npm ci` / `npm clean-install` - クリーンインストール](#npm-ci--npm-clean-install---クリーンインストール)
    - [`npm install-test` - インストールとテスト](#npm-install-test---インストールとテスト)
    - [`npm install-ci-test` - クリーンインストールとテスト](#npm-install-ci-test---クリーンインストールとテスト)
    - [`npm uninstall` - アンインストール](#npm-uninstall---アンインストール)
    - [`npm update` - アップデート](#npm-update---アップデート)
    - [`npm ls` / `npm list` - インストール済みのパッケージを一覧する](#npm-ls--npm-list---インストール済みのパッケージを一覧する)
    - [`npm outdated` - outdatedになっているパッケージを確認する](#npm-outdated---outdatedになっているパッケージを確認する)
    - [`npm prune` - 不要なパッケージを削除する](#npm-prune---不要なパッケージを削除する)
    - [`npm edit` - インストール済みのパッケージのソースを編集する](#npm-edit---インストール済みのパッケージのソースを編集する)
  - [依存関係](#依存関係)
    - [`npm explain` - 依存関係の表示](#npm-explain---依存関係の表示)
    - [`npm dedupe` - パッケージの重複を解消する](#npm-dedupe---パッケージの重複を解消する)
    - [`npm find-dupes` - パッケージの重複を表示する](#npm-find-dupes---パッケージの重複を表示する)
    - [`npm query` - パッケージの依存関係をセレクタで検索する](#npm-query---パッケージの依存関係をセレクタで検索する)
  - [その他](#その他)
    - [`npm docs` - パッケージのドキュメントをブラウザで開く](#npm-docs---パッケージのドキュメントをブラウザで開く)
    - [`npm repo` - パッケージのリポジトリURLをブラウザで開く](#npm-repo---パッケージのリポジトリurlをブラウザで開く)
    - [`npm link` - パッケージへのシンボリックリンクを作る](#npm-link---パッケージへのシンボリックリンクを作る)
    - [`npm pack` - tarballを作成する](#npm-pack---tarballを作成する)
    - [`npm rebuild` - パッケージのリビルド](#npm-rebuild---パッケージのリビルド)
- [パッケージの公開](#パッケージの公開)
  - [`npm publish`](#npm-publish)
  - [`npm unpublish`](#npm-unpublish)
  - [`npm access` - アクセスレベル](#npm-access---アクセスレベル)
  - [`npm deprecate`](#npm-deprecate)
  - [`npm owner`](#npm-owner)
  - [`npm dist-tag`](#npm-dist-tag)
  - [`npm shrinkwrap`](#npm-shrinkwrap)
- [バグ](#バグ)
  - [`npm bugs`](#npm-bugs)
- [セキュリティ](#セキュリティ)
  - [`npm audit`](#npm-audit)
- [キャッシュ](#キャッシュ)
  - [`npm cache`](#npm-cache)
- [その他](#その他-1)
  - [`npm config` -](#npm-config--)
  - [`npm help` -](#npm-help--)
  - [`npm help-search` -](#npm-help-search--)
  - [`npm fund`](#npm-fund)
  - [`npm completion` -](#npm-completion--)
  - [`npm org`](#npm-org)
  - [`npm whoami`](#npm-whoami)
  - [`npm team`](#npm-team)
  - [`npm token`](#npm-token)
  - [`npm explore` -](#npm-explore--)
  - [`npm prefix` -](#npm-prefix--)
  - [`npm root` -](#npm-root--)
  - [`npm sbom`](#npm-sbom)



> [npm CLI | npm Docs](https://docs.npmjs.com/cli/v10/)

v10.8.0

# 全般
## `npm`
## `npx`
**TODO**

## `npm exec` / `npm x` - ローカルまたはリモートのパッケージを実行する
**TODO**

## `npm doctor` - npm環境を検証する
- npmが正常に実行できる環境であることを確認する。


# ローカル
## `npm init`
## `npm pkg` - package.jsonのマネージ
## `npm start` - startスクリプトを実行する
## `npm stop` - stopスクリプトを実行する
## `npm test` - testスクリプトを実行する
## `npm restart` - restartスクリプトを実行する
- `restart`が定義されているなら、 `prerestart` > `restart` > `postrestart` の順で実行する。
- `restart`が定義されていないなら、以下の順で実行する。
  - `prerestart`
  - `prestop` > `stop` > `poststop`
  - `prestart` > `start` > `poststart`
  - `postrestart`
## `npm run-script` / `npm run` - 任意のスクリプトを実行する
## `npm version` - バージョンを変更する


# レジストリ
## `npm adduser`
## `npm login`
## `npm logout`
## `npm diff` - レジストリにあるファイルとローカルのdiffを取る
## `npm ping`
## `npm hook`
## `npm star`
## `npm unstar`
## `npm stars`
## `npm search` - パッケージを探す
## `npm view` - レジストリの情報を見る
## `npm profile`


# 依存パッケージ
## インストール / アンインストール
### `npm install` - インストール
### `npm ci` / `npm clean-install` - クリーンインストール
`./node_modules`を削除してプロジェクト全体を再インストールする

### `npm install-test` - インストールとテスト
- `npm install`して`npm test`する。

### `npm install-ci-test` - クリーンインストールとテスト
- `npm ci`して`npm test`する。

### `npm uninstall` - アンインストール
### `npm update` - アップデート
### `npm ls` / `npm list` - インストール済みのパッケージを一覧する
### `npm outdated` - outdatedになっているパッケージを確認する
### `npm prune` - 不要なパッケージを削除する
### `npm edit` - インストール済みのパッケージのソースを編集する

## 依存関係
### `npm explain` - 依存関係の表示
指定したパッケージを現在のプロジェクトにインストールした依存関係を表示する。
### `npm dedupe` - パッケージの重複を解消する
- 同じパッケージのバージョン違いがインストールされている場合に解消する？

### `npm find-dupes` - パッケージの重複を表示する
- `npm dedupe --dry-run`する

### `npm query` - パッケージの依存関係をセレクタで検索する


## その他
### `npm docs` - パッケージのドキュメントをブラウザで開く
### `npm repo` - パッケージのリポジトリURLをブラウザで開く
### `npm link` - パッケージへのシンボリックリンクを作る
- ローカルにあるパッケージを、ローカルにある他のパッケージから参照できる

### `npm pack` - tarballを作成する
### `npm rebuild` - パッケージのリビルド
- 以下を実行する。
  - preinstall, install, postinstall, prepare
  - バイナリをリンクする


# パッケージの公開
## `npm publish`
## `npm unpublish`
## `npm access` - アクセスレベル
## `npm deprecate`
## `npm owner`
## `npm dist-tag`
## `npm shrinkwrap`


# バグ
## `npm bugs`


# セキュリティ
## `npm audit`


# キャッシュ
## `npm cache`


# その他
## `npm config` - 
## `npm help` - 
## `npm help-search` - 
## `npm fund`
## `npm completion` - 
## `npm org`
## `npm whoami`
## `npm team`
## `npm token`
## `npm explore` - 
## `npm prefix` - 
## `npm root` - 
## `npm sbom`


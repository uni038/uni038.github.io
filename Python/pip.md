# pip
> pip documentation v24.2
> https://pip.pypa.io/en/stable/


## コマンド
### 共通オプション
- `--proxy <proxy>`
- `--trusted-host <hostname>`
- `--cert <path>`
- `--client-cert <path>`


### `pip install`✅️
```sh
pip install [options] <requirement specifier> [package-index-options] …
pip install [options] -r <requirements file> [package-index-options] …
pip install [options] [-e] <vcs project url> …
pip install [options] [-e] <local project path> …
pip install [options] <archive url/path> …
```
次のいずれかからパッケージをインストールする。
- PyPIまたは他のインデックスのURL (requirements specifierを使用)
- VCSのプロジェクトのURL
- ローカルのプロジェクトのディレクトリ (要pyproject.tomlまたはsetup.py)
- ローカルまたはリモートのアーカイブ (sdistまたはwheel形式のアーカイブ)

引数は次の順で照合する。
1. プロジェクトやアーカイブのURL
2. ローカルのディレクトリ（pyproject.tomlまたはsetup.pyを含む必要がある）
3. ローカルファイル（sdistまたはwheel形式のアーカイブ。名前は各形式の命名規則に従う）
4. バージョン指定子

インストールは以下の手順で行われる。
1. requirementsを同定する
2. 依存関係を解決する。何をインストールするかがここで決定される。
3. wheelをビルドする。すべての依存関係がwheelの中にビルドされる。
4. パッケージをインストールする。アップグレードされるものはアンイストールされる。

#### オプション （インストール指示）
- `(-r | --requirement) <file>`
  - requirementsファイルからインストールする
  - requirementsファイルには`pip install`に渡す引数を行ごとに記述する
- `-c <file>`
  - 制約ファイル。
- `(-e | --editable) <path/url>`
  - ローカルのプロジェクトやVCSのURLから、編集可能モードでインストールする。
- `--src <dir>`
  - 編集可能なプロジェクトをチェックアウトするディレクトリ
- `--user`
  - ユーザーディレクトリにインストールする
  - `~/.local/`, または `%APPDATA%Python` (Win)
- `--root <dir>`
  - インストールのルートディレクトリの指定
  - `--prefix` や `-t` とどう違うのか不明
- `--prefix`
- `(-t | --target) <dir>`
  - インストール先のディレクトリの指定。デフォルトではすでに存在するファイルを上書きしない。上書きしたい場合は `--upgrade` を使う
- `--python-version <version>`
- `(-i | --index-url) <url>`
  - Python Package Index (レジストリ)のURL。デフォルトは https://pypi.org/simple.
- `--extra-index-url <url>`

#### オプション（インストール戦略）
- `-U | --upgrade`
  - 利用可能な最新バージョンにアップグレードする。
- `--upgrade-strategy <strategy>`
  - 依存関係をどうアップグレードするか。
  - `eager` : アップグレードするパッケージの依存関係を満たしているかどうかに関係なくアップグレードする。
  - `only-if-needed` : 満たしていない場合のみアップグレードする（デフォルト）。
- `-I | --ignore-installed`
  - インストール済みのパッケージも上書きインストールする。
- `--force-reinstall`
  - up-to-dateなパッケージもすべて再インストールする。

#### オプション（ソースとバイナリ）
- `--no-binary <format_control>`
  - バイナリパッケージを使用しない。
- `--only-binary <format_control>`
  - ソースパッケージを使用しない。
- `--prefer-binary`
  - （ソースパッケージのほうが新しくても）バイナリパッケージを優先する。

#### オプション（その他）
- `--report <file>`
  - インストールの詳細を記述したJSONを出力する
  - `--dry-run`と組み合わせるとよい。
- `(-C | --config-settings) <settings>`
  - ビルドバックエンドに渡すコンフィグ。KEY=VALUEの形式。


### `pip uninstall`

### `pip inspect`
python環境を調べる

### `pip list`
インストールされているパッケージを一覧する

### `pip show`
```sh
pip show [options] <package> ...
```
インストールされているパッケージの情報を表示する

### `pip freeze`✅️
インストールされているパッケージの一覧をrequirementsフォーマットで出力する。
- `(-r | --requirement) <file>`
  - 指定したrequirementsファイルでの並び順を使用する
  - 複数回使用可
- `--exclude <package>`
  - 指定したパッケージを除外する
- `--exclude-editable`
  - 編集可能パッケージを除外する
- `--user`
  - ユーザーにインストールされているパッケージだけ出力する
- `--exclude-editable`
  - 編集可能パッケージを除外する
- `--exclude <package>`
  - 指定したパッケージを除外する

### `pip check`
インストールされているパッケージが依存関係に適合しているかどうか検証する

### `pip download`
パッケージをダウンロードする

### `pip wheel`
requirementsと依存関係からwheelをビルドする
- ビルドシステムインターフェース
  - pyproject.tomlがあればそれを使う
  - ない場合はsetup.py

### `pip hash`

### `pip search`

### `pip cache`

### `pip config`
グローバルまたはローカルのコンフィグ
> https://pip.pypa.io/en/stable/topics/configuration/
```sh
pip config [<file-option>] list
pip config [<file-option>] [--editor <editor-path>] edit

pip config [<file-option>] get command.option
pip config [<file-option>] set command.option value
pip config [<file-option>] unset command.option
pip config [<file-option>] debug
```
- `--edtitor <editor>`
- `--global`
- `--user`
- `--site`


### `pip debug`

## requirements specifier (PEP 508)
> https://pip.pypa.io/en/stable/reference/requirement-specifiers/

- 名前形式
  ```sh
  SomeProject
  SomeProject == 1.3
  SomeProject >= 1.2, < 2.0
  SomeProject[foo, bar]
  SomeProject ~= 1.4.2
  SomeProject == 5.4 ; python_version < '3.8'
  SomeProject ; sys_platform == 'win32'
  requests [security] >= 2.8.1, == 2.8.* ; python_version < "2.7"
  ```
- URL形式
  ```sh
  pip @ https://github.com/pypa/pip/archive/22.0.2.zip
  requests [security] @ https://github.com/psf/requests/archive/refs/heads/main.zip ; python_version >= "3.11"
  ```
- バージョン指定子
  - `~=` : 指定バージョンに適合するバージョン
    - A.B.C の場合は A.B.* で A.B.C より後のバージョン
    - A.B の場合は A.* で A.B より後のバージョン
  - `==` : 完全一致
    - ただし A.B の場合 A.B.0 はOK
  - `!=` : 除外
  - `<=`, `>=` :
  - `<`, `>` :
  - `===` : 文字列として完全一致

## ビルドシステムインターフェース
インストール時に使うビルドシステム。
- pyproject.tomlあるならそれを使う。ない場合はsetup.pyを使う


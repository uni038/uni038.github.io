# pip
> pip documentation v24.2
> https://pip.pypa.io/en/stable/


## コマンド
### 共通オプション
- `--proxy <proxy>`
- `--trusted-host <hostname>`
- `--cert <path>`
- `--client-cert <path>`


### `pip install`
```sh
pip install [options] <requirement specifier> [package-index-options] …
pip install [options] -r <requirements file> [package-index-options] …
pip install [options] [-e] <vcs project url> …
pip install [options] [-e] <local project path> …
pip install [options] <archive url/path> …
```
次のいずれかからパッケージをインストールする。
- URL
  - PyPI (requirements specを使用)
  - VCSのURL
- ローカルのプロジェクトのディレクトリ (要pyproject.tomlまたはsetup.py)
- ローカルのアーカイブ (sdistまたはwheel形式のアーカイブ)

オプション
- `(-r | --requirement) <file>`
  - requirementsファイルからインストールする
- `(-e | --editable) <path/url>`
  - ローカルのプロジェクトやVCSのURLから、編集可能モードでインストールする。
- `-U | --upgrade`
  - 利用可能な最新バージョンにアップグレードする
- `-I | --ignore-installed`
  - インストール済みのパッケージも上書きインストールする。
- `--force-reinstall`
  - up-to-dateなパッケージもすべて再インストールする。
- `--report <file>`
  - インストールの詳細を記述したJSONを出力する
  - `--dry-run`と組み合わせるとよい。
- `--user`
- `(-C | --config-settings) <settings>`
  - ビルドバックエンドに渡すコンフィグ

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

### `pip freeze`
インストールされているパッケージをrequirementsフォーマットで出力する。
- `(-r | --requirement) <file>`
  - 指定したrequirementsファイルでの並び順を使用する
  - 複数回使用可
- `--exclude <package>`
  - 指定したパッケージを除外する
- `--exclude-editable`
  - 編集可能パッケージを除外する


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


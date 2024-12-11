# uv

## command
> CLI Reference\
> https://docs.astral.sh/uv/reference/cli/

### `uv run` コマンドやスクリプトを実行
指定したpython環境でコマンドやスクリプトを実行する。
```sh
uv run [OPTIONS] [--] [COMMAND]
```

```sh
uv run python file.py
# *.pyは直接実行できる
uv run file.py
# URLはダウンロードして実行する
uv run <URL>
# 標準入力をpythonスクリプトとして読む
uv run -
```
- プロジェクト内で実行すると、プロジェクトの環境が作成・更新されて実行される
- プロジェクト外で実行すると、カレントまたは親ディレクトリに仮想環境があればその環境で実行する。そうでないなら、発見したインタプリタの環境で実行する
- `--python | -p` : 実行環境に使用するインタプリタ。発見された環境が要求されたインタプリタを満足するならその環境を使う。
- `--python-preference` : インタプリタの探索戦略。  
  - `only-managed`
  - `managed` (default)
  - `system`
  - `only-system`

### `uv init` プロジェクトの初期化
```sh
uv init [OPTIONS] [PATH]
```
- pyproject.toml がすでに存在するならエラー。

### `uv add` プロジェクトに依存関係を追加
```sh
uv add [OPTIONS] <PACKAGES|--requirements <REQUIREMENTS>>
```
- pyproject.toml に追加する。
- PACKAGES はPEP508形式。 (`ruff==0.5.0`など)

### `uv remove` プロジェクトから依存関係を削除
- pyproject.toml から依存関係を削除する
- `uv pip install`などで手動インストールしたものは削除されない

### `uv sync` プロジェクトの環境を更新？
### `uv lock` プロジェクトのロックファイルを更新
```sh
uv lock [OPTIONS]
```
- `uv.lock`ファイルが存在しないなら作成する。

### `uv export` プロジェクトのロックファイルをエクスポート
- 現在は requirements-txt 形式のみサポート。

### `uv tree` プロジェクトの依存関係ツリーを表示
### `uv tool` pythonパッケージの提供するコマンドを実行
- `uv tool run`
- `uv tool install`
- `uv tool upgrade`
- `uv tool list`
- `uv tool uninstall`
- `uv tool update-shell`
- `uv tool dir`

### `uv python` pythonバージョンを管理
- `uv python list` : 利用できるバージョンの一覧
- `uv python install` : ダウンロード、インストール
    ```sh
    uv python install [OPTIONS] [TARGETS]…
    ```
    - TARGETS: インストールするpythonバージョン。指定しない場合は`.python-versions` (`.python-version`)ファイルを探す。ファイルがない場合はuvでインストール済みのバージョンがあるか確認し、なにもインストールされていなければlatest stableバージョンをインストールする
- `uv python find` : 指定した条件のpythonをローカルから探す
    ```sh
    uv python find [OPTIONS] [REQUEST]
    ```
    - インストールされたpythonを探す。
- `uv python pin` : pythonバージョンを固定する
    ```sh
    uv python pin [OPTIONS] [REQUEST]
    ```
    - `.python-version`ファイルにバージョンを書き込む。他のコマンドがバージョンを決定するのに使用される。
    - バージョンを指定されていないなら、`.python-version`を探してそのバージョンを表示する。ファイルがない場合はエラー。
    - `.python-version`ファイルはuv以外にもpyenvなどのツールが使用するファイル。uvは他のツールよりもバージョンの指定形式が広く、互換性を保ちたい場合はバージョン番号より複雑な指定はしないこと
- `uv python dir` : uvがpythonインストールに使うディレクトリを表示
  - `$HOME/.local/share/uv/python` (Unix)
  - `%APPDATA%\uv\data\python` (Win)
- `uv python uninstall`

pythonバージョンの指定形式
- `<version>` : `3`, `3.12.3`
- `<version-specifier>` : `>=3.12, <3.13`
- `<implementation>` : `cpython`, `cp`
- `<implementation>@<version>` : `cpython@3.12`
- `<implementation><version>` : `cpython3.12`, `cp312`
- `<implementation><version-specifier>` : `cpython>=3.12, <3.13`
- `<implementation>-<version>-<os>-<arch>-<libc>` : `cpython-3.12.3-macos-aarch64-none`
- `<executable-path>` : `/opt/homebrew/bin/python3`
- `<executable-name>` : `mypython3` ？
- `<install-dir>` : `/some/environment/`
- CPython, PyPy, GraalPyをサポート

### `uv pip` pythonパッケージをpipのインターフェースで管理
- `uv pip compile` : requirements.in を requirements.txt にコンパイル
    ```sh
    uv pip compile [OPTIONS] <SRC_FILE>…
    ```
    - requirements.in, pyproject.toml, setup.py, setup.cfg
    - `-` (標準入力)
- `uv pip sync` : 環境をrequirements.txtと同期する
    ```sh
    uv pip sync [OPTIONS] <SRC_FILE>…
    ```
    - requirements.txt, pyproject.toml, setup.py, setup.cfg
    - `-` (標準入力)
- `uv pip install` : 環境にパッケージをインストール
- `uv pip uninstall` : 環境からパッケージをアンインストール
- `uv pip freeze`
- `uv pip list`
- `uv pip show`
- `uv pip tree` 
- `uv pip check`

### `uv venv` 仮想環境を作成
  ```sh
  uv venv [OPTIONS] [PATH]
  ```
  - PATH: 作成先パス。デフォルトでは `./.venv`
  - すでに存在する場合は削除して新しく作成する
  - `--prompt` : その環境のプロンプトのプレフィックス。

### `uv build` pythonパッケージをsdist,bdistにビルド

### `uv publish` 公開

### `uv cache` uvのキャッシュを管理

### `uv self` uv実行ファイルを管理
- `uv self update` : uvをアップデートする
    ```sh
    uv self update [OPTIONS] [TARGET_VERSION]
    ```

### `uv version` uvのバージョンを表示

### `uv generate-shell-completion`

### `uv help`

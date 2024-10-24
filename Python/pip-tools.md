# pip-tools
> github
> https://github.com/jazzband/pip-tools

> documentation
> https://pip-tools.readthedocs.io/en/latest/

```sh
pip install pip-tools
```

# pip-compile
```sh
pip-compile
python -m piptools compile
pipx run --spec pip-tools pip-compile
```
以下のいずれかをコンパイルして`requirements.txt`を出力する。依存関係を満たすrequirements.txtがすでにある場合は（アップデート可能なものがあっても）何もしない。
- `pyproject.toml`
- `setup.cfg`
- `setup.py`
- `requirements.in`

## コマンドライン
```sh
pip-compile [OPTIONS] [SRC_FILES]…
```
- `-v | --verbose`
- `-q | --quiet`
- `-n | --dry-run`
- `-p | --pre`
- `-r | --rebuild`
- `(-f | --find-links) <text>`
- `(-i | --index-url) <text>`
- `-U | --upgrade` すべての依存を最新バージョンにアップグレードする
- `(-P | --upgrade-package) <text>` 指定したパッケージをアップグレードする
- `(-o | --output-file) <filename>` 出力先ファイル
  - `--output-file=-` 標準出力
- `(-c | --constraint) <text>` 制約ファイル
- `--header` / `--no-header` 出力のヘッダーコメント
- `--annotate` / `--no-annotate` コメント行
- `--allow-unsafe` / `--no-allow-unsafe`
- `--build-isolation` / `--no-build-isolation`
- `--pip-args <text>` pipに渡す引数
- `--config <file>` 設定ファイル(TOML)
  - .pip-tools.toml
  - pyproject.toml


# pip-sync
```sh
pip-sync
python -m piptools sync
```
環境をrequirements.txtの内容と一致させる。
- requirements.txtはpip-compileで生成したものにか対応していない
- パッケージングツール(setuptools, pip, pip-tools)は対象外

# コンフィグ
pyproject.tomlの`tool.pip-tools`に設定を記載できる
- pip-compile用の設定は `tool.pip-tools.compile`, syncは `tool.pip-tools.sync` にも書ける
- requirements.txtの最初にコメントで書かれる実行したコマンドは`CUSTOM_COMPILE_COMMAND`環境変数で変更できる


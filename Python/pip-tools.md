# pip-tools
> https://github.com/jazzband/pip-tools

```sh
pip install pip-tools
```

# pip-compile
```sh
pip-compile
python -m piptools compile
pipx run --spec pip-tools pip-compile
```
以下のいずれかをコンパイルして`requirements.txt`を出力する。依存関係を満たすrequirements.txtがすでにある場合、pip-compileは何もしない。アップデート可能なものが含まれているとしても何もしない
- `pyproject.toml`
- `setup.cfg`
- `setup.py`
- `requirements.in`

## コマンドライン
- `-o <FILE>`, `--output-file=<FILE>`
- `--extra`
- `--upgrade`
- `--upgrade-package`, `-P`
- `--pip-args`


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


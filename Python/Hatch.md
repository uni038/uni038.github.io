# Hatch
> GitHub - pypa/hatch: Modern, extensible Python project management
> https://github.com/pypa/hatch

> Hatch - Hatch (pypa.io)
> https://hatch.pypa.io/latest/

## インストール
- Linux/Win/Mac
- CLI/GUI/BIN
- pip
  ```sh
  pip install hatch
  ```
- pipx
  ```sh
  pipx install hatch
  ```
- homebrew, conda


## Introduction
Setup
```sh
hatch new "Hatch Demo"
```

```txt
hatch-demo
├── src
│   └── hatch_demo
│       ├── __about__.py
│       └── __init__.py
├── tests
│   └── __init__.py
├── LICENSE.txt
├── README.md
└── pyproject.toml
```

```sh
hatch new --init
```
- setup.py


## Environments (仮想環境)
### commands
```sh
# create
hatch env create

# enter
hatch shell
```

直接実行
```sh
hatch run python -c "import sys; print(sys.executable)"
```

- `-e | --env`, `$HATCH_ENV` : 環境の選択
- runはコマンドの頭に `<ENVNAME>:` を付加して指定できる

### dependency
project.dependencies (pyproject.toml)
- ビルド用のツールはしばしばそれ自体がpythonパッケージだったりするので、ビルドにはビルド用の環境を作成するのが通例。

### matrix

### configuration
pyproject.toml
```toml
[tool.hatch.envs.<ENV_NAME>]
```
- 名前が `hatch-` で始まる環境は特別な用途を持つ
- `template` で継承元を指定できる。デフォルトで`default`環境を継承する。自身を継承することで継承を無効化できる
- `dependencies`, `extra-dependencies` で依存関係を追加できる
- 依存関係のインストールにはpipを使用している
- `feature` ( → optional-dependencies)
- `dev-mode`
- `skip-install` 環境生成時にプロジェクトをインストールしない
- `env-vars` 環境固有の環境変数
  - `env-include`, `env-exclude`
- `scripts`
- `pre-install-commands`, `post-install-commands`
- `python` pythonバージョン
- `platform`
- `description`
- `type` 環境のタイプ。対応する環境プラグイン。ビルトインは`virtual` (=venv) のみ。

### advanced
- context formatting
- `matrix`

## Versioning
tool.hatch.version (pyproject.toml)

## Builds
tool.hatch.build (pyproject.toml)
```toml
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[tool.hatch.build.targets.sdist]
exclude = [
  "/.github",
  "/docs",
]

[tool.hatch.build.targets.wheel]
packages = ["src/foo"]
```

build command
```sh
hatch build
```
- `-t` でターゲット指定
  - sdist, wheel


## Publishing



## コマンドリスト


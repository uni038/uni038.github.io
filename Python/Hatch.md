# Hatch
> GitHub - pypa/hatch: Modern, extensible Python project management
> https://github.com/pypa/hatch

> Hatch - Hatch (pypa.io)
> https://hatch.pypa.io/latest/

## インストール
- GUIインストーラー (Win/Mac)
- CLIインストール (Win/Mac)
- スタンドアロンバイナリ (Linux/Win/Mac)
- pip install
  ```sh
  pip install hatch
  ```
- pipx
  ```sh
  pipx install hatch
  ```
- homebrew
- conda


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

- pyproject.tomlを使う
- `tool.*` に関しては hatch.toml に記述することもできる

.
- setup.py

## 依存関係
- pyproject.tomlの `project.dependencies` に記述する。
  ```toml
  [project]
  dependencies = [
    "cowsay"
  ]
  ```

## Environments (仮想環境)
- `hatch env create`で作成できる。
  - `hatch shell`や`hatch run`を実行したときに自動的に環境が作成されるので、通常は手動で作成する必要はない。
- `hatch shell`で環境内でシェルを起動できる。`hatch run`で環境内でコマンドを実行できる
  - `-e | --env`, `$HATCH_ENV` : 環境の選択
  - runはコマンドの頭に `<ENVNAME>:` を付加して指定できる
- 名前が `hatch-` で始まる環境は特別な用途を持つ
- 各環境に固有の設定を追加できる。
  ```toml
  [tool.hatch.envs.<ENV_NAME>]
  ```
  - `template` : 指定した環境から設定を継承する
  - `detached`
  - `extra-dependencies`
  - `features` : プロジェクトからインストールする`optional-dependencies`の指定
  - `dev-mode`
  - `skip-install` : プロジェクト作成時にインストールしない
  - `env-vars` : 環境変数の定義
  - `env-include` : 環境が参照できる環境変数
  - `env-exclude` :
  - `pre-install-commands` :
  - `post-install-commands` :
  - `python` : pythonバージョン
  - `platforms` :
  - `type` : 環境のタイプ。対応する環境プラグイン。ビルトインは`virtual` (=venv) のみ。
  - ビルド用のツールはしばしばそれ自体がpythonパッケージだったりするので、ビルドにはビルド用の環境を作成するのが通例。
  - 依存関係のインストールにはpipを使用している

### matrix
環境は固有のマトリックス(matrix)を設定できる。


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
> https://hatch.pypa.io/latest/cli/reference/

### プロジェクト
- `hatch new`
  - プロジェクトを作成または初期化する
- `hatch project`
  - プロジェクトの情報を見る
  - `hatch project metadata`
- `hatch version`
  - プロジェクトのバージョンを表示または設定する

### 環境
- `hatch dep`
  - 環境の依存関係を管理する
  - `hatch dep hash`
  - `hatch dep show`
  - `hatch dep show requirements`
  - `hatch dep table`
- `hatch env`
  - 環境管理
  - `hatch env create`
  - `hatch env find`
  - `hatch env prune`
  - `hatch env remove`
  - `hatch env run`
  - `hatch env show`
- `hatch run`
  - プロジェクトの環境でコマンドを実行する。`hatch env run` のショートカットコマンド。
- `hatch shell`
  - プロジェクトの環境でシェルを起動する
- `hatch status`
  - 現在の環境の情報を表示する
- `hatch test`
  - `hatch-test`環境を使ってテストを実行する

### ビルド
- `hatch build`
  - プロジェクトをビルドする
- `hatch clean`
  - ビルドのアーティファクトを削除する
- `hatch publish`
  - ビルドアーティファクトをpublishする(?)

### その他
- `hatch config`
  - `hatch config explore`
  - `hatch config find`
  - `hatch config restore`
  - `hatch config set`
  - `hatch config show`
  - `hatch config update`
- `hatch fmt`
  - フォーマッターとリンターを実行する
- `hatch python`
  - pythonインストールの管理
  - `hatch python find`
  - `hatch python install`
    - `--private`
  - `hatch python remove`
  - `hatch python show` : 利用可能なpythonディストリビューションを表示する
  - `hatch python update`
- `hatch self`
  - Hatch自体の管理
  - `hatch self report` Github issureの生成
  - `hatch self restore` インストールの修復
  - `hatch self update` アップデート


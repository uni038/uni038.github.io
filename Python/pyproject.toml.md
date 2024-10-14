# pyproject.toml

## `[build-system]`
- requires
  - ビルドに必要な依存関係。
- build-backend
  - 使用されるべきビルドバックエンド

## `[project]`
### 必須かつ静的
- name
  - このプロジェクトの名前

### 必須かつ静的/動的
- version
  - このプロジェクトのバージョン

### 任意、静的/動的
- 情報系
  - authors
  - classifiers
    - PyPI分類詞
  - description
    - このプロジェクトの1行説明。
  - keywords
  - license
  - maintainers
  - readme
    - このプロジェクトの完全な説明。ファイルパスまたはテーブル。
    - file
    - text
    - content-type
  - urls
    - プロジェクトに関連するURLのテーブル。
- 依存関係
  - dependencies
    - プロジェクトの依存関係である、文字列の配列。
  - optional-dependencies
  - requires-python
    - このプロジェクトの要求するPythonバージョン
- スクリプト系
  - scripts
    - プロジェクトにスクリプトを作成する。
      ```
      [project.scripts]
      spam-cli = "spam:main_cli"
      ```
      - `spam-cli`コマンドを実行することで、`from spam import main_cli; main_cli()`が走るようになる
  - gui-scripts
    - GUIから起動したときにターミナルを表示したくないコマンド
  - entry-points
- その他
  - dynamic
    - 動的なキーとして指定するキー。つまり、目的を持って未指定にしておき、ツールによって設定するキー。

## `[tool]`



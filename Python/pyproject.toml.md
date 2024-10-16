# pyproject.toml
> pyproject.toml を書く - Python Packaging User Guide
> https://packaging.python.org/ja/latest/guides/writing-pyproject-toml/

> pyproject.toml の仕様 - Python Packaging User Guide
> https://packaging.python.org/ja/latest/specifications/pyproject-toml/

## `[build-system]`
- `requires`
  - ビルドに必要な依存関係。
- `build-backend`
  - 使用されるべきビルドバックエンド

## `[project]`
### 必須かつ静的
- `name`
  - このプロジェクトの名前

### 必須かつ静的/動的
- `version`
  - このプロジェクトのバージョン

### 任意、静的/動的
- 情報系
  - `authors`
  - `classifiers`
    - PyPI分類詞
  - `description`
    - このプロジェクトの1行説明。
  - `keywords`
  - `license`
  - `maintainers`
  - `readme`
    - このプロジェクトの完全な説明。ファイルパスまたはテーブル。
    - `file`
    - `text`
    - `content-type`
  - `urls`
    - プロジェクトに関連するURLのテーブル。
- 依存関係
  - `dependencies`
    - プロジェクトの依存関係。文字列の配列。
  - `optional-dependencies.<key>`
    - オプショナルな依存関係。テーブルで、値は文字列の配列。
    - `プロジェクト名[名前]`の形式で参照する。（ツール依存？）
  - `requires-python`
    - このプロジェクトの要求するPythonバージョン
- スクリプト系
  - `scripts`
    - プロジェクトにスクリプトを作成する。
      ```toml
      [project.scripts]
      spam-cli = "spam:main_cli"
      ```
      - `spam-cli`コマンドを実行することで、`from spam import main_cli; main_cli()`が走るようになる
  - `gui-scripts`
    - WindowsでGUIから起動したときにターミナルを表示したくないコマンド
    - コマンドラインから実行すると非同期実行する
    - Windows以外では不要
  - `entry-points`
- その他
  - `dynamic`
    - 動的なキーとして指定するキー。つまり、目的を持って未指定にしておき、ツールによって設定するキー。

## `[tool]`
各ツール固有の設定


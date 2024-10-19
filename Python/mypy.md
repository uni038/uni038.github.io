# mypy

> mypy - Optional Static Typing for Python \
> https://www.mypy-lang.org/ \
> mypy 1.12.0 documentation \
> https://mypy.readthedocs.io/en/stable/ \
> GitHub - python/mypy: Optional static typing for Python \
> https://github.com/python/mypy \
> Mypy Type Checker - Visual Studio Marketplace \
> https://marketplace.visualstudio.com/items?itemName=ms-python.mypy-type-checker

## コマンドライン
> The mypy command line - mypy 1.12.0 documentation
> https://mypy.readthedocs.io/en/stable/command_line.html

```sh
mypy program.py
```

- `-m MODULE`, `--module MODULE`
  - チェックするモジュール
- `-p PACKAGE`, `--package PACKAGE`
  - チェックするパッケージ
- `--exclude`
  -  .
- `--config-file CONFIG_FILE`
  -  .

## mypy.ini
> https://mypy.readthedocs.io/en/stable/config_file.html

コマンドラインで `--config-file` を指定しなかった場合は以下の順で探索する
1. `./mypy.ini`
2. `./.mypy.ini`
3. `./pyproject.toml`
4. `./setup.cfg`
5. `$XDG_CONFIG_HOME/mypy/config`
6. `~/.config/mypy/config`
7. `~/.mypy.ini`

- `[mypy]` セクションが必須。
- `[mypy-PATTERN1,PATTERN2,…]`
  - PATTERN はモジュール名。 (`foo.bar`, `foo.bar.*` など)
  - その名前のモジュールに適用される。
  - `foo.*` は `foo` とそのサブモジュールに適用。
  - `foo.*.bar` のように途中に使用可能。このとき `foo.bar` にもマッチする。

## type hints
- 型推論があるため、単純な型であればいちいち型ヒントをつける必要はない
- python 3.9 以降はジェネリクスが使える。3.8以前は `typing` からインポートする
- 可変サイズのタプルの型ヒントは `...` (ellipsis) を使う
    ```py
    x: tuple[int, ...]
    ```
- python 3.10 以降は `|` が使える。3.9以前は Union を使う
- `assert` ?
- Callable (コールバックなど)
    ```py
    x: Callable[[int, float], float]
    ```
- 可変長引数は値の型を書く
    ```py
    def call(*args: str, **kwargs: str):
    ```

### クラス
- インスタンス変数の型ヒントはクラス定義に書いてもよい
    ```py
    class MyClass:
        audit_log: list[str]

        def __init__(self) -> None:
            self.audit_log: list[str] = []
    ```
- クラス変数の型ヒントは `ClassVar` を使う
    ```py
    class Car:
        seats: ClassVar[int] = 4
    ```
- `__setattr__`, `__getattr__` で定義した動的属性もチェックされる

### その他
- 型推論の結果が知りたいときは `typing.reveal_type()` を使う
- `# type: ignore` プラグマでエラーを無視する
- `typing.cast()` で型推論による型を変更できる。実行時には影響しない
- `typing.TYPE_CHECKING` は型検査中のみ True になる。これを使えば型検査時と実行時で違うパスを通るようにできる
- ストリームオブジェクトは `typing.IO` を使う
- 前方参照は通常できないが `__future__.annotations` をインポートするとできるようになる



## mypy type checker (VSCode)


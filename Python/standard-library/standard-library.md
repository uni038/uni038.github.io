v3.12.4

> Python 標準ライブラリ — Python 3.12.4 ドキュメント \
> https://docs.python.org/ja/3/library/

- memo
  - tomllib

# 一覧
- [組み込み関数](#組み込み関数)
- テキスト
  - [`string`](#string)
  - `re` 正規表現 → [re.md](re.md)
  - `difflib`
  - [`textwrap`](#textwrap)
  - `unicodedata`
  - `stringprep`
  - `readline`
  - `rlcompleter`
- バイナリ
  - `struct`
  - `codecs`
- データ型
  - `datetime`
  - `zoneinfo`
  - `calendar`
  - [`collections`](#collections)
  - [`collections.abc`](#collectionsabc)
  - `heapq`
  - `bisect`
  - `array`
  - `weakref` 弱参照
  - `types`
  - [`copy`](#copy)
  - [`pprint`](#pprint)
  - `reprlib`
  - [`enum`](#enum)
  - `graphlib` グラフ構造
- 数学
  - `numbers`
  - `math` 数学関数
  - `cmath` 複素数用の数学関数
  - `decimal` 固定十進数
  - `fractions` 有理数
  - `random` 乱数
  - `statistics` 数学的統計関数
- 関数型プログラミング
  - [`itertools`](#itertools)
  - [`functools`](#functools)
  - `operator`
- ファイルとディレクトリ
  - `pathlib` → [pathlib.md](pathlib.md)
  - `os.path` → [os.path.md](os.path.md)
  - [`fileinput` - 複数の入力ストリームをまたいで行を反復する](#fileinput---複数の入力ストリームをまたいで行を反復する)
  - `stat`
  - `filecmp` ファイルとディレクトリの比較
  - `tempfile` 一時ファイルや一時ディレクトリの作成
  - [`glob` - UNIX形式のパス名パターン展開](#glob---unix形式のパス名パターン展開)
  - [`fnmatch` - UNIXファイル名パターンマッチ](#fnmatch---unixファイル名パターンマッチ)
  - `linecache`
  - [`shutil`](#shutil) 高水準ファイル操作
- 永続化
  - `pickle`
  - `copyreg`
  - `shelve`
  - `marshal`
  - `dbm`
  - [`sqlite3`](#sqlite3) SQLite インターフェース
- 圧縮、アーカイブ
  - `zlib`
  - `gzip`
  - `bz2`
  - `lzma`
  - `zipfile` zip
  - `tarfile` tar ファイルの読み書き
- ファイルフォーマット
  - [`csv`](#csv) CSV ファイル
  - [`configparser`](#configparser)
  - [`tomllib`](#tomllib) TOML ファイル
  - `netrc` netrc ファイル
  - `plistlib`
- 暗号
  - `hashlib`
  - `hmac`
  - `secrets`
- 汎用 OS サービス
  - `os` OS インターフェース全般 → [os.md](os.md)
  - [`io`](#io) ストリーム
  - `time`
  - [`argparse`](#argparse)
  - `getopt`
  - `logging` ロギング → [loggigng.md](logging.md)
    - `logging.config`
    - `logging.handler`
  - `getpass`
  - `curses`
  - `curses.textpad`
  - `curses.ascii`
  - `curses.panel`
  - `platform` プラットフォーム固有の情報
  - `errno`
  - `ctypes`
- 並列処理
  - [`threading`](#threading) スレッドベースの並列処理
  - [`multiprocessing`](#multiprocessing) プロセスベースの並列処理
  - `multiprocessing.shared_memory`
  - `concurrent`
  - `concurrent.futures`
  - `subprocess` → [subprocess.md](subprocess.md)
  - `sched`
  - `queue`
  - `contextvars`
  - `_thread`
- ネットワーク、プロセス間通信
  - [`asyncio`](#asyncio)
  - `socket`
  - `ssl`
  - `select`
  - `selectors`
  - `signal`
  - `mmap`
- インターネット上のデータ
  - `email`
  - [`json`](#json)
  - `mailbox`
  - `mimetypes`
  - `base64`
  - `binascii`
  - `quopri`
- マークアップ
  - `html`
  - `html.parser`
  - `html.entities`
  - `xml.etree.ElementTree`
  - `xml.dom`
  - `xml.dom.minidom`
  - `xml.dom.pulldom`
  - `xml.sax`
  - `xml.sax.handler`
  - `xml.sax.saxutils`
  - `xml.sax.xmlreader`
  - `xml.parsers.expat`
- インターネットプロトコル
  - `webbrowser`
  - `wsgiref` WSGI
  - [`urllib`](#urllib) URL を扱うモジュール
  - `urllib.request`
  - `urllib.response`
  - `urllib.parse`
  - `urllib.error`
  - `urllib.robotparser`
  - `http`
  - [`http.client`](#httpclient)
  - `ftplib`
  - `poplib`
  - `imaplib`
  - `smtplib`
  - `uuid`
  - `sockerserver`
  - [`http.server`](#httpserver)
  - `http.cookies`
  - `http.cookiejar`
  - `xmlrpc`
  - `xmlrpc.client`
  - `smlrpc.server`
  - `ipaddress`
- マルチメディア
  - `wave`
  - `colorsys`
- 国際化
  - `gettext`
  - `locale`
- プログラムフレームワーク
  - `turtle`
  - [`cmd`](#cmd)
  - `shlex`
- Tk
  - `tkinter`
  - `tkinter.colorchooser`
  - `tkinter.font`
  - `tkinter.simpledialog`
  - `tkinter.filedialog`
  - `tkinter.commondialog`
  - `tkinter.messagebox`
  - `tkinter.scrolledtext`
  - `tkinter.dnd`
  - `tkinter.ttk`
  - `tkinter.tix`
  - `IDOL`
- 開発ツール
  - `typing` 型ヒント → [typing.md](typing.md)
  - `pydoc`
  - Python 開発モード
  - `doctest`
  - [`unittest`](#unittest)
  - `unittest.mock`
  - `2to3`
  - `test`
  - `test.support`
  - `test.support.socket_helper`
  - `test.support.script_helper`
  - `test.support.bytecode_helper`
  - `test.support.threading_helper`
  - `test.support.os_helper`
  - `test.support.import_helper`
  - `test.support.warnings_helper`
- デバッグ
  - 監査イベント表
  - `bdb`
  - `faulthandler`
  - `pdb` Python デバッガ
  - Python プロファイラ
  - [`cProfile`, `profile`](#cprofile-profile)
  - [`timeit`](#timeit)
  - `trace`
  - [`tracemalloc`](#tracemalloc)
- ソフトウェアパッケージと配布
  - `ensurepip`
  - [`venv`](#venv) 仮想環境
  - [`zipapp`](#zipapp)
- ランタイムサービス
  - `sys` → [sys.md](sys.md)
  - `sys.monitoring`
  - [`sysconfig`](#sysconfig) Python の構成情報
  - `builtins`
  - `__main__`
  - `warnings`
  - [`dataclasses`](#dataclasses) データクラス
    - `@dataclass`
    - `field`
  - [`contextlib`](#contextlib) with 文コンテキスト用ユーティリティ
  - [`abc`](#abc)
  - `atexit`
  - `traceback`
  - `__future__`
  - `gc`
  - `inspect`
  - `site`
- カスタムのインタプリタ
  - `code`
  - `codeop`
- モジュールのインポート
  - `zipimport`
  - `pkgutil`
  - `modulefinder`
  - `runpy`
  - [`importlib`](#importlib)
  - `importlib.resources`
  - `importlib.resources.abc`
  - `importlib.metadata`
  - `sys.path`
- Python 言語関連
  - `ast`
  - `symtable`
  - `token`
  - `keyword`
  - `tokenize`
  - `tabnanny`
  - `pyclbr`
  - `py_compile`
  - `compileall`
  - `dis`
  - `pickletools`
- Windows 固有
  - `msvcrt`
  - [`winreg`](#winreg)
  - `winsound`
- Unix 固有
  - `posix`
  - `pwd`
  - `grp`
  - `termios`
  - `tty`
  - `pty`
  - `fcntl`
  - `resource`
  - `syslog`

# 組み込み関数

- 組み込み型
  - `bool`
  - `bytearray`
  - `bytes`
  - `complex`
  - `dict`
  - `float`
  - `frozenset`
  - `int`
  - `list`
  - `memoryview`
  - `object`
  - `property`
  - `range`
  - `set`
  - `slice`
  - `str`
  - `super`
  - `tuple`
  - `type`
- 文字列
  - `ascii()`
  - `bin()`
  - `chr()`
  - `format()`
  - `hex()`
  - `oct()`
  - `ord()`
- 数学
  - `abs()`
  - `divmod()`
  - `max()`
  - `min()`
  - `pow()`
  - `round()`
  - `sum()`
- データ構造
  - `aiter()`
  - `all()`
  - `anext()`
  - `any()`
  - `enumerate()`
  - `filter()`
  - `iter()`
  - `len()`
  - `map()`
  - `next()`
  - `reversed()`
  - `sorted()`
  - `zip()`
- クラスやオブジェクト
  - `@classmethod`
  - `delattr()`
  - `getattr()`
  - `hasattr()`
  - `id()`
  - `isinstance()`
  - `issubclass()`
  - `repr()`
  - `setattr()`
  - `@staticmethod`
  - `vars()`
  - `hash()`
- python の実行
  - `breakpoint()`
  - `callable()`
  - `compile()`
  - `dir()`
  - `eval()`
  - `exec()`
  - `globals()`
  - `help()`
  - `input()`
  - `locals()`
- IO
  - `open()`
  - `print()`
- その他
  - `__import__()`

# テキスト

## `string`

- 文字クラス
  - `string.ascii_letters`, `string.whitespace`など
- `Formatter`クラス
  - `str.format()`と同様の文字列フォーマットを行うクラス。
- `Template`クラス
  - javascript のようなテンプレート文字列を実現するクラス。文字列中の`$value`を`value`の値に置き換える。

## `textwrap`
- `wrap()`
  - 文字列をwidthごとに区切り、list[str]で返す
- `fill()`
  - 文字列をwidthごとに区切り、改行で結合した単一のstrで返す
- `shorten()`
  - 指定幅に収まるように切り詰める。単語単位？
- `dedent()`
  - インデントを可能な限り削除する
- `indent()`

# データ型

## `collections`

使えそうな順。

- `defaultdict`オブジェクト
  - 存在しないキーが`[]`（`__getitem__()`）で呼び出された場合にデフォルト値を返す辞書。
  - デフォルト値を返す関数をコンストラクタに渡して生成する。
- `ChainMap`オブジェクト
  - 複数の辞書を結合した辞書
  - もとの辞書の要素をコピーするのではなく、参照として保持する
  - 辞書以外にも Mapping オブジェクト全般を結合できる
- `Counter`オブジェクト
  - 数を数える。
  - キーに数える対象、値に数を持つ辞書
- `deque`オブジェクト
  - 両端キュー。先頭と終端両方から要素を追加・削除できる。
  - `list`は計算量以外の違いはない。
- `OrderedDict`オブジェクト
  - 順序付き辞書。3.7 で通常の`dict`が順序を保証する様になったので必要性はなくなった。
- `UserDict`
  - `dict`のサブクラスを作れなかった時代のもの。以下も同じ。
- `UserList`
- `UserString`
- `namedtuple()`関数
  - 名前付きタプル。
  - `namedtuple("typename", ["x", "y"])`で typename という名前の x と y という属性を持つ名前付きタプルを作成する。
  - 型注釈がつけられないので`typing.NamedTuple`のほうが良い。

## `collections.abc`
コンテナの基底抽象クラス
```
Iterable  ─┬─── Iterator  ─────── Generator
           ├─── Reversible ───┐
           └─┐                │
Container ───┤                │
Sized     ─┬─┴─ Collection ─┬─┴── Sequence ─┬──── MutableSequence
           │                │               └──── ByteString
           │                ├──── Mapping ─────── MutableMapping
           │                ├──── Set     ───┬─── MutableSet
           │                └──┐             │
           └─── MappingView ─┬─┴─ ValuesView │
                             │               ├─┐
                             ├───────────────╂─┴─ ItemsView
                             │               └─┐
                             └─────────────────┴─ KeysView
Hashable
Callable
Awaitable ────── Coroutine
AsyncIterable ── AsyncIterator ── AsyncGenerator
Buffer
```

||抽象|
|-|-|
|Iterable|`__iter__`|
|Container|`__contains__`|
|Sized|`__len__`|

||mixin|抽象|
|-|-|-|
|Iterator|`__iter__`|`__next__`|
|Reversible|---|`__reversed__`|
|Collection|---|`__contains__`, `__iter__`, `__len__`|
|MappingView|`__len__`|---|

||mixin|抽象|
|-|-|-|
|Generator|`close`, `__iter__`, `__next__`|`send`, `throw`|
|Sequence|`__contains__`, `__iter__`, `__reversed__`, `index`, `count`|`__getitem__`, `__len__`|
|Mapping|`__contains__`, `keys`, `items`, `values`, `get`, `__eq__`, `__ne__`|`__getitem__`, `__iter__`, `__len__`|
|Set|`__le__`, `__lt__`, `__eq__`, `__ne__`, `__gt__`, `__ge__`, `__and__`, `__or__`, `__sub__`, `__xor__`, `isdisjoint`|`__contains__`, `__iter__`, `__len__`|
|ValuesView|`__contains__`, `__iter__`|---|

||mixin|抽象|
|-|-|-|
|MutableSequence|Sequence から継承したメソッドと、 `append`, `clear`, `reverse`, `extend`, `pop`, `remove`, `__iadd__`|`__getitem__`, `__setitem__`, `__delitem__`, `__len__`, `insert`|
|~~ByteString~~|~~Sequence から継承したメソッド~~|~~`__getitem__`, `__len__`~~|
|MutableMapping|Mapping から継承したメソッドと、 `pop`, `popitem`, `clear`, `update`, `setdefault`|`__getitem__`, `__setitem__`, `__delitem__`, `__iter__`, `__len__`|
|MutableSet|Set から継承したメソッドと、 `clear`, `pop`, `remove`, `__ior__`, `__iand__`, `__ixor__`, `__isub__`|`__contains__`, `__iter__`, `__len__`, `add`, `discard`|
|ItemsView|`__contains__`, `__iter__`|---|
|KeysView|`__contains__`, `__iter__`|---|



## `copy`
- `copy()` シャローコピー
- `deepcopy()` ディープコピー

## `pprint`
- `pp`
  - stream: 出力先
  - depth: 出力する深さ
  - compact: 長過ぎるリストをwidthの幅内でフォーマットする
  - sort_dicts: 辞書をキー順でソートする
- `pprint()`
  - ppのsort_dictのデフォルトをTrueにしたエイリアス。
- `pformat()`
  - 文字列で返す
- `isreadable()`
- `isrecursive()`
- `saferepr()`
- (class) `PrettyPrinter`

## `enum`

列挙型。

# 関数型プログラミング

## `itertools`
便利なイテレータ。
- `count(start=0, step=1)`
  - カウントアップ
- `cycle(iterable)`
  - 無限に循環
- `repeat(object[, times])`
  - 同じ値を繰り返し出力

- `accumulate(iterable[, func, *, initial=None])`
  - 畳み込み。デフォルトでは加算
- `batched(iterable, n)`
  - n個ごとにタプルとして分割して出力
- `chain(*iterables)`
  - 複数のイテラブルを順番に出力
- `chain.from_iterable(iterable)`
  - イテラブルのイテラブルを受け取り、chainと同様に処理する。遅延評価
- `compress(data, selectors)`
  - boolean列selectorを渡し、trueに対応する要素のみ出力
- `dropwhile(predicate, iterable)`
  - 述語を渡し、初めてfalseになった要素以降を出力
- `filterfalse(predicate, iterable)`
  - 述語を渡し、falseになる要素のみ出力
- `groupby()`
- `islice(iterable, stop)` / `islice(iterable, start, stop[, step])`
  - スライス
- `pairwise(iterable)`
  - 隣り合う2つのペアを出力
- `starmap(function, iterable)`
  - 関数を渡し、イテラブルの各要素(イテラブル)を引数展開(`*`)して関数に渡した結果を出力
- `takewhile(predicate, iterable)`
  - 述語を渡し、頭から始めてtrueであるかぎり出力
- `tee(iterable, n=2)`
  - 1つのイテラブルからn個のイテレータを返す
- `zip_longest(*iterables, fillvalue=None)`
  - 長い方に合わせてzip

- `product()`
  - 重複あり順序ありの組み合わせ
- `permutations()`
  - 重複なし順序ありの組み合わせ
- `combinations()`
  - 重複なし順序なしの組み合わせ、ソート順
- `combinations_with_replacement()`
  - 重複あり順序なしの組み合わせ、ソート順


## `functools`

関数に対する操作。

- `@cache`
  - 関数の戻り値をキャッシュする。`lru_cache(maxsize=None)`と等価。
- `@cached_property`
  - クラスのメソッドの戻り値をキャッシュし、プロパティに変換する。
- `cmp_to_key()`
- `@lru_cache`
  - 関数の戻り値をキャッシュする。キャッシュの最大個数を指定できる。
- `@total_ordering`
  - 1 つ以上の順序比較メソッド（`__lt__`, `__le__`, `__gt__`, `__ge__`）と`__eq__`が定義されているクラスを受取り、残りの順序比較メソッドを実装したクラスを返すデコレータ。
- `partial()`
  - 関数と位置引数、キーワード引数を受取り、partial オブジェクトを生成する。
  - partial オブジェクトは、元の関数にそれらの引数がデフォルト値として設定されたもののように振る舞う。
- (class) `partial`
  - partial() によって生成される呼び出し可能オブジェクト。
- (class) `partialmethod`
  - partial() と同様に、メソッドを partial 化する。
  - partial 化したメソッドを直接呼び出すのではなく、メソッドの定義に使用する。
- `reduce()`
  - javascript の reduce() と同じ機能。2 つの引数を持つ関数を iterable に左から順に適用し、最終的に単一の値を返す。
- `@singledispatch`
  - 関数をシングルディスパッチなジェネリック関数に変換する。
  - 別な場所から`@<funcname>.register`デコレータを用いて、第 1 引数の型に応じた別の実装を追加できるようになる。
- (class) `singledispatchmethod`
- `update_wrapper()`
  - ラッパーをラップする関数。ラッパーが返す関数の属性を差し替える。
  - update_wrapper はラッパー関数 wrapper とラップされる関数 wrapped を引数として受け取り、新しいラッパー関数を返す。新しいラッパー関数が返す関数は、もとのラッパー関数 wrapper が返す関数の属性の一部を、wrapped の属性で置き換えたものである。
  - デフォルトでは`__module__`, `__name__`, `__qualname__`, `__annotations__`, `__type_params__`, `__doc__`を上書きする。
  - `@wraps`を用いてこれをデコレータ内のラッパーに適用することで、ラッパーを更新し、ラップされる関数の属性で上書きできる。
- `@wraps`
  - ラップされる関数を引数 wrapped として受け取り、デコレートした関数をラッパーとして、update_wrapper() を呼び出す。

# ファイルとディレクトリ

## `fileinput` - 複数の入力ストリームをまたいで行を反復する

## `glob` - UNIX形式のパス名パターン展開

## `fnmatch` - UNIXファイル名パターンマッチ

## `shutil`
- `copyfileobj()`
- `copyfile()`
- `copymode()`
- `copystat()`
- `copy()`
- `copy2()`
- `ignore_patterns()`
- `copytree()`
- `rmtree()`
- `move()`
- `disk_usage()`
- `chown()`
- `which()`
- `make_archive()`
- `get_archive_formats()`
- `register_archive_format()`
- `unregister_archive_format()`
- `unpack_archive()`
- `register_unpack_format()`
- `unregister_unpack_format()`
- `get_unpack_formats()`
- `get_terminal_size()`

# データの永続化

## `sqlite3`

# ファイルフォーマット

## `csv`

## `configparser`

## `tomllib`

# OS サービス

## `io`

## `argparse`



# 並列

## `threading`

## `multiprocessing`

- Processオブジェクト
  - `Process(group, target, name, args, kwargs, daemon)`
    - `group` : None固定
    - `target` : callable
    - `name` :
    - `args` : 引数のタプル
    - `kwargs` : 引数（辞書）
    - `daemon` : デーモンプロセス
      - バックグラウンドで動作するプロセス。デーモンでないプロセスがすべて終了すると終了する。
  - `run()`
  - `start()`
  - `join()` : 終了を待つ
  - `name`
  - `is_alive()`
  - `daemon`
  - `pid`
  - `exitcode`
  - `authkey`
  - `sentinel`
  - `terminate()`
  - `kill()`
  - `close()`
- オブジェクト交換
  - Queue
  - Pipe
- プロセスの同期
  - 共有メモリ
  - サーバープロせス
- プール
  - Poolオブジェクト
- イベント



# 非同期

## `asyncio`

# インターネットデータ

## `json`

# インターネットプロトコル

## `urllib`

## `http.client`

## `http.server`

# プログラムフレームワーク

## `cmd`

# 開発ツール


## `unittest`

# デバッグとプロファイル

## `cProfile`, `profile`

## `timeit`

- `timeit()`
- `repeat()`
- `default_timer()`
- (class) `Timer`

## `tracemalloc`

# 配布

## `venv`

## `zipapp`

- `create_archive()`
- `get_interpreter()`

# Python ランタイムサービス



## `sysconfig`


## `dataclasses`

- `@dataclass`デコレータ
  - フィールドを初期化する`__init__()`を追加する。引数には型アノテーションが付く
    - フィールドに初期化子がついているならデフォルト引数にする
  - `__repr__()`, `__eq__()`も追加する
  - `__lt__()`, `__le__()`, `__gt__()`, `__ge__()`も追加できる（要オプション）
  - `__hash__()`も可
  - `frozen`オプションで読み取り専用にする
  - `kw_only`オプションで`__init__()`のすべての引数をキーワード専用にする
- `field()`
  - フィールドをカスタマイズする
- `Field`オブジェクト
  - `field()`の返すオブジェクト
- `fields()`
  - 渡したデータクラスまたはデータクラスオブジェクトの各フィールドオブジェクトのタプル
- `asdict()`
  - データクラスオブジェクトを辞書に変換する
- `astuple()`
  - データクラスオブジェクトをタプルに変換する
- `make_dataclass()`
  - データクラスを動的に作成する
- `replace()`
  - データクラスオブジェクトの指定したフィールドを置き換えたデータクラスオブジェクトを返す
- `is_dataclass()`
  - オブジェクトがデータクラスまたはデータクラスオブジェクトなら True
- `__post_init__()`
  - データクラス内で定義されていると、フィールドの初期化が行われた後に呼ばれる。

## `contextlib`

## `abc`

- (class) `ABC`
- (class) `ABCMeta`
- `@abstracctmethod`

# モジュールのインポート
## `importlib`


# Windows

## `winreg`

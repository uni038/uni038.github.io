- [一覧](#一覧)
- [組み込み関数](#組み込み関数)
- [テキスト](#テキスト)
  - [`string`](#string)
  - [`re`](#re)
  - [`textwrap`](#textwrap)
- [データ型](#データ型)
  - [`collections`](#collections)
  - [`collections.abc`](#collectionsabc)
  - [`copy`](#copy)
  - [`pprint`](#pprint)
  - [`enum`](#enum)
- [関数型プログラミング](#関数型プログラミング)
  - [`itertools`](#itertools)
  - [`functools`](#functools)
- [ファイルとディレクトリ](#ファイルとディレクトリ)
  - [`pathlib`](#pathlib)
  - [`os.path`](#ospath)
  - [`fileinput`](#fileinput)
  - [`glob`](#glob)
  - [`fnmatch`](#fnmatch)
  - [`shutil`](#shutil)
- [データの永続化](#データの永続化)
  - [`sqlite3`](#sqlite3)
- [ファイルフォーマット](#ファイルフォーマット)
  - [`csv`](#csv)
  - [`configparser`](#configparser)
  - [`tomllib`](#tomllib)
- [OS サービス](#os-サービス)
  - [`os`](#os)
  - [`io`](#io)
  - [`argparse`](#argparse)
  - [`logging`](#logging)
- [並列](#並列)
  - [`threading`](#threading)
  - [`multiprocessing`](#multiprocessing)
  - [`subprocess`](#subprocess)
- [非同期](#非同期)
  - [`asyncio`](#asyncio)
- [インターネットデータ](#インターネットデータ)
  - [`json`](#json)
- [インターネットプロトコル](#インターネットプロトコル)
  - [`urllib`](#urllib)
  - [`http.client`](#httpclient)
  - [`http.server`](#httpserver)
- [プログラムフレームワーク](#プログラムフレームワーク)
  - [`cmd`](#cmd)
- [開発ツール](#開発ツール)
  - [`typing`](#typing)
  - [`unittest`](#unittest)
- [デバッグとプロファイル](#デバッグとプロファイル)
  - [`cProfile`, `profile`](#cprofile-profile)
  - [`timeit`](#timeit)
  - [`tracemalloc`](#tracemalloc)
- [配布](#配布)
  - [`venv`](#venv)
  - [`zipapp`](#zipapp)
- [Python ランタイムサービス](#python-ランタイムサービス)
  - [`sys`](#sys)
    - [パス](#パス)
    - [その他](#その他)
  - [`sysconfig`](#sysconfig)
  - [`dataclasses`](#dataclasses)
  - [`contextlib`](#contextlib)
  - [`abc`](#abc)
- [モジュールのインポート](#モジュールのインポート)
  - [`importlib`](#importlib)
- [Windows](#windows)
  - [`winreg`](#winreg)

v3.12.4

> Python 標準ライブラリ — Python 3.12.4 ドキュメント \
> https://docs.python.org/ja/3/library/

# 一覧

- テキスト
  - `string`
  - `re` 正規表現
  - `difflib`
  - `textwrap`
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
  - `collections`
  - `collections.abc`
  - `heapq`
  - `bisect`
  - `array`
  - `weakref` 弱参照
  - `types`
  - `copy`
  - `pprint`
  - `reprlib`
  - `enum` 列挙型
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
  - `itertools`
  - `functools`
  - `operator`
- ファイルとディレクトリ
  - `pathlib`
  - `os.path`
  - `fileinput`
  - `stat`
  - `filecmp` ファイルとディレクトリの比較
  - `tempfile` 一時ファイルや一時ディレクトリの作成
  - `glob` Unix 形式パスの展開
  - `fnmatch`
  - `linecache`
  - `shutil` 高水準ファイル操作
- 永続化
  - `pickle`
  - `copyreg`
  - `shelve`
  - `marshal`
  - `dbm`
  - `sqlite3` SQLite インターフェース
- 圧縮、アーカイブ
  - `zlib`
  - `gzip`
  - `bz2`
  - `lzma`
  - `zipfile` zip
  - `tarfile` tar ファイルの読み書き
- ファイルフォーマット
  - `csv` CSV ファイル
  - `configparser`
  - `tomllib` TOML ファイル
  - `netrc` netrc ファイル
  - `plistlib`
- 暗号
  - `hashlib`
  - `hmac`
  - `secrets`
- 汎用 OS サービス
  - `os` OS インターフェース全般
  - `io` ストリーム
  - `time`
  - `argparse`
  - `getopt`
  - `logging` ロギング
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
  - `threading` スレッドベースの並列処理
  - `multiprocessing` プロセスベースの並列処理
  - `multiprocessing.shared_memory`
  - `concurrent`
  - `concurrent.futures`
  - `subprocess`
  - `sched`
  - `queue`
  - `contextvars`
  - `_thread`
- ネットワーク、プロセス間通信
  - `asyncio`
  - `socket`
  - `ssl`
  - `select`
  - `selectors`
  - `signal`
  - `mmap`
- インターネット上のデータ
  - `email`
  - `json`
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
  - `urllib` URL を扱うモジュール
  - `urllib.request`
  - `urllib.response`
  - `urllib.parse`
  - `urllib.error`
  - `urllib.robotparser`
  - `http`
  - `http.client`
  - `ftplib`
  - `poplib`
  - `imaplib`
  - `smtplib`
  - `uuid`
  - `sockerserver`
  - `http.server`
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
  - `cmd`
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
  - `typing` 型ヒント
  - `pydoc`
  - Python 開発モード
  - `doctest`
  - `unittest`
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
  - `timeit`
  - `trace`
  - `tracemalloc`
- ソフトウェアパッケージと配布
  - `ensurepip`
  - `venv` 仮想環境
  - `zipapp`
- ランタイムサービス
  - `sys`
  - `sys.monitoring`
  - `sysconfig` Python の構成情報
  - `builtins`
  - `__main__`
  - `warnings`
  - `dataclasses` データクラス
    - `@dataclass`
    - `field`
  - `contextlib` with 文コンテキスト用ユーティリティ
  - `abc`
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
  - `importlib`
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
  - `winreg`
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

## `re`

正規表現。

- `re.compile()` 正規表現文字列を正規表現オブジェクトにコンパイルする
- `re.search()` 最初にマッチする箇所のマッチオブジェクトを返す
- `re.match()` 先頭がマッチする場合のみ、マッチオブジェクトを返す
- `re.fullmatch()` 全体がパターン文字列にマッチする場合のみ、マッチオブジェクトを返す
- `re.split()` マッチ箇所で分割した文字列を返す
- `re.findall()` すべてのマッチ文字列のリストを返す。パターンがグループを持つ場合はタプルのリストを返す
- `re.finditer()` マッチオブジェクトを yield するイテレータを返す
- `re.sub()` 一番左でマッチした箇所を置換した文字列を返す
- `re.subn()` 一番左でマッチした箇所を置換した文字列と、置換した数とのタプルを返す
- `re.escape()`
- 正規表現オブジェクト `re.Pattern`
  - `Pattern.search()`
  - `Pattern.match()`
  - `Pattern.fullmatch()`
  - `Pattern.split()`
  - `Pattern.findall()`
  - `Pattern.finditer()`
  - `Pattern.sub()`
  - `Pattern.subn()`
  - `Pattern.flags`
  - `Pattern.groups`
  - `Pattern.pattern` 元のパターン文字列
- マッチオブジェクト `re.Match`
  - `Match.expand()`
  - `Match.group()` マッチグループ
  - `Match.groups()` すべてのマッチグループのタプル
  - `Match.groupdict()` グループの辞書。キーはグループ名
  - `Match.start()`
  - `Match.end()`
  - `Match.span()`
  - `Match.pos()`
  - `Match.endpos()`
  - `Match.lastindex()`
  - `Match.lastgroup()`
  - `Match.re()` マッチに使用した正規表現オブジェクト
  - `Match.string()` 文字列

## `textwrap`

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

- 1 次クラス
  - `Container`
    - 抽象：`__contains__`
  - `Hashable`
    - 抽象：`__hash__`
  - `Iterable`
    - 抽象：`__iter__`
  - `Sized`
    - 抽象：`__len__`
  - `Callable`
    - 抽象：`__call__`
  - `Awaitable`
    - 抽象：`__await__`
  - `AsyncIterable`
    - 抽象：`__aiter__`
  - `Buffer`
    - 抽象：`__buffer__`
- 2 次クラス
  - `Iterator` (Iterable)
    - mixin：`__iter__`
    - 抽象：`__next__`
  - `Reversible` (Iterable)
    - 抽象：`__reversed__`
  - `Collection` (Sized, Iterable, Container)
    - 抽象：`__contains__`, `__iter__`, `__len__`
  - `MappingView` (Sized)
  - `Coroutine` (Awaitable)
  - `AsyncIterator` (AsyncIterable)
- 3 次クラス
  - `Generator` (Iterator)
    - mixin：`close`, `__iter__`, `__next__`
    - 抽象：`send`, `throw`
  - `Sequence` (Reversible, Collection)
    - mixin：`__contains__`, `__iter__`, `__reversed__`, `index`, `count`
    - 抽象：`__getitem__`, `__len__`
  - `Set` (Collection)
  - `Mapping` (Collection)
  - `ValuesView` (MappingView, Collection)
  - `AsyncGenerator` (AsyncIterator)
- 4 次クラス
  - `MutableSequence` (Sequence)
    - mixin：Sequence から継承したメソッドと`append`, `clear`, `reverse`, `extend`, `pop`, `remove`, `__iadd__`
    - 抽象：`__getitem__`, `__setitem__`, `__delitem__`, `__len__`, `insert`
  - ~~`ByteString` (Sequence)~~ 3.14 で削除
  - `MutableSet` (Set)
  - `MutableMapping` (Mapping)
  - `ItemsView` (MappingView, Set)
  - `KeysView` (MappingView, Set)

## `copy`

- `copy()` シャローコピー
- `deepcopy()` ディープコピー

## `pprint`

- `pp()`
- `pprint()`
- `pformat()`
- `isreadable()`
- `isrecursive()`
- `saferepr()`
- (class) `PrettyPrinter`

## `enum`

列挙型。

# 関数型プログラミング

## `itertools`

便利なイテレータ。

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

## `pathlib`

パスの抽象化

- 純粋パス `PurePath`
  - 演算子`/`を使って子パスを作成できる
  - `PurePath.parts` パスの各セグメントのタプル
  - `PurePath.drive`
  - `PurePath.root`
  - `PurePath.anchor` ドライブ＋ルート
  - `PurePath.parent` 1 つ上の上位パス
  - `PurePath.parents[index]` index 個上の上位パス
  - `PurePath.name` 末尾
  - `PurePath.suffix` 拡張子
  - `PurePath.suffixex` 拡張子のリスト。拡張子が多重になっている場合用
  - `PurePath.stem` 末尾から拡張子を取り除いた部分
  - `PurePath.as_posix()` `\`を`/`に置換したパス
  - `PurePath.as_uri()` 先頭に`file://`を追加した URI 形式
  - `PurePath.is_absolute()`
  - ~~`PurePath.is_relative_to()`~~
  - `PurePath.is_reserved()`
  - `PurePath.joinpath()`
  - `PurePath.match()` このパスが指定した glob にマッチするかどうか
    - glob が相対の場合、パスを下から遡ってマッチする。
    - glob が絶対の場合、パスは絶対パスでなければマッチしない。
  - `PurePath.relative_to()` 指定パスからこのパスへの相対パス
  - `PurePath.with_name()` 末尾を指定した名前に変更したパス
  - `PurePath.with_stem()` stem を変更したパス
  - `PurePath.with_suffix()` suffix を変更したパス
  - `PurePath.with_segments()` parent や relative_to()が呼び出されたときに実行する関数
- 具象パス `Path`
  - classmethod `Path.home()` ホームディレクトリの具象パス
  - classmethod `Path.cwd()` カレントディレクトリの具象パス
  - `Path.absolute()` 絶対パスの具象パス。リンクは解決しない
  - `Path.resolve()` 絶対パスの具象パス。リンクを解決する
  - `Path.readlink()` リンクの参照先の具象パス
  - ファイルタイプとステータス
    - `Path.stat()`
    - `Path.lstat()`
    - `Path.exists()`
    - `Path.is_file()`
    - `Path.is_dir()`
    - `Path.is_symlink()`
    - `Path.is_junction()`
    - `Path.is_mount()`
    - `Path.is_socket()`
    - `Path.is_fifo()`
    - `Path.is_block_device()`
    - `Path.is_char_device()`
    - `Path.samefile()`
  - 読み書き
    - `Path.open()`
    - `Path.read_text()`
    - `Path.read_bytes()`
    - `Path.write_text()`
    - `Path.write_bytes()`
  - ディレクトリ
    - `Path.iterdir()` ディレクトリの内容の具象パスを yield する
    - `Path.glob()` このパスを基準に、指定した glob に一致するすべてのファイルを yield する
    - `Path.rglob()` glob() と同じだが、指定した glob の先頭に`**/`を追加する
    - `Path.walk()` 下位のディレクトリ名とその中のディレクトリ・ファイルのタプルを再帰的に yield する
  - ファイル・ディレクトリの作成
    - `Path.touch()`
    - `Path.mkdir()`
    - `Path.symlink_to()`
    - `Path.hardlink_to()`
  - `Path.rename()`
  - `Path.replace()`
  - `Path.unlink()`
  - `Path.rmdir()`
  - パーミッション
    - `Path.owner()`
    - `Path.group()`
    - `Path.chmod()`
    - `Path.lchmod()`

## `os.path`

- パスの取得
  - `os.path.abspath()` 絶対パス
  - `os.path.basename()` ファイル名部分
  - `os.path.commonpath()` 複数のパスの共通部分
  - ~~`os.path.commonprefix()`~~
  - `os.path.dirname()` ディレクトリ名
  - `os.path.realpath()` シンボリックリンクを解決したパス
  - `os.path.relpath()` 指定したディレクトリから見た相対パス
- パス操作
  - `os.path.expanduser()` パス先頭の`~`をユーザホームに置き換える
  - `os.path.expandvars()` パス内の環境変数を展開する
  - `os.path.join()` パスを結合する
  - `os.path.normname()` (Win) パスの大文字を小文字に、`/`を`\`に正規化する
  - `os.path.normpath()` パスを正規化する
  - `os.path.split()` パスを構成要素の末尾とそれ以外に分割する
    - 末尾が`/`を含むことはない。パスが`/`で終わる場合、末尾は空文字列になる
    - 末尾を除いた部分の最後の`/`は取り除かれる
  - `os.path.splitdrive()` パスをドライブレターとそれ以外に分割する。UNC パスの場合はホストネームとそれ以外に分割する。
  - `os.path.splitroot()` パスをドライブ、ルートパス、それ以外に分割する
  - `os.path.splitext()` パスを拡張子とそれ以外に分割する
- パスの判定
  - `os.path.exists()` パスが存在しているかどうか
  - `os.path.lexists()` exists と同じだが、壊れたシンボリックリンクも True
  - `os.path.isabs()` パスが絶対パスかどうか
  - `os.path.isfile()` パスがファイルかどうか
  - `os.path.isdir()` パスがディレクトリかどうか
  - `os.path.isjunction()` (NTFS) パスがジャンクションかどうか
  - `os.path.islink()` パスがシンボリックリンクかどうか
  - `os.path.ismount()` パスがマウントポイントかどうか
  - `os.path.isdevdrive()` パスが WindowsDevDrive かどうか
  - `os.path.samefile()` 2 つのパスが同じものを参照しているかどうか
  - `os.path.sameopenfile()` 2 つのファイルディスクリプタが同じファイルを参照しているかどうか
  - `os.path.samestat()` 2 つの stat が同じファイルを参照しているかどうか（→`os.stat()`）
- 情報
  - `os.path.getatime()` 最終アクセス時刻
  - `os.path.getmtime()` 最終更新時刻
  - `os.path.getctime()` (Unix) 最後にメタデータが変更された時刻 (Win) 作成時刻
  - `os.path.getsize()` ファイルサイズ

## `fileinput`

## `glob`

## `fnmatch`

## `shutil`

# データの永続化

## `sqlite3`

# ファイルフォーマット

## `csv`

## `configparser`

## `tomllib`

# OS サービス

## `os`

## `io`

## `argparse`

## `logging`

# 並列

## `threading`

## `multiprocessing`

## `subprocess`
- `run()` (function)
  - コンストラクタ
    - `args` コマンド。文字列または引数のシーケンス
    - `*`
    - `stdin`, `stdout`, `stdout`
    - `input`
      - 子プロセスの標準入力に渡す入力。
    - `capture_output`
      - stdoutとstderrをパイプする。両方を単一のストリームにしたいときは`stdout=PIPE, stderr=STDOUT`とする
    - `timeout` タイムアウト秒数
    - `check`
      - 子プロセスが非ゼロで終了した場合 CalledProcessError を投げる
    - `encoding`, `errors`, `text`
      - Popenと同じ
    - `env`
      - Popenと同じ
- `CompletedProccess` (class)
  - `args`
  - `returncode`
  - `stdout`, `stderr`
  - `check_returncode()`
- 定数等
  - ``
- `Popen` (class)
  - コンストラクタ
    - `args`
      - 実行するもの。シーケンス、文字列、path-like。
    - `bufsize`
      - パイプを使用するときのバッファーサイズ
    - `executable`　？
    - `stdin`, `stdout`, `stderr`
      - 標準入出力
      - None、PIPE、DEVNULL、ファイルディスクリプタ、ファイルオブジェクトが可
    - `preexec_fn` (POSIXのみ)
      - 子プロセスが生成された後、実行される前に子プロセス内で呼ばれるcallable。
    - `close_fds`
      - 0,1,2以外のファイルディスクリプタを、子プロセスが実行される前に閉じる
    - `shell`
      - シェルを使用する
    - `cwd`
      - 子プロセスの作業ディレクトリ
    - `env`
      - 子プロセスの環境変数
    - `universal_newlines` textと同じ
    - `startupinfo`
    - `creationflags`
    - `restore_signals` (POSIXのみ)
    - `start_new_session`
    - `pass_fds` (POSIXのみ)
    - `*`
    - `group`
    - `extra_groups`
    - `user`
    - `umask`
    - `encoding` 標準入出力のエンコーディング
    - `errors` 標準エラーのエンコーディング？
    - `text` 標準IOをテキストモードで開く？
    - `pipesize` 標準入出力のパイプサイズ (Linuxのみ)
    - `process_group`
  - `poll()`
  - `wait()`
  - `communicate()`
  - `send_signal()`
  - `kill()`
  - `args`
  - `stdin`, `stdout`, `stderr`
  - `pid`
  - `returncode`
  - Popenはコンテキストマネージャになれる。

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

## `typing`

- 組み込みの`type`
  - `type`文（組み込み）
    > https://docs.python.org/ja/3.12/reference/simple_stmts.html#the-type-statement
    ```
    type_stmt ::=  'type' identifier [type_params] "=" expression
    ```
    - 型エイリアスを定義する。
    - 型エイリアス自体の型は`typing.TypeAliasType`である。
  - (class) `TypeAliasType`
    - `type`文で定義された型エイリアスの型。
  - (class) `type`（組み込み）
    - 型オブジェクト。
    - コンストラクタに型を渡すと、その型を表す型オブジェクトを生成する。
      ```python
      t: type = type(int)
      ```
    - (GenericAlias) `type[T]`
      - `T`とみなせる型（`T`または`T`のサブクラス）を表す、ジェネリックな型オブジェクト。
- 特殊な型
  - (meta) `Any` 制約のないことを意味する型
  - (TypeVar) `AnyStr`
    - `str`か`bytes`を表す、定義済みの型変数。文字列系の関数向けの型
  - (class) `Annotated`
    - `Annotated[<type>, <metadata>]`の形式でメタデータを付加できる。
    - ※通常のクラスであり、特殊形式ではない。
- 特殊な形式（Special Form）
  - Special Form
    - `LiteralString`
      - 文字列のリテラルを意味する型。`str`は拒否する
      - 文字列リテラル同士の演算は受け入れることに注意。
    - `Never`, `NoReturn`
      - `return`しない関数の戻り値に使用する型。
    - `Self` クラス内において、現在のクラスを表すのに使用する型。
    - ~~`TypeAlias` 型エイリアスであることを意味する型。~~ --> 3.12 で非推奨。`type`文を推奨
    - `Union[]`
      - 3.10 以降は`|`でもよい。
    - `Optional[]`
      - `Optional[X]` は `Union[X, None]` と基本的に同義。
    - `Concatenate[]`
      - `ParamSpec`を結合する。
      - 高階関数（callable を引数に取る関数）向け。
    - `Literal[]` 指定したリテラルのみ許容する型。
    - `ClassVar[]` クラス変数であることを示すために使うラッパー。
    - `Final[]` 再アサイン禁止であることを示すラッパー。
      - `[]`は省略可。
      - クラス内の場合、サブクラスでのオーバーライドも禁止される。
    - `Required[]`, `NotRequired[]`
      - `TypedDict`のキーが必須である、または必須でないことを示すためのラッパー。
    - `TypeGuard[]` タイプガード関数の戻り値に使うラッパー。
    - `Unpack[]`
      - 型変数のタプル（`TypeVarTuple`）をアンパックすることを表すラッパー。
      - TypeVarTuple の頭にアンパック演算子`*` をつけるのと同じ。
- ジェネリック型
  - class
    - `Generic` ジェネリッククラスの抽象基底クラス
    - `TypeVar` 型変数クラス。
      - ジェネリック型の`[]`内の変数は TypeVar 型である。
      - ...
    - `TypeVarTuple` 型変数のタプルを表すクラス。
      - 型変数の前に`*`をつけるとそれは`TypeVarTuple`になる。
    - `ParamSpec` callable の引数の型の指定であることを表すためのクラス。
      - 型変数の前に`**`をつけるとそれは`ParamSpec`になる。
        ```python
        def add_logging[T, **P](f: Callable[P, T]) -> Callable[P, T]:
        ```
      - `ParamSpec.args`, `ParamSpec.kwargs`
    - `ParamSpecArgs`, `ParamSpecKwargs`
      - `ParamSpec.args`および`ParamSpec.kwargs`の型。
- その他
  - (function) `NamedTuple()`関数
    - `collections.namedtuple()`の型注釈付き版。
  - (class) `NewType`
    - 型注釈にのみ使える型。
    - 元にした型のサブクラスのように扱われる。
  - (meta) `Protocol` プロトコルクラスの基底クラス。構造的部分型を実現する
  - `@runtime_checkable`
  - (function) `TypedDict()`関数
- プロトコル
  - Protocol
    - `SupportsAbs`
    - `SupportsBytes`
    - `SupportsComplex`
    - `SupportsFloat`
    - `SupportsIndex`
    - `SupportsInt`
    - `SupportsRound`
- IO
  - class
    - `IO`
    - `TextIO`
    - `BinaryIO`
- 関数とデコレータ
  - `cast()` --> TypeGuard を使う。
  - `assert_type()`
  - `assert_never()`
  - `reveal_type()`
  - `@dataclass_transform`
  - `@overload`
  - `get_overloads()`
  - `clear_overloads()`
  - `@final`
    - 関数に使うとオーバーライドを禁止する。
    - クラスに使うと継承を禁止する。
  - `@no_type_check` --> Annotated
  - `@no_type_check_decorator` --> Annotated
  - `@override`
  - ~~`@type_check_only`~~
- イントロスペクション
  - `get_type_hints()`
  - `get_origin()`
  - `get_args()`
  - `is_typeddict()`
  - (class) `ForwardRef`
- 定数
  - `TYPE_CHECKING`
- 非推奨になったエイリアス
  - (class) `Dict`, `List`, `Set`, `FrozenSet`, `Tuple()`, `Type()`
  - (class) `DefaultDict`, `OrderedDict`, `ChainMap`, `Counter`, `Deque`
  - (class) `Pattern`, `Match`, `Text`
  - (class) `AbstractSet`, `ByteString`, `Collection`, `Container`, `ItemsView`, `KeysView`, `Mapping`, `MappingView`, `MutableMapping`, `MutableSequence`, `MutableSet`, `Sequence`, `ValuesView`
  - (class) `Coroutine`, `AsyncGenerator`, `AsyncIterable`, `AsyncIterator`, `Awaitable`
  - (class) `Iterable`, `Iterator`, `Callable`, `Generator`, `Hashable`, `Reversible`, `Sized`
  - (class) `ContextManager`, `AsyncContextManager`
- ellipsis

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

## `sys`
### パス
||||
|-|-|-|
|`base_exec_prefix`|ベース|
|`base_prefix`|ベース|
|`exec_prefix`|仮想環境の場合は仮想環境を指す|
|`prefix`|プラットフォーム依存なPythonファイルがインストールされたサイト固有ディレクトリプレフィックス。仮想環境の場合は仮想環境を指す|


### その他
||||
|-|-|-|
|`abiflags`||
|`addaudithook`||
|`argv`|argv[0]がスクリプトの名前|orig_argv
|`audit`||
|`byteorder`|プラットフォームのバイトオーダー|
|`builtin_module_names`|インタプリタコンパイル時に組み込まれているすべてのモジュール名|
|`call_tracing`||
|`copyright`|インタプリタの著作権表示|
|`_clear_type_cache`||
|`_current_frames`||
|`_current_exceptions`||
|`breakpointhook`|`breakpoint()`から呼ばれる|
|`_debugmallocstats`||
|`dllhandle`||
|`displayhook`||
|`dont_write_bytecode`|モジュールインポート時にpycファイルを生成しない|
|`_emscripten_info`||
|`pycache_prefix`|キャッシュ生成場所の指定|
|`excepthook`||
|`__breakpointhook__`||
|`__displayhook__`||
|`__excepthook__`||
|`__unraiseablehook__`||
|`exception`||
|`exc_info`||
|`executable`|pythonインタプリタの実行ファイルのパス|
|`exit`|SystemExit例外を発生させ、インタプリタを終了する|
|`flags`||
|`float_info`|float型に関する情報|
|`float_repr_style`|`repr()`のfloat型に対するふるまい|
|`getallocatedblocks`||
|`getunicodeinternedsize`||
|`getandroidapilevel`||
|`getdefaultencoding`||
|`getdlopenflags`||
|`getfilesystemencoding`|ファイルシステムのエンコーディング|
|`getfilesystemencodeerrors`||
|`get_int_max_str_digits`||
|`getrefcount`|objectの参照数|
|`getrecursionlimit`|最大再帰数|
|`getsizeof`|オブジェクトのバイト数を返す|
|`getswitchinterval`|インタプリタのスレッド切り替え間隔|
|`_getframe`||
|`_getframemodulename`||
|`getprofile`||setprofile
|`gettrace`||gettrace
|`getwindowsversion`|実行中のWindowsバージョン|
|`get_asyncgen_hooks`||
|`get_coroutine_origin_tracking_depth`||
|`hash_info`|ハッシュ実装のパラメータ|
|`hexversion`|pythonバージョンの単精度整数|
|`implementation`|pythonインタプリタの実装に関する情報|
|`int_info`|整数の内部表現に関する情報|
|`__interactivehook__`||
|`intern`||
|`is_finalizing`||
|`last_exc`||
|`last_type`||
|`last_value`||
|`last_traceback`||
|`maxsize`||
|`maxunicode`|Unicodeコードポイントの最大値|
|`meta_path`||
|`modules`|ロード済みのモジュールの辞書|
|`orig_argv`|Python実行ファイルに渡されたオリジナルのコマンドライン引数|
|`path`|モジュールの検索パスのリスト|
|`path_hooks`||
|`path_importer_cache`||
|`platform`|プラットフォームを表す文字列|
|`platlibdir`||
|`ps1`|インタプリタの1次プロンプト|
|`ps2`|インタプリタの2次プロンプト|
|`setdlopenflags`||
|`set_int_max_str_digits`||
|`setprofile`||
|`setrecursionlimit`||
|`setswitchinterval`||
|`settrace`||
|`set_asyncgen_hooks`||
|`set_coroutine_origin_tracking_depth`||
|`active_stack_trampoline`||
|`deactivate_stack_trampoline`||
|`is_stack_trampoline_active`||
|`_enablelegacywindowsfsencoding`||
|`stdin`|標準入力（ファイルオブジェクト）|
|`stdout`|標準出力|
|`stderr`|標準エラー出力|
|`__stdin__`||
|`__stdout__`||
|`__stderr__`||
|`stdlib_module_names`||
|`thread_info`|スレッドの実装に関する情報|
|`tracebacklimit`|捕捉されない例外が発生したときのトレースバックの最大レベル数。|
|`unraisablehook`||
|`version`|インタプリタのバージョン番号のほか、ビルド番号や使用コンパイラなどの情報|
|`api_version`|インタプリタのC APIバージョン|
|`version_info`|バージョン番号のタプル|
|`warnoptions`||
|`winver`||
|`monitoring`||
|`_xoptions`||


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

- [テキスト](#テキスト)
- [バイナリ](#バイナリ)
- [データ型](#データ型)
- [数学](#数学)
- [関数型プログラミング](#関数型プログラミング)
- [ファイルとディレクトリ](#ファイルとディレクトリ)
- [永続化](#永続化)
- [圧縮、アーカイブ](#圧縮アーカイブ)
- [ファイルフォーマット](#ファイルフォーマット)
- [暗号](#暗号)
- [汎用OSサービス](#汎用osサービス)
- [並列処理](#並列処理)
- [ネットワーク、プロセス間通信](#ネットワークプロセス間通信)
- [インターネット上のデータ](#インターネット上のデータ)
- [マークアップ](#マークアップ)
- [インターネットプロトコル](#インターネットプロトコル)
- [マルチメディア](#マルチメディア)
- [国際化](#国際化)
- [プログラムフレームワーク](#プログラムフレームワーク)
- [Tk](#tk)
- [開発ツール](#開発ツール)
- [デバッグ](#デバッグ)
- [ソフトウェアパッケージと配布](#ソフトウェアパッケージと配布)
- [ランタイムサービス](#ランタイムサービス)
- [カスタムのインタプリタ](#カスタムのインタプリタ)
- [モジュールのインポート](#モジュールのインポート)
- [Python言語関連](#python言語関連)
- [Windows固有](#windows固有)
- [Unix固有](#unix固有)


v3.12.4
> Python 標準ライブラリ — Python 3.12.4 ドキュメント \
> https://docs.python.org/ja/3/library/

# テキスト
- `string`
- `re` 正規表現
- `difflib`
- `textwrap`
- `unicodedata`
- `stringprep`
- `readline`
- `rlcompleter`

# バイナリ
- `struct`
- `codecs`

# データ型
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

# 数学
- `numbers`
- `math` 数学関数
- `cmath` 複素数用の数学関数
- `decimal` 固定十進数
- `fractions` 有理数
- `random` 乱数
- `statistics` 数学的統計関数

# 関数型プログラミング
- `itertools`
- `functools`
- `operator`

# ファイルとディレクトリ
- `pathlib`
- `os.path`
- `fileinput`
- `stat`
- `filecmp` ファイルとディレクトリの比較
- `tempfile` 一時ファイルや一時ディレクトリの作成
- `glob` Unix形式パスの展開
- `fnmatch`
- `linecache`
- `shutil` 高水準ファイル操作

# 永続化
- `pickle`
- `copyreg`
- `shelve`
- `marshal`
- `dbm`
- `sqlite3` SQLiteインターフェース

# 圧縮、アーカイブ
- `zlib`
- `gzip`
- `bz2`
- `lzma`
- `zipfile` zip
- `tarfile` tarファイルの読み書き

# ファイルフォーマット
- `csv` CSVファイル
- `configparser`
- `tomllib` TOMLファイル
- `netrc` netrcファイル
- `plistlib`


# 暗号
- `hashlib`
- `hmac`
- `secrets` 

# 汎用OSサービス
- `os` OSインターフェース全般
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

# 並列処理
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

# ネットワーク、プロセス間通信
- `asyncio`
- `socket`
- `ssl`
- `select`
- `selectors`
- `signal`
- `mmap`

# インターネット上のデータ
- `email`
- `json`
- `mailbox`
- `mimetypes`
- `base64`
- `binascii`
- `quopri`

# マークアップ
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

# インターネットプロトコル
- `webbrowser`
- `wsgiref` WSGI
- `urllib` URLを扱うモジュール
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

# マルチメディア
- `wave`
- `colorsys`

# 国際化
- `gettext`
- `locale`

# プログラムフレームワーク
- `turtle`
- `cmd`
- `shlex`

# Tk
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

# 開発ツール
- `typing` 型ヒント
- `pydoc`
- Python開発モード
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

# デバッグ
- 監査イベント表
- `bdb`
- `faulthandler`
- `pdb` Pythonデバッガ
- Pythonプロファイラ
- `timeit`
- `trace`
- `tracemalloc`

# ソフトウェアパッケージと配布
- `ensurepip`
- `venv` 仮想環境
- `zipapp`

# ランタイムサービス
- `sys`
- `sys.monitoring`
- `sysconfig` Pythonの構成情報
- `builtins`
- `__main__`
- `warnings`
- `dataclasses` データクラス
  - `@dataclass`
  - `field`
- `contextlib` with文コンテキスト用ユーティリティ
- `abc`
- `atexit`
- `traceback`
- `__future__`
- `gc`
- `inspect`
- `site`

# カスタムのインタプリタ
- `code`
- `codeop`

# モジュールのインポート
- `zipimport`
- `pkgutil`
- `modulefinder`
- `runpy`
- `importlib`
- `importlib.resources`
- `importlib.resources.abc`
- `importlib.metadata`
- `sys.path`

# Python言語関連
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

# Windows固有
- `msvcrt`
- `winreg`
- `winsound`

# Unix固有
- `posix`
- `pwd`
- `grp`
- `termios`
- `tty`
- `pty`
- `fcntl`
- `resource`
- `syslog`
- ``
- ``
- ``
- ``

- [`logging`](#logging)
    - [ロガー `Logger`](#ロガー-logger)
    - [ハンドラ `Handler`](#ハンドラ-handler)
    - [フォーマッタ `Formatter`](#フォーマッタ-formatter)
    - [フィルタ `Filter`](#フィルタ-filter)
    - [ログレコード `LogRecord`](#ログレコード-logrecord)
    - [モジュールレベル関数](#モジュールレベル関数)
  - [`logging.config`](#loggingconfig)
  - [`logging.handlers`](#logginghandlers)


# `logging`

- ログレベル
  |名前|数値||
  |-|-|-|
  |NOTSET|0|未定義|
  |DEBUG|10|デバッグ|
  |INFO|20|情報|
  |WARNING|30|警告|
  |ERROR|40|エラー|
  |CRITICAL|50|重大なエラー|

### ロガー `Logger`
- name : 名前
- level : 閾値。閾値より深刻度の低いメッセージは無視する
- setLevel(level)
- parent : 親ロガー
- propagate : Trueなら上位ロガーにもイベントを伝播する
- handlers : ハンドラ
- disabled
- isEnabledFor(level) : そのレベルがこのロガーで処理されるかどうか
- getEffectiveLevel()
  - 実効レベル。このロガーが`NOTSET`でないならそのレベル、設定されていないなら上位ロガーの`NOTSET`以外のレベルで一番近いもの
- getChild(suffix) : 子ロガー
- getChildren() : すべての（直接の）子ロガー
- ハンドラ
  - addHandler(handler)
  - removeHandler(handler)
  - hasHandlers() : ハンドラが設定されているかどうか。`propagate`を考慮して上位ロガーからも探す
  - handle(record) : 実際にハンドルする
- ログ
  - debug(msg), info(msg), warning(msg), error(msg), critical(msg)
  - log(level, msg) : 指定したレベルでログを出力する
  - exception(msg) : ERRORレベルのログ。例外ハンドラ用
- フィルタ
  - addFilter(filter)
  - removeFilter(filter)
  - filter(record) : フィルタを適用する
  - findCaller() : 呼び出し元のファイル名と行番号
  - makeRecord(name, level, fn, lno, msg, args, exc_info) : 特殊なレコード用のファクトリ

### ハンドラ `Handler`
- `__init__()`
- setLevel(level)
- flush() : すべてのログ出力をflushする。オーバーライド用
- close() : 使用しているすべてのリソースを閉じる。オーバーライド用
- handle(record) : このハンドラのフィルタに応じて出力する
- handleError(record) : `emit()`中に発生したエラーを処理する
- emit(record) : オーバーライド用
- スレッドロック
  - createLock()
  - acquire()
  - release()
- フィルタ
  - addFilter(filter)
  - removeFilter(filter)
  - filter(record)
- フォーマッタ
  - setFormatter(formatter)
  - format(record) : フォーマッタの適用

### フォーマッタ `Formatter`
- Formatter(...)
  - `__init__()`
    - fmt
    - datefmt
    - style
    - validate
    - defaults
  - format(record)
  - formatTime(record)
  - formatException(exc_info)
  - formatStack(stack_info)
- `BufferingFormatter`
  - formatHeader(records)
  - formatFooter(records)
  - format(records)

### フィルタ `Filter`
- filter()

### ログレコード `LogRecord`
- `__init__()`
  - name, level, pathname, lineno, msg, args, exc_info
- getMessage()
  |属性の名前|プレースホルダ||
  |-|-|-|
  |args|-||
  |asctime|`%(asctime)s`|生成された時刻|
  |created|`%(created)f`|生成された時刻|
  |exc_info|-|sys.exc_info風の例外タプル|
  |filename?|`%(filename)s`|pathnameのファイル名部分|
  |funcName|`%(funcName)s`|ロギングを呼び出した関数|
  |levelname|`%(levelname)s`|ログレベル|
  |levelno|`%(levelno)s`|ログレベル|
  |lineno|`%(lineno)d`|ロギングが呼び出された行番号|
  |message|`%(message)s`|ログメッセージ (`msg % args`)|
  |module|`%(module)s`|モジュール（filenameの名前部分|
  |msecs|`%(msecs)d`|生成された時刻のミリ秒部分|
  |msg|-|元のロギング呼び出しで渡されたフォーマット文字列|
  |name|`%(name)s`|ロガーの名前|
  |pathname|`%(pathname)s`|ロギングが呼び出されたファイルの完全なパス|
  |process|`%(process)d`|プロセスID|
  |processName|`%(processName)s`|プロセス名|
  |relativeCreated|`%(relativeCreated)d`|loggingモジュールが読み込まれた時刻に対する、ログが生成された時刻のミリ秒|
  |stack_info|-||スタックフレーム
  |thread|`%(thread)d`|スレッドID|
  |threadName|`%(threadName)s`|スレッド名|
  |taskName|`%(taskName)s`|`asyncio.Task`名|

### モジュールレベル関数
- getLogger(name)
  - ロガーを名前で取得する。nameは`__name__`が推奨。
- debug(msg), info(msg), warning(msg), error(msg), critical(msg), exception(msg), log(level, msg)
  - ルートロガーでログを出力する。
  - `basicConfig()`を呼び出す。
- disable(level=CRITICAL)
  - すべてのロガーのレベルを上書きし、level**以下**のログを出力しない。
  - `NOTSET`で呼び出せば元に戻る
- 名前関連
  - addLevelName(level, levelName)
  - getLevelNamesMapping()
  - getLevelName(level)
  - getHandlerByName(name)
  - getHandlerNames()
- makeLogRecord(attrdict)
  - 属性辞書からLogRecordを生成する。通信用
- basicConfig()
  - デフォルトのFormatterを持つStreamHandlerを生成してルートロガーに追加する。
- shutdown()
  - すべてのバッファをフラッシュしハンドラを閉じる。アプリケーション終了用
- getLoggerClass()
  - `Logger`クラスを返す。`setLoggerClass()`によって変更される。
- getLogRecordFactory()
  - `LogRecord`の生成に使われる callable を返す。
- setLoggerClass(klass)
  - ロガーの生成に使うクラスを設定する。
- setLogRecordFactory(factory)
  - `LogRecord`の生成に使う callable を設定する。

## `logging.config`

## `logging.handlers`
- StreamHandler
- FileHandler
- NullHandler
  - 何もしないハンドラ
- WatchedFileHandler
  - 記録先ファイルを監視するハンドラ。ファイルが変更された場合、同じファイル名で開き直す。Unix用
  - Windowsでは不要
- BaseRotatingHandler
  - RotatingFileHandler
    - ファイルサイズでローテートする
  - TimedRotatingFileHandler
    - 時間でローテートする
- SocketHandler
  - TCPで送信する
  - DatagramHandler
    - UDPで送信する
- SysLogHandler : Unixのsyslogに送る
- NTEventLogHandler : Windowsのイベントログに送る
- SMTPHandler : SMTPで送る
- MemoryHandler
  - メモリ上にバッファし、定期的に送り先にフラッシュする。BufferingHandlerのサブクラス
- HTTPHandler : HTTPで送る
- QueueHandler : `queue`モジュールや`multiprocessing`モジュールの queue に送る
- QueueListener : queueから受信する

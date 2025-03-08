# Powershell
- バージョン情報 `$PSVersionTable`
- ストリクトモード `Set-PSDebug -Strict`

- Windows PowershellとPowershell Coreがある


## 変数
- 定義
  - `$a = "Yamada"`
  - `[string]$str = 123` (型の宣言)
  - `$a = [int]"123"` (キャスト)
- 値を消去
  - `Clear-Variable -Name a`
  - `$a = null`
- 変数を削除
  - `Remove-Variable -Name a`
  - `Remove-Item -Path Variable:\a`
- コマンド置換 `$( … )`


## 型
変数の型は `$a.GetType()` で確認できる。
```powershell
Write-Host $a.GetType()
```

### ブール
|名前||.NET|
|-|-|-|
|bool|ブール|System.Boolean|
- `$true`, `$false`

### 数値
|名前||.NET|サフィックス|
|-|-|-|-|
|byte|8ビット|System.Byte|`uy`|
|sbyte|8ビット|System.SByte|`y`|
|short|16ビット|System.Int16|`s`|
|ushort|16ビット|System.UInt16|`us`|
|int16|16ビット|System.Int16||
|uint16|16ビット|System.UInt16||
|int|32ビット|System.Int32|`l`|
|uint|32ビット|System.UInt32|`ul`|
|int32|32ビット|System.Int32||
|uint32|32ビット|System.UInt32||
|long|64ビット|System.Int64||
|ulong|64ビット|System.UInt64||
|int64|64ビット|System.Int64||
|uint64|64ビット|System.UInt64||
|bigint|制限なし？|System.BigInteger|`n`|
|single|32ビット実数|System.Single||
|float|32ビット実数|System.Single||
|double|64ビット実数|System.Double||
|decimal|10進数|System.Decimal|`d`|
- 他にファイルサイズ用の `kb`, `mb`, `gb`, `tb`, `pb` というサフィックスもある
- 16進数プレフィックスとして `0x` がある
- 実数
  - `1.23e4` (1.23×10^4)

### 文字列
||||
|-|-|-|
|char|文字|System.Char|
|string|文字列|System.String|
- `"My name is $Name"` (変数展開される)
- `'My name is $Name'` (変数展開されない)
- 必要なら変数名を `{}` で囲む
- 文字列に `"` を含めたいときは `'` を使うか `""` とエスケープする。逆も同様
- `` ` `` でもエスケープできる
- ヒアドキュメントは以下。`"` と `'` のどちらでもOKで、違いも同じ。
    ```powershell
    $a = @"
    This is here-document.
    "@
    ```
- `*` でリピートする

### その他
||||
|-|-|-|
|void|型無し|System.Void|
|array|配列|System.Array|
|datetime|日時|System.DateTime|
|timespan|タイムスパン|System.TimeSpan|
|type|型|System.Type|
|hashtable|ハッシュテーブル|System.Collections.Hashtable|
|psobject|PowerScriptオブジェクト|System.Management.Automation.PSObject|
|Regex|正規表現|System.Text.RegularExpressions.Regex|
|scriptblock|スクリプトブロック|System.Management.Automation.ScriptBlock|
|switch|switchパラメータ|System.Management.Automation.SwitchParameter|
|xml|XMLドキュメント|System.Xml.XmlDocument|
- `$null`
- 配列
  - `@("a", "b", "c")`
    - `@(` `)` は省略して `"a", "b", "c"` とできる
  - `1..3`, `"A".."C"` のように範囲指定できる
  - 要素アクセスは `$a[0]`
    - スライスが使える `$a[0..3]`
    - `+` で要素を追加する。値を渡しても配列を渡しても結合される
    - 比較演算子でフィルターできる
    - `*` でリピートする
- ハッシュテーブル
  - `@{"x"=1; "y"=2; "z"=3}`
  - 要素アクセスは `$a["x"]`
  - `+` でハッシュテーブル同士を結合する
- TODO: 列挙型(enum)
- TODO: スクリプトブロック
  - `{ … }`
  - `& { … }` で実行する


## リダイレクト
- `>`, `>>`
- エラー `2>`
- エラーを成功に書き込む `2>&1`
    |||
    |-|-|
    |1|成功|
    |2|エラー|
    |3|警告|
    |4|詳細|
    |5|デバッグ|
    |6|情報|
    |*|すべてのストリーム|

## パイプ
- パイプ `|`
- パイプで渡されたオブジェクト `$_`
- `Where`, `Where-Object`
- TODO: フィルタ


## 演算子
- `+`, `-`, `*`, `/`, `%`
- `++`, `--`
- `=`, `+=`, `-=`, `*=`, `/=`, `%=`
- 比較 `-eq`, `-ne`, `-gt`, `-lt`, `-ge`, `-le`
- 正規表現一致 `-match`, `-notmatch`
- ワイルドカード一致 `-like`, `-notlike`
- 配列の要素 `-contains`, `-notcontains`
  - `-eq`系、`-match`系, `-like`系、`-contains`系は文字の大文字小文字を区別しない。区別したい場合はプレフィックス `c` をつける ( `-eq` → `-ceq` )
- `-and`, `-or`, `-not`
- ビット演算 `-band`, `-bor`, `-bnot`
- 文字列の分割 `-split`
- 文字列の結合 `-join`
    ```powershell
    -join "A", "B", "C"  # => "ABC"
    "A", "B", "C" -join ","  # => "A,B,C"
    ```
- 型演算
  - 型判定 `-is`, `-isnot`
    ```powershell
    "ABC" -is [string]
    ```
  - キャスト `-as`
    ```powershell
    123 -as [string]
    ```


## コマンドライン
- 行継続
- コマンド区切り


## 制御構文
- if-elseif-else
    ```powershell
    if  () {
    } elseif () {
    } else {
    }
    ```
- switch
    ```powershell
    switch () {
        <expr1> {}
        <expr2> {}
        Default {}
    }
    ```
    - フォールスルーしたくない場合は `break` が必要
    - `-Wildcard`オプションで判定式にワイルドカードを使えるようになる (`switch -Wildcard () { … }`)
    - `-Regex`オプションで判定式に正規表現を使えるようになる
    - 判定式には条件式を使える
        ```powershell
        switch ("file.txt") {
            {$_ -match "\.txt$"} { … }
        }
        ```
- for
    ```powershell
    for ( …; …; …) {
    }
    ```
- foreach
    ```powershell
    foreach (<value> in <array>) {
    }
    ```
    foreachは `ForEach-Object` のエイリアスである。オブジェクトのリストをパイプで受け取ることができる。また、`%` もエイリアスである。
    ```powershell
    Get-Process | foreach { … }
    Get-Process | % { … }
    ```
    - TODO: BEGINブロック、ENDブロック
- do-while
- do-until
- while `while () { … }`
- break
- continue
- throw
- try-catch-finally
    ```powershell
    try {
    }
    catch {
    }
    finally {
    }
    ```
- TODO: trap
  - エラーが発生した際に呼ばれる
- exit
  - Int32を終了コードとして投げられる

その他
- Powershellでは制御構文はローカルスコープを作らない。

## 関数
```powershell
function Hello {
}
function Hello ($Name, $Color) {
}
function Hello {
    param (
        $Name,
        $Color
    )
}
# 関数呼び出しはコマンドレットと同じように行う。
Hello "Yamada" "Red"
# 引数名を指定できる。
Hello -Color "Red" -Name "Yamada"
```
- 引数の型を指定できる。
    ```powershell
    function Add([int]x, [int]y) { … }
    ```
- 引数のデフォルト値を指定できる。
    ```powershell
    function Add(x = 0, y = 1) { … }
    ```
- TODO: 必須引数
- TODO: バリデートセット
- TODO: バリデートスクリプト
- 可変長引数
    ```powershell
    function Add([Parameter(ValueFromRemainingArguments)]$ArgList) { … }
    ```
  - `$args` に引数のリストが格納されるのでそちらを使うこともできる。
- 参照渡し
    ```powershell
    function Add([ref]$a) { … }
    ```
- `return`で値を返却する。`return`がない場合は最後の式の値が返る。
  - 複数の値を返却できる。
      ```powershell
      function Hello() { return "a", "b" }
      $x, $y = Hello
      ```
- `process` でパイプから受け取った配列に対して処理を行うことができる。
    ```powershell
    function DoubleValue {
        process { Write-Host ($_ * 2)}
    }
    ```
    - `begin`, `end` で開始時・終了時の処理を記述できる。
        ```powershell
        function DoubleValue {
            begin { … }
            process { Write-Host ($_ * 2)}
            end { … }
        }
        ```

## クラス
TODO:


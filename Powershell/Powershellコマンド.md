# コマンド
## エイリアス

## *-Command
CommandType|Name|Version|Source|
-----------|----|-------|------|
Function|Find-Command|1.0.0.1|PowerShellGet|
Cmdlet|Get-Command|3.0.0.0|Microsoft.PowerShell.Core|
Cmdlet|Invoke-Command|3.0.0.0|Microsoft.PowerShell.Core|
Cmdlet|Measure-Command|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|Show-Command|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|Trace-Command|3.1.0.0|Microsoft.PowerShell.Utility|
- `Get-Command`
  - `-Name`, `-Verb`, `-Noun` を指定してコマンドを返す (`CmdletInfo`)
  - `-Name` はエイリアスも指定できる (`Alias`)
  - `-Module` でモジュールを指定できる
  - `-Syntax` を指定するとコマンドの構文定義を説明した文字列を返す
  - `-ShowCommandInfo` で完全なコマンド説明を返す
- `Invoke-Command` ローカルまたはリモートでコマンドを実行する
- `Measure-Command` 実行時間を計測する
- `Show-Command` コマンドの情報をGUIで表示する
- `Trace-Command` 

## *-Alias

## *-Object
CommandType|Name|Version|Source|
-|-|-|-|
Cmdlet|Compare-Object|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|ForEach-Object|3.0.0.0|Microsoft.PowerShell.Core|
Cmdlet|Group-Object|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|Measure-Object|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|New-Object|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|Select-Object|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|Sort-Object|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|Tee-Object|3.1.0.0|Microsoft.PowerShell.Utility|
Cmdlet|Where-Object|3.0.0.0|Microsoft.PowerShell.Core|

- `Compare-Object` (`compare`, `diff`)
  - オブジェクトを比較する。比較はオブジェクトによる
- `ForEach-Object` (`%`, `foreach`)
  - 配列を反復処理する。構文が3つある。
  ```powershell
  ForEach-Object [-Process] <scriptblock[]> [-InputObject <psobject>] [-Begin <scriptblock>] [-End <scriptblock>] [-RemainingScripts <scriptblock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
  ```
  - `-Process` スクリプトブロックを指定する。省略可。2つ指定すると最初のブロックがbegin、3つ以上指定すると最後がendになる。
  - `-InputObject` 
  - `-Begin <scriptblock>` beginブロック。
  - `-End <scriptblock>` endブロック。
  ```powershell
  ForEach-Object [-MemberName] <string> [-InputObject <psobject>] [-ArgumentList <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
  ```
  - `-MemberName` メンバープロパティまたはメンバーメソッドの名前。インスタンスメンバー限定。
  ```powershell
  ForEach-Object -Parallel <scriptblock> [-InputObject <psobject>] [-ThrottleLimit <int>] [-TimeoutSeconds <int>] [-AsJob] [-UseNewRunspace] [-WhatIf] [-Confirm] [<CommonParameters>]
  ```
  - `-Paralell`
  - `-ThrottleLimit` 同時に実行する最大数。既定値は5。
- `Group-Object` オブジェクトのリストを特定の条件に基づいてグループ化する
- `Measure-Object` (`measure`)
- `New-Object` .NETオブジェクトまたはCOMオブジェクトを作成する
  - `-TypeName` クラス名の文字列。
- `Select-Object` (`select`) オブジェクトのプロパティや、配列のオブジェクトを選択する。
- `Sort-Object` (`sort`) オブジェクトをプロパティでソートする
- `Tee-Object` (`tee`) オブジェクトをteeする
- `Where-Object` (`?`, `where`) プロパティの値に基づいて選択する

エイリアス
- ForEach-Object -> %, foreach


## *-Item
CommandType|Name|Version|Source
-----------|----|-------|------
Cmdlet|Clear-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Copy-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Get-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Invoke-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Move-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|New-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Remove-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Rename-Item|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Set-Item|7.0.0.0    Microsoft.PowerShell.Management
- `New-Item` ファイルやディレクトリを作成する。
- `Get-Item` 指定したパスにあるアイテムを取得する。
  - `-Path`
  - `-LiteralPath` ワイルドカードを使用しない。エスケープは行う。
- `Move-Item` (`mv`)ファイルやディレクトリや変数を移動する。
- `Rename-Item` ファイルやディレクトリや変数をリネームする。
- `Copy-Item` (`cp`)ファイルやディレクトリをコピーする。
- `Remove-Item` (`rm`) ファイルや変数を削除する。
- `Invoke-Item` ファイルに既定のアクションを実行する。
- `Set-Item` 環境変数やレジストリなどの変数に値をセットする。
- `Clear-Item` 変数の値を消去する。

### *-ChildItem
- `Get-ChildItem` (`ls`)


## *-ItemProperty
CommandType|Name|Version|Source
-----------|----|-------|------
Cmdlet|Clear-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Copy-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Get-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Move-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|New-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Remove-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Rename-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Set-ItemProperty|7.0.0.0|Microsoft.PowerShell.Management
- `Clear-ItemProperty`
- `Copy-ItemProperty`
- `Get-ItemProperty`
- `Move-ItemProperty`
- `New-ItemProperty`
- `Remove-ItemProperty`
- `Rename-ItemProperty`
- `Set-ItemProperty`


## *-Content
CommandType|Name|Version|Source
-----------|----|-------|------
Cmdlet|Add-Content|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Clear-Content|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Get-Content|7.0.0.0|Microsoft.PowerShell.Management
Cmdlet|Set-Content|7.0.0.0|Microsoft.PowerShell.Management
- `Add-Content`
- `Clear-Content`
- `Get-Content` (`cat`)
- `Set-Content`

## *-Location
- `Get-Location` (`pwd`) 現在のディレクトリを返す
- `Set-Location` (`cd`) 現在のディレクトリを指定したパスに変更する
- `Push-Location` (`pushd`)
- `Pop-Location`(`popd`)


## *-Path
- `Convert-Path`
- `Join-Path`
- `Resolve-Path`
- `Split-Path`
- `Test-Path`


## *-Host
- `Clear-Host` (`clear`, `cls`)
- `Get-Host` 現在のホストを表すオブジェクトを取得する
- `Out-Host` 出力を表示する
- `Read-Host`
- `Write-Host`
  - `Write-Output` (`echo`)


## *-History
- `Add-History`
- `Clear-History`
- `Get-History` (`h`, `history`)
- `Invoke-History` (`r`)


## *-Variable
- `Clear-Variable`
- `Get-Variable`
- `New-Variable`
- `Remove-Variable`
- `Set-Variable`


## *-Process
- `Debug-Process`
- `Get-Process` (`ps`)
- `Start-Process` (`start`)
- `Stop-Process` (`kill`)
- `Wait-Process`


## *-String
- `Join-String`
- `Out-String`
- `Select-String`


## その他
- `Out-File`
- `Write-Output`
- `Start-Sleep` (`sleep`)

- [実行環境](#実行環境)
- [文法](#文法)
  - [用語](#用語)
  - [文](#文)
    - [単純文 (simple statement)](#単純文-simple-statement)
    - [複合文 (compound statement)](#複合文-compound-statement)
  - [式 (expression)](#式-expression)
  - [変数](#変数)
    - [スコープ](#スコープ)
    - [標準型](#標準型)
  - [演算子](#演算子)
  - [リスト・集合・辞書](#リスト集合辞書)
  - [関数](#関数)
    - [引数](#引数)
    - [デコレータ (関数)](#デコレータ-関数)
  - [クラス](#クラス)
    - [定義](#定義)
    - [クラス変数とインスタンス変数](#クラス変数とインスタンス変数)
    - [静的メソッド、クラスメソッド、インスタンスメソッド](#静的メソッドクラスメソッドインスタンスメソッド)
    - [特殊メソッド](#特殊メソッド)
    - [継承](#継承)
    - [デコレータ (クラス)](#デコレータ-クラス)
    - [メタクラス、MRO](#メタクラスmro)
  - [コルーチン (v3.5)](#コルーチン-v35)
  - [IO](#io)
  - [ライブラリ](#ライブラリ)
  - [非同期処理](#非同期処理)
- [属性](#属性)
- [ジェネリクス](#ジェネリクス)
- [標準ライブラリ](#標準ライブラリ)


> Python 言語リファレンス — Python 3.12.3 ドキュメント
> https://docs.python.org/ja/3/reference/index.html

# 実行環境
# 文法
## 用語



## 文
### 単純文 (simple statement)
> 7 単純文 (simple statement)\
> https://docs.python.org/ja/3/reference/simple_stmts.html
1. 式文
2. 代入文
3. `assert`文
4. `pass`文
5. `del`文
6. `return`文
7. `yield`文
8. `raise`文
9. `break`文
10. `continue`文
11. `import`文
12. `global`文
    - グローバル変数として解釈するよう宣言する
13. `nonlocal`文
    - （現在のスコープの1つ外側のスコープの変数として宣言する）
14. `type`文
    - 型のエイリアスを宣言する

### 複合文 (compound statement)
> 8 複合文 (compound statement)\
> https://docs.python.org/ja/3/reference/compound_stmts.html#
1. `if`文
2. `while`文
3. `for`文
4. `try`文
5. `with`文
6. `match`文 (v3.10)
7. 関数定義
8. クラス定義
9. コルーチン (v3.5)
10. 型パラメータリスト `[T]` (v3.12)

## 式 (expression)
- 丸括弧形式 `()`
- ジェネレータ式 `(… [async] for … in …)`
- `yield`式
- `await`式
- ラムダ式 `lambda`
- 式のリスト（？）
- 各種演算子による演算
  - Pythonでは演算子と式は特に区別しない。

## 変数
- pythonには宣言はなく、バインドによって変数を作る。バインドは以下の8つである。
  1. 関数のパラメータ
  2. クラス定義
  3. 関数定義
  4. 代入式
  5. （複合文のtarget）
  6. import文
  7. type文
  8. typeパラメータリスト

> https://docs.python.org/ja/3/reference/executionmodel.html#naming
- ブロック内でバインドされた名前は、`nonlocal`や`global`でない限りそのブロックの**ローカル変数**である。
- モジュールレベル（トップレベル）でバインドされたなら、ローカル変数であると同時に**グローバル変数**でもある。
- ブロックで使われているがそのブロックで定義されていない変数は自由変数である。

> https://docs.python.org/3/glossary.html#term-namespace
- 変数は**名前空間**に格納される。名前空間は辞書である。
- ローカル名前空間、グローバル名前空間、ビルトイン名前空間と、オブジェクトの中にネストされた名前空間がある。


解決
- ある名前がブロック内のどこかでバインドされている場合、そのブロック内でのその名前の使用はすべてその変数への参照として扱われる。(巻き上げ？)

### スコープ
- 名前の解決は、ネストの一番内側の近い方から順にスコープを辿って行われる。

### 標準型
> 3.2. 標準型の階層\
> https://docs.python.org/ja/3/reference/datamodel.html#the-standard-type-hierarchy
- `None`
- `NotImplemented`
- `Ellipsis`
- `numbers.Number`
  - `numbers.Integral`
    - `int`
    - `bool`
  - `numbers.Real` (`float`)
  - `numbers.Complex` (`complex`)
- シーケンス型
  - immutableシーケンス
    - string
    - tuple
    - bytes
  - mutableシーケンス
    - list
    - bytearray
- 集合型
  - 集合型（可変）
  - Frozen set型
- マッピング型
  - 辞書型
- 呼び出し可能型
  - ユーザ定義関数
  - インスタンスメソッド
  - ジェネレータ関数
  - コルーチン関数
  - 非同期ジェネレータ関数
  - 組み込み関数
  - 組み込みメソッド
  - クラス
  - クラスのインスタンス
- モジュール
- カスタムクラス
- クラスインスタンス
- IOオブジェクト（ファイルオブジェクト）
- 内部型
  - コードオブジェクト
  - フレームオブジェクト
  - トレースバックオブジェクト
  - スライスオブジェクト
  - 静的メソッドオブジェクト
  - クラスメソッドオブジェクト




## 演算子
  - 算術 `+` `-` `*` `@` `//` `/` `%` `**`
  - ビット `~` `<<` `>>` `&` `^` `|`
  - 比較 `<` `>` `==` `<=` `>==` `!=` `is` `is not` `in` `not in`
  - ブール `and` `or` `not`
  - 代入 `:=`
    - 代入と同時に右辺式の値を返す。
  - 条件式（三項） `… if … else …`
  - リスト表示、辞書表示、集合表示

## リスト・集合・辞書
- 内包表記

## 関数
> 8.7. 関数定義\
> https://docs.python.org/ja/3/reference/compound_stmts.html#function-definitions

### 引数
- 仮引数
  1. 位置またはキーワード
  2. 位置専用
  3. キーワード専用
  4. 可変長位置
  5. 可変長キーワード
  - デフォルト引数
- 実引数
  1. キーワード引数
  2. 位置引数
- アノテーション

### デコレータ (関数)

## クラス
> 8.8. クラス定義\
> https://docs.python.org/ja/3/reference/compound_stmts.html#class-definitions

### 定義
```python
@decorator(arg)
class class_name[type_params](parent_class):
  …
```
- クラス定義ブロックは例外的な名前解決を行う。
  - バインドされていないローカル変数がある場合は、グローバル名前空間から探す。
  - クラス定義ブロック内で定義される名前のスコープはそのクラスブロックに制限され、メソッドのブロックに拡大することはない。
  - 例外の例外として、annotaion scopeはこの例外に含まれない。
  ```python
  # NG
  class A:
    a = 42
    b = list(a + i for i in range(10))
  ```


### クラス変数とインスタンス変数
> https://docs.python.org/ja/3/reference/compound_stmts.html#class-definitions\
> プログラマのための注釈: クラス定義内で定義された変数はクラス属性であり、全てのインスタンス間で共有されます。インスタンス属性は、メソッドの中で `self.name = value` とすることで設定できます。クラス属性もインスタンス属性も `self.name` 表記でアクセスでき、この表記でアクセスしたとき、インスタンス属性は同名のクラス属性を隠蔽します。クラス属性は、インスタンス属性のデフォルト値として使えますが、そこにミュータブルな値を使うと予期せぬ結果につながります。 「記述子(デスクリプタ)」を使うと、詳細な実装が異なるインスタンス変数を作成できます。
- クラス変数
  - クラス定義に直接定義する。
  - `<classname>.<varname>`で参照できる。
  - クラス内からは、同名のインスタンス変数が定義されていないときのみ`self.<varname>`でも参照できるが、インスタンス変数に隠蔽されてしまうため推奨されない。
- インスタンス変数
  - `__init__()`内で`self.<varname> = xxx`で定義する。
  - クラス内から`self.<varname>`で参照できる。


### 静的メソッド、クラスメソッド、インスタンスメソッド

### 特殊メソッド
  > https://docs.python.org/ja/3/reference/datamodel.html#special-method-names
  - `__new__`
  - `__init__`
  - `__del__`
  - …

### 継承

### デコレータ (クラス)

### メタクラス、MRO

## コルーチン (v3.5)
>8.9. コルーチン\
> https://docs.python.org/ja/3/reference/compound_stmts.html#coroutines
- コルーチン関数定義 `async def`
- `async for`文
- `async with`文

## IO
## ライブラリ
## 非同期処理

----
# 属性
# ジェネリクス
# 標準ライブラリ

----
block:
    | NEWLINE INDENT [compound_stmt | simple_stmts]+ DEDENT
    | simple_stmts

simple_stmts:
    | simple_stmt !';' NEWLINE  # Not needed, there for speedup
    | ';'.simple_stmt+ [';'] NEWLINE

simple_stmt
  割当て、タイプエイリアス、star、return, import, raise, pass, del, yield, assert, break, continue, global, nonlocal

compound_stmt
  関数定義、クラス定義、if, with, for, try, while, match

- [実行環境](#実行環境)
- [文法](#文法)
  - [文](#文)
    - [単純文 (simple statement)](#単純文-simple-statement)
    - [複合文 (compound statement)](#複合文-compound-statement)
  - [式 (expression)](#式-expression)
  - [変数](#変数)
    - [標準型](#標準型)
  - [演算子](#演算子)
  - [リスト・集合・辞書](#リスト集合辞書)
  - [関数](#関数)
    - [引数](#引数)
    - [デコレータ](#デコレータ)
  - [クラス](#クラス)
    - [クラス変数とインスタンス変数](#クラス変数とインスタンス変数)
    - [特殊メソッド](#特殊メソッド)
    - [継承](#継承)
    - [デコレータ](#デコレータ-1)
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
- 宣言
  1. 修飾子なし（ローカル）
  2. `global`
  3. `nonlocal`
- ~~巻き上げ~~
- （スコープ？）

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
- モジュール




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

### デコレータ

## クラス
> 8.8. クラス定義\
> https://docs.python.org/ja/3/reference/compound_stmts.html#class-definitions

### クラス変数とインスタンス変数

### 特殊メソッド
  > https://docs.python.org/ja/3/reference/datamodel.html#special-method-names
  - `__new__`
  - `__init__`
  - `__del__`
  - …
### 継承

### デコレータ

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

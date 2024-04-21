- [全般](#全般)
  - [ES](#es)
  - [実行環境](#実行環境)
  - [厳格モード](#厳格モード)
- [文法](#文法)
  - [文と宣言](#文と宣言)
  - [式](#式)
  - [変数](#変数)
    - [宣言](#宣言)
    - [巻き上げ](#巻き上げ)
    - [特殊定数](#特殊定数)
    - [特殊変数](#特殊変数)
  - [演算子](#演算子)
  - [型](#型)
  - [配列](#配列)
    - [作成](#作成)
    - [操作など](#操作など)
  - [関数](#関数)
    - [引数](#引数)
    - [即時関数 (IIFE)](#即時関数-iife)
    - [ジェネレータ関数 `funciton*`](#ジェネレータ関数-funciton)
  - [オブジェクト `{}`](#オブジェクト-)
    - [メソッド](#メソッド)
    - [ゲッター、セッター](#ゲッターセッター)
    - [計算されたプロパティ名](#計算されたプロパティ名)
  - [制御構文](#制御構文)
  - [クラス](#クラス)
  - [IO](#io)
  - [非同期処理](#非同期処理)
  - [ライブラリ](#ライブラリ)


# 全般
## ES
- ES6=ES2015、以降はES2016, ES2017, ...

## 実行環境

## 厳格モード
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Strict_mode
```javascript
"use strict";
```
- グローバルまたは関数スコープに対して設定できる。
- 可変長引数、デフォルト引数、分割引数（？）のある関数には使用できない
- モジュールとクラスは常に厳格モードである

# 文法
## 文と宣言
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements

以下の9つが宣言(Declaration)である。
- `let` `const`
- `function` `function*` `async function` `async function*`
- `class`
- `export` `import` (モジュールの最上位限定)

以下が文(Statement)である。
- フロー関連 `return` `break` `continue` `throw` `if`...`else` `switch`
- 変数宣言関連 `var`
- ループ `do`...`while` `for` `for`...`in` `for`...`of` `for await`...`of` `while`
- 空文
- ブロック
  - 複数の文や宣言を並べて`{}`で囲ったもの。
- 式文
  - 単一の**式**(expression)からなる文。式単体では意味がないため通常は何らかの副次的な効果をもち、通常は次のどれか。他の文や宣言と区別できないような式（`function`キーワードなど）は禁止されており、その場合は`()`で囲う。
  1. 関数呼び出し
  2. 代入式（代入演算子）
  3. インクリメント/デクリメント
  4. `delete`演算子
  5. `yield`演算子, `yield*`演算子
  6. `import()`式
  7. タグ付きテンプレートリテラル
- ラベル、`debugger`

文と宣言の違い：
- ほとんどのフロー制御は文だけを受け入れる
- ラベルは文にのみ付けられる

## 式
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators

式(expression)は、何らかの値を返すもの。
- 基本式
  - `this`
    - 関数の実行のコンテキスト。https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/this
  - リテラル
    - `null` `true` `false`
    - 数値リテラル
    - 配列リテラル `[]`
    - オブジェクトリテラル `{}`
    - 文字列リテラル
    - 正規表現リテラル
    - テンプレートリテラル
      ```javascript
      [<func>]`<text>`
      ```
  - 関数式
    - `function`キーワード
    - `function*`キーワード
    - `async function`キーワード
    - `async function*`キーワード
  - クラス式
    - `class`キーワード
  - グループ化 `()`
- プロパティアクセス `obj.property` `<obj>["property"]` `?.`
- `new`式
- `new.target`
  - コンストラクタ内において、new演算子で呼び出されたかどうかを検出するための疑似プロパティ。newで呼ばれて以内ならundefined。
- `super`
- `import()`式
  - 関数風の式であり、関数ではない。
- `import.meta`
- 単項演算、二項演算、三項演算
- スプレッド構文

## 変数
### 宣言
- 変数名は大文字と小文字を区別する
- キーワードなしで宣言した変数はグローバル変数となる
- ローカル変数は以下のキーワードで宣言する
  - ~~`var` 関数スコープまたはグローバルスコープの変数~~ 使わない
  - `let` ブロックスコープのローカル変数
- `const` (定数)

### 巻き上げ
> https://developer.mozilla.org/ja/docs/Glossary/Hoisting

- タイプ1の巻き上げ：`function` `function*` `async function` `async function*`
  - 宣言より前の位置で変数の値を使用できる。
- タイプ2の巻き上げ：`var`
  - (同じスコープ内で)宣言より前に参照しても`ReferenceError`にならないが、`undefined`が返る。
- タイプ3の巻き上げ：`let` `const` `class`
  - 宣言だけがスコープ内で巻き上がり、宣言位置より前で参照すると`ReferenceError`になる。
  ```javascript
  const x = 1;
  {
    console.log(x); // -> ReferenceError
    const x = 2;
  }
  ```
- タイプ4の巻き上げ：`import` ※

### 特殊定数
- `true`/`false`
- `null`
- `undefined`
- `NaN`
- `Infinity`

### 特殊変数
- `arguments`
  - 関数が受け取った引数。引数不定のときしか使わないため、可変長引数を使うほうがよい。
- `global`
- `globalThis`

## 演算子
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators
- 代入 `=`
  - 算術代入 `*=` `/=` `%=` `+=` `-=` `**=`
  - ビット演算代入 `<<=` `>>=` `>>>=` `&=` `^=` `|=`
  - 論理代入 `&&=` `||=` `??=`
  - 分割代入 `[a,b]=arr` `{a,b}=obj` (ES2015)
    - 配列の要素やオブジェクトのプロパティを複数の変数に一括で代入する\
      ```javascript
      [x, y] = [10, 20];    // x=10, y=20
      [x, y, ...z] = [10, 20, 30, 40, 50];   // z=[30, 40, 50]
      ```
- 算術 `+` `-` `*` `/` `%` `**`(べき乗)
  - インクリメント・デクリメント `++` `--`
- 比較 `==` `!=` `===` `!==` `<` `>` `<=` `>=`
  - `===`
  - `instanceof`
  - `in` プロパティの判別
- ビット `<<` `>>` `>>>` `&` `|` `^` `~`
- 論理 `!` `&&` `||` `??`
  - `??` Null合体演算子
- 条件 `?` `:`
- オブジェクト
  - プロパティアクセサ `.<property>` `[<property>]`
  - オプショナルチェーン演算子 `?.`
    - 左辺がnullish(nullまたはundefined)の場合にundefinedを返す
  - プロパティの削除 `delete`
  - オブジェクトの型 `typeof`
  - プロトタイプチェーンの検査 `instanceof`
  - プロパティの検査 `in`
  - スプレッド `...` (ES2015)
    - 反復可能オブジェクトを展開する。
- その他
  - ジェネレータの操作 `yield` `yield*`
  - カンマ `,`
    - 前後の式を評価したあと右の式を返す。
  - `new`
    - インスタンスを作成する
    - `new.target` (疑似プロパティ)\
      new演算子で呼び出されたコンストラクターの中ではそのコンストラクター、それ以外ではundefined
  - `import.meta`
  - 動的インポート `import()`
  - 式の破棄 `void`
  - (非同期) `await`

## 型
※暫定。typeofの返す型
- undefined
- object
- boolean
- number
- bigint
- string
- symbol
- function

?
- 文字列
- 列挙型
- キャスト

## 配列
### 作成
  - `array = [e1, e2, ...]`
  - `array = new Array(e1, e2, ...)` あまり使わない
  - `array = Array.from(<arraylike>)` (ES2015)
    - 反復可能オブジェクトから配列を作成
    - arraylikeは配列やstring, set, mapなど
  - `array = Array.of(e1, e2, ...)` (ES2015)
    - new Arrayとほぼ同じ

### 操作など
情報
- 配列の長さ `array.length`
- 配列判定 `Array.isArray()`
- `array.entries()`
- `array.keys()`
- `array.values()`

操作
- `array.concat()`
- `array.join()`
- `array.push()`
- `array.pop()`
- `delete array[]`
- `array.sort()`

反復処理
- `array.forEach()`
- `array.map()`
- `array.filter()`
- `array.every()`
- `array.some()`

## 関数
```javascript
function myfunc() {}
```
```javascript
var f1 = function() {}
```
- javascriptの関数はすべて`Function`オブジェクトである
- 既定で`undefined`を返す
  - コンストラクタを`new`で呼ぶと`this`を返す（？）
- アロー`=>`を用いても定義できる (ES2015)
  ```javascript
  var f1 = () => {}
  ```
  - ただし`function`と`=>`では`this`の扱いが変わる。`function`の`this`はその関数がバインドされているオブジェクトだが、`=>`の`this`はその関数の実行を指示するオブジェクトである。

### 引数
- デフォルト引数を指定できる (ES2015)
- 可変長引数を指定できる (ES2015)
  ```
  function myfunc(arg1, ...arg2) {}
  ```
  - 可変長引数は配列になる。
- 引数の末尾にカンマを許容する (ES2017)
- `arguments`オブジェクト
- (参照渡しは?)

### 即時関数 (IIFE)
> https://developer.mozilla.org/ja/docs/Glossary/IIFE
```javascript
(function(arg) {
  // ...
})();
```

<!-- ### バインド
- `func.call()`
- `func.apply()`
- `func.bind()` -->

### ジェネレータ関数 `funciton*`

## オブジェクト `{}`
### メソッド
オブジェクトのメンバーである関数をメソッドといい、簡略構文がある。
```javascript
const obj = {
  foo: function () {},
  bar: function* () {}
}
// 簡略化された構文
const obj = {
  foo() {},
  bar() {}
}
```

### ゲッター、セッター
- `get` `set`

### 計算されたプロパティ名


## 制御構文
- 通常のfor
  ```javascript
  for (let i = 0; i < limit; i++) {
  }
  ```
- 反復可能オブジェクト（配列等）の反復
  ```javascript
  for (const element of array) {
  }
  ```
- オブジェクトのプロパティの反復
  ```javascript
  for (const property in object) {
  }
  ```
- `while`
- `do...while`
- `for await...of`


## クラス
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Classes

クラスの実体は関数である。
- 宣言
  - クラス宣言またはクラス式を使う。
    ```javascript
    class myClass extends supderClass {
      static staticField1;
      #privateField;
      static {
        // 静的初期化
      }
      constructor() {
      }
      method1() {
      }
      #privateMethod() {
      }
      get getter1() {
      }
      set setter1() {
      }
    }
    ```
- 静的初期化ブロック `static{}`
- 静的プロパティ `static`
- プライベートプロパティ `#<property>`
- 継承 `extends`

## IO
- コンソール

## 非同期処理
- プロミス
- `async function`
- `async function*`

## ライブラリ
----
- 属性
- ジェネリクス

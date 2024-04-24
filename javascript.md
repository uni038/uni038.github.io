- [厳格モード (strict mode)](#厳格モード-strict-mode)
- [文法](#文法)
  - [文と宣言](#文と宣言)
  - [式](#式)
  - [変数](#変数)
    - [宣言](#宣言)
    - [スコープ](#スコープ)
    - [巻き上げ](#巻き上げ)
    - [型](#型)
    - [標準オブジェクト](#標準オブジェクト)
  - [演算子](#演算子)
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
  - [モジュール (ECMAScript Module (ESModule))](#モジュール-ecmascript-module-esmodule)
    - [エクスポート](#エクスポート)
    - [インポート](#インポート)
    - [その他](#その他)
- [付録](#付録)
  - [ECMAScriptの改定履歴](#ecmascriptの改定履歴)

以下より。
> JavaScript リファレンス - JavaScript | MDN
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference

# 厳格モード (strict mode)
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Strict_mode
```javascript
"use strict";
```
- グローバルまたは関数スコープに対して設定できる。
  - 可変長引数、デフォルト引数、分割引数（？）のある関数には使用できない
  - モジュールとクラスは常に厳格モードである

厳格モードで制限されるものは以下の通り。
1. 未宣言の変数（＝グローバル変数）への代入禁止
2. プロパティへの代入とプロパティの削除失敗時に例外を発生させる
3. 関数の引数名の重複禁止
4. 8進数リテラルの接頭辞`0`の禁止 (`0o`, `0O`はOK)
5. プリミティブ値へのプロパティの設定禁止
6. プロパティ名の重複禁止
7. `with`文禁止
8. `eval`がそのスコープに変数を作成しない
9. ブロックスコープ内関数宣言の挙動の明確化
   - 厳格モードではそのブロックの内部でしかその関数を参照できない
10. `eval`と`arguments`の挙動の単純化
    - `eval`と`arguments`への代入禁止
    - `arguments`と名前付き引数の値を別インスタンスにする
11. 関数に`this`として渡された値をオブジェクトに変換（ボックス化）しない
12. stack-walkingプロパティの除去
    - `Function.caller`, `Function.arguments`
    - `arguments.callee`
13. 予約語の追加（既に使われているものもある）
    - `let`, `static`, `yield` （使用済み）
    - `implements`, `interface`, `package`, `private`, `protected`, `public`


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
- 空文 (`;`)
- ブロック
  - 複数の文や宣言を並べて`{}`で囲ったもの。
- 式文
  - 単一の**式**(expression)からなる文。式単体では意味がないため通常は何らかの副次的な効果をもち、通常は次のどれか。他の文や宣言と区別できないような式（`function`キーワードなど）は禁止されており、その場合は`()`で囲う。詳細は[式](#式)を参照。
  1. 関数呼び出し
  2. 代入式（代入演算子）
  3. インクリメント/デクリメント
  4. `delete`演算子
  5. `yield`演算子, `yield*`演算子
  6. `import()`式
  7. タグ付きテンプレートリテラル
- ラベル
- `debugger`

文と宣言にはいくつかの違いがある。
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
- `import()`式（ダイナミックインポート）
  - 関数風の式であり、関数ではない。
- `import.meta`
- 単項演算、二項演算、三項演算
- スプレッド構文

## 変数
### 宣言
- ローカル変数は以下のキーワードで宣言する
  - ~~`var`文 関数スコープまたはグローバルスコープの変数~~ 使わない
  - `let`宣言 （ブロックスコープのローカル変数）
  - `const`宣言 （定数）
- キーワードなしで宣言した変数はグローバル変数となる
- 変数名は大文字と小文字を区別する

### スコープ
1. グローバルスコープ
2. モジュールスコープ
3. 関数スコープ
4. ブロックスコープ

### 巻き上げ
> https://developer.mozilla.org/ja/docs/Glossary/Hoisting

- タイプ1の巻き上げ：`function` `function*` `async function` `async function*`
  - 宣言より前の位置で変数の値を使用できる。
- タイプ2の巻き上げ：`var`
  - (同じスコープ内で)宣言より前に参照しても`ReferenceError`にならないが、`undefined`が返る。
- タイプ3の巻き上げ：`let` `const` `class`
  > 一時的なデッドゾーン (TDZ)
  > https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/let#%E4%B8%80%E6%99%82%E7%9A%84%E3%81%AA%E3%83%87%E3%83%83%E3%83%89%E3%82%BE%E3%83%BC%E3%83%B3_tdz
  - 宣言だけがスコープ内で巻き上がり、宣言位置より前で参照すると`ReferenceError`になる。
  ```javascript
  const x = 1;
  {
    console.log(x); // -> ReferenceError
    const x = 2;
  }
  ```
- タイプ4の巻き上げ：`import` ※

### 型
> JavaScript のデータ型とデータ構造 - JavaScript | MDN
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Data_structures \
> 文法とデータ型 - JavaScript | MDN
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Grammar_and_types

7つのプリミティブ型と`object`型がある。
- `null`
- `undefined`
  - nullはキーワード、undefinedは識別子であるが、実用上の影響はない。
- `boolean`
  - `true`
  - `false`
- `number` (数値型)
  - 8進数リテラル：先頭が`0`, `0o`, `0O`で始まる数値
  - 16進数リテラル：先頭が`0x`, `0X`
  - 2進数リテラル：先頭が`0b`, `0B`
  - 浮動小数点数リテラル
- `bigint` (長整数型)
  - 数値リテラルの末尾に`n`を付ける。
- `string`
  - `""`
  - `''`
  - テンプレートリテラル
    ```javascript
    ``
    ```
- `symbol` (シンボル型)
- `object`
  - `{}`

### 標準オブジェクト
> 標準組み込みオブジェクト - JavaScript | MDN
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects

グローバルスコープにあり、どこからでもアクセスできるオブジェクト。
- 値プロパティ
  - `Infinity`
  - `NaN`
  - **`undefined`**
  - `globalThis`
- 関数プロパティ\
  グローバルな関数。
  - `eval()`
  - `isFinite()`
  - `isNaN()`
  - `parseFloat()`
  - `parseInt()`
  - `encodeURI()`
  - `encodeURIComponent()`
  - `decodeURI()`
  - `decodeURIComponent()`
- 基本オブジェクト
  - **`Object`**
  - `Function`
  - `Boolean` (booleanのラッパー)
  - `Symbol`
- エラーオブジェクト
  - `Error`
  - ...
- 数値と日付
  - `Number` (numberのラッパー)
  - `BigInt` (bigintのラッパー)
  - `Math`
  - `Date`
- テキスト処理
  - `String` (stringのラッパー)
  - `RegExp`
- インデックス付きコレクション
  - `Array`
  - `Int8Array`
  - `Uint8Array`
  - ...
- キー付きコレクション
  - `Map`
  - `Set`
  - `WeakMap`
  - `WeakSet`
- 構造化データ
  - `ArrayBuffer`
  - `SharedArrayBuffer`
  - `Atomics`
  - `DataView`
  - `JSON`
- 制御抽象化オブジェクト
  - `Promise`
  - `Generator`
  - `GeneratorFunction`
  - `AsyncFunction`
  - `AsyncGenerator`
  - `AsyncGeneratorFunction`
- リフレクション
  - `Reflect`
  - `Proxy`
- 国際化
  - `Intl`
  - ...
- WebAssembly
  - `WebAssembly`
  - ...
- その他
  - `arguments`
    - 関数が受け取った引数 。引数不定のときしか使わないため、可変長引数を使うほうがよい。


## 演算子
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators
- 代入 `=`
  - 算術代入 `*=` `/=` `%=` `+=` `-=` `**=`
  - ビット演算代入 `<<=` `>>=` `>>>=` `&=` `^=` `|=`
  - 論理代入 `&&=` `||=` `??=`
  - 分割代入 `[a,b]=arr` `{a,b}=obj` (ES2015)
    - 配列の要素やオブジェクトのプロパティを複数の変数に一括で代入する
      ```javascript
      [x, y] = [10, 20];    // x=10, y=20
      [x, y, ...z] = [10, 20, 30, 40, 50];   // z=[30, 40, 50]
      ```
- 算術 `+` `-` `*` `/` `%` `**`(べき乗)
  - インクリメント・デクリメント `++` `--`
- 比較 `==` `!=` `===` `!==` `<` `>` `<=` `>=`
  - `===`
  - `instanceof`
  - `in` プロパティの存在
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
  - ただし`function`と`=>`では`this`の扱いが変わる。`function`の`this`はその関数がバインドされているオブジェクトだが、`=>`の`this`はその関数の実行を指示するオブジェクト(?)である。

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
（未）

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
- `for...of` : 反復可能オブジェクト（配列等）の反復
  ```javascript
  for (const element of array) {
  }
  ```
- `for...in` : オブジェクトのプロパティの反復
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

## モジュール (ECMAScript Module (ESModule))
> JavaScript モジュール - JavaScript | MDN
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Modules
### エクスポート
- 名前付きエクスポート宣言 `export`
  - `let`, `const`, `var`, 関数、クラスをエクスポートできる
  - `export {name1, name2}`で別の場所で宣言した変数をまとめてエクスポートできる
  - `as`で名前を変更できる
    ```js
    export { myFunction as function1, myVariable as variable };
    ```
- デフォルトエクスポート `export default`
  ```js
  // 以下2つは同等
  export { myFunction as default };
  export default myFunction;
  ```
  - モジュールで1度のみ使用できる
  - 値1つだけをエクスポートしたいときに使う
  - あらゆる式をエクスポートできる
  - インポート時にインポート側で名前を付ける
    ```js
    import m from "./test";  // 元の名前に関係なくmになる
    ```
- 再エクスポート `export from`
  - 別のモジュールからインポートすると同時にエクスポートできる
    ```js
    // デフォルトをfunc1としてエクスポート、func2をそのままエクスポート？
    export { default as func1, func2} from "bar.js"  
    ```
  - 現在のモジュール内では参照できない
  - `export * from "module"`はmoduleモジュールのすべての**名前付き**エクスポートを再エクスポートする。複数使用して重複する名前があった場合はどちらも再エクスポートされない

### インポート
```js
// デフォルトエクスポートのインポート（デフォルトインポート）
import defaultexport from "module-name";
import {default as alias} from "module-name";
// 名前付きエクスポートのインポート
import {export1} from "module-name";
import {export1 as alias1} from "module-name";
import {export1, export2, …} from "module-name";
// 名前空間オブジェクトのインポート
import * as name from "module-name";
// 副作用のためだけのインポート（何の値もインポートされない）
import "module-name";
```
```js
// 複数種類同時にインポート
import defaultexport, * as name from "module-name";
import defaultexport, {export1, export2} from "module-name";
```
- 名前空間オブジェクトのデフォルトインポートは`.default`キーワードで参照する
- インポートされた値はエクスポートしたモジュール側からのみ動的に変更できる
- 動的インポート `import()`
  ```js
  import("module-name")`
  ```
  - モジュール名前空間オブジェクトを返す

### その他
- インポートマップ
- トップレベル`await`


# 付録
## ECMAScriptの改定履歴
> proposals/finished-proposals.md at main · tc39/proposals
> https://github.com/tc39/proposals/blob/main/finished-proposals.md
- ES2016
  - `Array.prototype.includes`
  - Exponentiation operator (べき乗演算子)
    - `**`
- ES2017
  - `Object.values`/`Object.entries`
  - String padding
    - `String.prototype.padStart`
    - `String.prototype.padEnd`
  - `Object.getOwnPropertyDescriptors`
  - Trailing commas in function parameter lists and calls
  - Async functions (非同期関数)
  - Shared memory and atomics
- ES2018
  - Lifting template literal restriction
  - `s` (`dotAll`) flag for regular expressions
  - RegExp named capture groups
  - Rest/Spread Properties
  - RegExp Lookbehind Assertions
  - RegExp Unicode Property Escapes
  - `Promise.prototype.finally`
  - Asynchronous Iteration (非同期イテレーション)
- ES2019
  - Optional `catch` binding
  - JSON superset
  - `Symbol.prototype.description`
  - `Function.prototype.toString` revision
  - `Object.fromEntries`
  - Well-formed `JSON.stringify`
  - `String.prototype.{trimStart,trimEnd}`
  - `Array.prototype.{flat,flatMap}`
- ES2020
  - `String.prototype.matchAll`
  - `import()`
  - `BigInt`
  - `Promise.allSettled`
  - `globalThis`
  - `for-in` mechanics
  - Optional Chaining
  - Nullish coalescing Operator
  - `import.meta`
- ES2021
  - `String.prototype.replaceAll`
  - `Promise.any`
  - WeakRefs (弱参照)
  - Logical Assignment Operators
  - Numeric separators
- ES2022
  - Class Fields (Private instance methods and accessors, Class Public Instance Fields & Private Instance Fields, Static class fields and private static methods)
  - RegExp Match Indices
  - Top-level `await` (トップレベルの`await`)
  - Ergonomic brand checks for Private Fields
  - `.at()`
  - Accessible `Object.prototype.hasOwnProperty`
  - Class Static Block
  - Error Cause
- ES2023
  - Array find from last (Arrayの末尾からのfind)
  - Hashbang Grammar (Hashbangの記述)
  - Symbols as WeakMap keys
  - Change Array by Copy

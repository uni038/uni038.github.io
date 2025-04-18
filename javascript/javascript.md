- [厳格モード (strict mode)](#厳格モード-strict-mode)
- [文法](#文法)
  - [文と宣言](#文と宣言)
  - [式、演算子](#式演算子)
    - [基本式](#基本式)
    - [左辺式](#左辺式)
    - [単項演算子](#単項演算子)
    - [算術演算子](#算術演算子)
    - [比較](#比較)
    - [ビット演算](#ビット演算)
    - [論理演算子](#論理演算子)
    - [条件演算子](#条件演算子)
    - [代入演算子](#代入演算子)
    - [その他](#その他)
  - [変数](#変数)
    - [宣言](#宣言)
    - [スコープ](#スコープ)
    - [巻き上げ](#巻き上げ)
    - [型](#型)
    - [標準オブジェクト](#標準オブジェクト)
  - [制御構文](#制御構文)
    - [反復処理メソッド](#反復処理メソッド)
    - [イテレータ (`yield`)](#イテレータ-yield)
  - [配列](#配列)
    - [作成](#作成)
    - [分割代入](#分割代入)
    - [スプレッド構文](#スプレッド構文)
    - [操作など](#操作など)
  - [関数](#関数)
    - [定義](#定義)
    - [引数](#引数)
    - [関数のバインド](#関数のバインド)
    - [即時関数 (IIFE)](#即時関数-iife)
    - [ジェネレーター関数 `funciton*`](#ジェネレーター関数-funciton)
    - [非同期関数](#非同期関数)
    - [非同期ジェネレーター関数](#非同期ジェネレーター関数)
    - [`new`演算子](#new演算子)
  - [オブジェクト `{}`](#オブジェクト-)
    - [メソッド](#メソッド)
      - [メソッドの定義形式](#メソッドの定義形式)
    - [ゲッター、セッター](#ゲッターセッター)
    - [計算されたプロパティ名](#計算されたプロパティ名)
    - [スプレッド構文](#スプレッド構文-1)
  - [クラス](#クラス)
  - [IO](#io)
  - [非同期処理](#非同期処理)
  - [モジュール (ECMAScript Module (ESModule))](#モジュール-ecmascript-module-esmodule)
    - [エクスポート](#エクスポート)
    - [インポート](#インポート)
    - [その他](#その他-1)
- [付録](#付録)
  - [ECMAScriptの改定履歴](#ecmascriptの改定履歴)

以下より。
> JavaScript リファレンス - JavaScript | MDN
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference

# 厳格モード (strict mode)
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Strict_mode
```js
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
  - 単一の**式**(expression)からなる文。式単体では意味がないため通常は何らかの副次的な効果をもち、通常は次のどれか。他の文や宣言と区別できないような式（`function`キーワードなど）は禁止されており、その場合は`()`で囲う。詳細は[式、演算子](#式、演算子)を参照。
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

## 式、演算子
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators

式(expression)は、何らかの値を返すもの。

### 基本式
- `this`
  - 関数が実行されるコンテキスト。https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/this#method_binding
- リテラル
  - `null`
  - 論理値
  - 数値
  - 文字列
  - 正規表現リテラル
  - テンプレートリテラル
- 配列リテラル（配列初期化子） `[]`
- オブジェクトリテラル（オブジェクト初期化子） `{}`
- 関数式 `function`, `function*`, `async function`, `async function*`
- クラス式 `class`
- グループ化 `()`

### 左辺式
- プロパティアクセサ `obj.property` `obj["property"]`
- オプショナルチェーン演算子 `?.`
  - プロパティアクセサの一種で、左辺が`null`や`undefined`の場合にエラーにならずに`undefined`を返す。
  - 関数呼び出し時にも使える。`[]`によるプロパティアクセス時にも使える。配列要素にも使える。
    ```js
    obj.myMethod?.()
    obj?.["property"]
    array1?.[3]
    ```
  - 代入演算の左辺値としては使用できない。
- `new`
- `new.target`
- `import.meta`
- `super`
- `import()`
  - 関数風の式であり、関数ではない。

### 単項演算子
- プロパティの削除 `delete`
- 値の破棄 `void`
- `typeof`
  - 変数のプリミティブ型か `"function"` を文字列で返す。
- `+`、正負反転 `-`、ビット否定 `~`、論理否定 `!`
- プロミスの待機 `await`
- インクリメント `++`、デクリメント `--`

### 算術演算子
- 加算 `+`、減算 `-`、乗算 `*`、除算 `/`、剰余 `%`、べき乗 `**`

### 比較
- `<`、`>`、`<=`、`>=`
- `instanceof`
  - あるオブジェクトが別のオブジェクトの子にあたるかどうかを返す。
- `in`
  - オブジェクトが特定のプロパティを持つかどうかを返す。
- 等価 `==`、`!=`
- 厳密等価 `===`、`!==`

### ビット演算
- 左シフト `<<`、右シフト `>>`、ビット符号なし右シフト `>>>`
- ビット積 `&`、ビット和 `|`、ビット排他的論理和 `^`

### 論理演算子
短絡評価を行う。
- 論理積 `&&`、論理和 `||`
- Null合体演算子 `??`
  - 左辺が`null`か`undefined`なら右辺の値を、そうでないなら左辺の値を返す。

### 条件演算子
- `? :`

### 代入演算子
- `=`, `+=`, `-=` …
- 分割代入
  - 右辺のどの値を何に代入するかを、左辺で指定する。

### その他
- yield演算子 `yield`, `yield*`
- スプレッド構文 `...obj`
  - 反復可能オブジェクトを関数の引数や配列リテラルの要素に展開する。
- カンマ演算子 `,`
  - 複数の式を評価し、最後の式の値を結果として返す。


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
  ```js
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
    ```js
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


## 制御構文
- 通常のfor
  ```js
  for (let i = 0; i < limit; i++) {
  }
  ```
- `for...of` : 反復可能オブジェクト（配列等）の反復
  ```js
  for (const element of array) {
  }
  ```
- `for...in` : オブジェクトのプロパティの反復
  ```js
  for (const property in object) {
  }
  ```
- `while`
- `do...while`
- `for await...of`

### 反復処理メソッド
- `every()`
- `filter()`
- `find()`
- `findIndex()`
- `findLast()`
- `findLastIndex()`
- `flatMap()`
- `forEach()`
- `map()`
- `some()`

### イテレータ (`yield`)
`{value, done}` を返す `next()` メソッドを持つオブジェクト。
- `value` : 返された値。シーケンスの次の値。
- `done` : シーケンスのすべての値を消費しているならtrue
  - done===trueのときにvalueが何を取るかは規約はない？


## 配列
### 作成
  - `array = [e1, e2, ...]`
  - `array = new Array(e1, e2, ...)` あまり使わない
  - `array = Array.from(<arraylike>)` (ES2015)
    - 反復可能オブジェクトから配列を作成
    - arraylikeは配列やstring, set, mapなど
  - `array = Array.of(e1, e2, ...)` (ES2015)
    - new Arrayとほぼ同じ

### 分割代入
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

右辺値の何を左辺に代入するかを左辺で定義する。

### スプレッド構文
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/Spread_syntax

配列やオブジェクトを、0個以上のものが期待される場所に展開する

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
> 関数 - JavaScript | MDN\
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions

### 定義
- 関数宣言
  ```js
  function myfunc() {}
  ```
  - 関数宣言は巻き上げが行われる
- 関数式
  ```js
  const f1 = function() {}
  const f2 = function someFunction() {}
  ```
- アロー関数式
  > アロー関数式 - JavaScript | MDN\
  > https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/Arrow_functions
  ```js
  const f = (args) => {}
  ```
  - ~~アロー関数式の中に記述された変数はそれがバインドされたオブジェクトのコンテキストではなく、アロー関数式の記述された場所のスコープで評価される。`this`等の扱いに注意~~
  - アロー関数式は`arguments`オブジェクトを持たない
- 備考
  - いずれの定義もクロージャである。すなわち、内部に記述された変数はその関数定義の記述された場所のスコープで評価される。
  - javascriptの関数はすべて`Function`オブジェクトである
  - 既定で`undefined`を返す
    - コンストラクタを`new`で呼ぶと`this`を返す（？）
### 引数
- デフォルト引数 (ES2015)
  ```js
  function myFunc(a, b = 1) {}
  ```
  - デフォルト引数に対して`undefined`を渡しても、デフォルト値が優先される
  - デフォルト値は呼び出し時に評価される
  - 自分より前の引数を参照できる
    ```js
    function myFunc(a, b = a) {}
    ```
  - 呼び出し時の引数が少ない場合、デフォルト値の有無にかかわらず左から順に代入される
    ```js
    function myFunc(a = 1, b) { return [a, b] }
    myFunc(2) // -> [2, undefined]
    ```
  - デフォルト値は分割代入できる
    ```js
    ```
- 可変長引数（残余引数） (ES2015)
  ```js
  function myfunc(arg1, ...arg2) {}
  ```
  - 最後の引数に`...`を付けると以降の引数を配列としてその引数に代入する
  - 要素が1つだけでも配列になる
  - 要素が空でも配列になる
- 引数の末尾にカンマを許容する (ES2017)
- `arguments`オブジェクト (deprecated)
  - 配列ではないため配列のプロパティを持たない
- 名前付き引数は存在しない。
  - 引数をオブジェクトで渡して関数側で分割代入することで擬似的に再現できるが...
    ```js
    function f1({a = 1, b = 2}) { return a + b }
    f1({ b = 10, a = 20 })
    ```
- (参照渡しは?)

### 関数のバインド
- `call`, `apply`, `bind`
  - TODO

### 即時関数 (IIFE)
> IIFE (即時実行関数式) - MDN Web Docs 用語集: ウェブ関連用語の定義 | MDN\
> https://developer.mozilla.org/ja/docs/Glossary/IIFE
```js
(function(arg) {
  // ...
})();
```

### ジェネレーター関数 `funciton*`
定義（関数宣言または関数式）
```js
// 関数宣言
function* myGeneratorFunction() {}
// 関数式
const myGeneratorFunction2 = function* () {}
const myGeneratorFunction3 = function* someFunc() {}
```
- TODO

### 非同期関数
```js
// 関数宣言
async function myFunc() {}
// 関数式
const myFunc2 = async function () {}
const myFunc3 = async function someFunc() {}
```

### 非同期ジェネレーター関数
```js
// 関数宣言
async function* myFunc() {}
// 関数式
const myFunc2 = async function* () {}
const myFunc3 = async function* someFunc() {}
```

### `new`演算子
- `new.target` 関数がnewで呼び出されたかどうかを検知する

## オブジェクト `{}`
### メソッド
> メソッド定義 - JavaScript | MDN\
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/Method_definitions

オブジェクトのメンバーである関数を**メソッド**といい、簡略構文がある。
```js
const obj = {
  foo: function () {},
  bar: function* () {},
  baz: async function () {},
  qux: async function* () {},
}
```
簡略化された構文
```js
const obj2 = {
  foo() {},
  *bar() {},
  async baz() {},
  async* qux() {},
}
```

#### メソッドの定義形式
> https://typescriptbook.jp/reference/functions/function-expression-vs-arrow-functions

関数宣言
```js
function f1() {}
```
値が関数式である変数
```js
const f1 = function () {}
```
値がアロー関数である変数
```js
const f1 = () => {}
```
- アロー関数のみ、`this`の指すものが関数定義時に決定される。
- 関数宣言のみ巻き上げが起こる。

### ゲッター、セッター
> ゲッター - JavaScript | MDN\
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/get \
> セッター - JavaScript | MDN\
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/set
- `get` `set`

### 計算されたプロパティ名
> 計算プロパティ名 （オブジェクト初期化子 - JavaScript | MDN）\
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/Object_initializer#%E8%A8%88%E7%AE%97%E3%83%97%E3%83%AD%E3%83%91%E3%83%86%E3%82%A3%E5%90%8D

### スプレッド構文
配列の項を参照。

## クラス
> クラス - JavaScript | MDN\
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Classes

クラスの実体は関数である。
- クラスの定義
  - クラス宣言
    ```js
    class MyClass {}
    ```
  - クラス式
    ```js
    const MyClass = class {}
    // 名前を付けてもよい
    const MyClass2 = class SomeClass {}
    ```
- クラスのメンバー
  - メソッド、フィールド
    ```js
    const MyClass {
      myField;
      myMethod() {}
    }
    ```
    - フィールドの既定値は`undefined`
    - 変数ではないため`let`等は不要
  - ゲッター、セッター
    ```js
    class MyClass {
      get myGetter() {}
      set mySetter(value) {}
    }
    ```
    - ゲッターは引数を持てない
    - ゲッターはフィールドと同じ名前を持てない
  - 静的メソッド、静的フィールド
    ```js
    const MyClass {
      static staticField;
      static staticMethod() {}
      // 静的初期化ブロック
      static {
        var x = this.staticField
      }
    }
    ```
    - 静的初期化ブロック
      - プライベート静的フィールドにアクセスできる
      - 複数定義できる
      - `this`でコンストラクターを参照できる
    - 静的フィールド、静的初期化ブロックは上から順に評価される
  - プライベートメンバー
    ```js
    const MyClass {
      #myField;
      #myMethod() {}
      constructor(value) {
        this.#myField = value; // 参照時も#を付ける
      }
    }
    ```
  - コンストラクター
    ```js
    const MyClass {
      myField;
      constructor(value) {
        this.myField = value;
      }
    }
    ```
- 継承
  ```js
  class MyClass extends ParentClass {
    constructor() {
      super()
    }
  }
  ```
  - `super`で親クラスのメンバーを参照できる
  - 子クラスのコンストラクターでは`super()`で親クラスのコンストラクターを参照できる。ただし`this`より前に使う必要がある
  - 子クラスのコンストラクターを定義しなかった場合、暗黙に引数が`super()`にそのまま渡り実行される


## IO
- コンソール

## 非同期処理
- プロミス

## モジュール (ECMAScript Module (ESModule))
> JavaScript モジュール - JavaScript | MDN
> https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Modules
### エクスポート
- 名前付きエクスポート宣言 `export`
  - モジュール内の最上位スコープでのみ使用できる
  - `let`, `const`, `var`, 関数、クラスをエクスポートできる
  - `as`で名前を変更できる
  - `export {name1, name2}`で別の場所で宣言した変数をまとめてエクスポートできる（※宣言前に参照できる）
    ```js
    export const a = 1;
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
    ```js
    export default 1 + 1;
    ```
  - インポート時にインポート側で名前を付ける
    ```js
    import m from "./test";  // 元の名前に関係なくmになる
    ```
- 再エクスポート `export from`
  - 別のモジュールからインポートすると同時にエクスポートできる
    ```js
    // bar.jsのデフォルトエクスポートをfunc1として名前付きエクスポート、
    // func2をそのまま名前付きエクスポート
    export { default as func1, func2 } from "bar.js"
    // これも可
    export { default, func2 } from "bar.js"
    ```
  - 現在のモジュール内では参照できない
  - importにはない`export * from "module"`構文はmoduleモジュールのすべての**名前付き**エクスポートを再エクスポートする
    - 複数使用し、重複する名前があった場合はどちらも再エクスポートされない

### インポート
- デフォルトエクスポートのインポート
  - 名前を付ける必要がある
  ```js
  import default_export from "module-name";
  import { default as module_alias } from "module-name";
  ```
- 名前付きエクスポートのインポート
  ```js
  // 個別にインポート
  import { export1, export2 as alias1, … } from "module-name";
  ```
- 名前空間のインポート
  ```js
  //（モジュールオブジェクトに名前を付ける必要がある）
  import * as name from "module-name";
  ```
  - 名前空間オブジェクトのデフォルトインポートは`.default`で参照できる
- 複数種類のインポート
  ```js
  import default_export, { export2, export3, … } from "module-name";
  import default_export, * as name from "module-name";
  ```
  - `import { default as module_alias, export2, export3, …}`はだめ？
- 動的インポート `import()`
  ```js
  import("module-name")`
  ```
  - モジュール名前空間オブジェクトを返す
- インポートされた値はエクスポートしたモジュール側からのみ動的に変更できる。

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

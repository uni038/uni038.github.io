# ES5
- ストリクトモード `use strict`
- ゲッターとセッター `get`、`set`
- `JSON.parse()`、`JSON.stringify()`
- `string.trim()`
# ES5.1
- `array.isArray()`

# ES2015 (ES6)
- クラス
- テンプレート文字列 ``` `${}` ```
  - タグ付きテンプレート
- モジュール `import`、`export`
- アロー関数 `=>`
- デフォルト引数
- 可変長引数 `... args`
- 定数 `const`
- 局所変数 `let`
- イテラブルのループ `for (` ... `of` ... `)`
- マップ `Map`
- セット `Set`
- 配列関数 `Array.from()`、`Array.of()`
- 分割代入（レスト構文） `[a,b, ...c] = `
- スプレッド構文 `...array`
- 型付き配列
  - `ArrayBuffer()`、`Int8Array`、`Uint8Array`、...
- シンボル型 `Symbol`
- 8進数、2進数
- 言語依存フォーマット
- 非同期処理 `Promise`

# ES2016
- `array.includes()`
- 冪乗演算子 `**`

# ES2017
- `obj.values()`、`obj.entries()`
- 文字列のパディング `str.padStart()`、`str.padEnd()`
- プロパティ記述子参照 `obj.getOwnPropertyDescriptors()`
- 関数末尾のカンマ
- 非同期処理 `async`, `await`
- （共有メモリ）

# ES2018
- テンプレート文字列の強化
- オブジェクトのスプレッド構文とレスト構文
- 正規表現の `s` (dotAll)フラグ
- 正規表現の名前付きキャプチャグループ
- 正規表現の前方マッチ条件
- 正規表現のUnicodeプロパティマッチ
- `Promise`
  - `finally`構文
  - `for await (` ... `of` ... `)` 構文

# ES2019
- `catch(e){}`の引数不要化
- `Symbol.description`
- JSON superset
- Well-formed `JSON.stringify`
- `function.toString()`がコメントも文字列化
- `Object.fromEntries()`
- `string.trimStart()`と`string.trimEnd()`
- `array.flat()`と`array.flatMap()`

# ES2020
- 任意精度整数 `BigInt`
- for-inループにおける順序保証
- ヌル合体演算子 `??`
- オプショナル連結 `?.`
- `globalThis`変数
- `string.matchAll()`
- ダイナミックインポート
- インポートの直接エクスポート `export * as` ... `from` ...
- モジュールのメタ情報 `import.meta`
- すべての非同期処理の完了を待つ `Promise.allSettled()`

# ES2021
- 論理代入演算子 `||= &&= ??=`
- 数値セパレータ
- `string.replaceAll()`
- いずれかの非同期処理が成功するのを待つ `Promise.any()`
- 弱参照 `WeakRef`

# ES2022
- トップレベル`await`
- クラスフィールド宣言
- プライベートフィールド、プライベートメソッド
- staticイニシャライズブロック
- オブジェクトの型チェックのためのプライベートフィールドに対する`in`演算子
- 正規表現の`d`フラグ （開始・終了インデックス）
- `Error.cause`によるエラーチェイン
- atで最後からN番目の要素を取得
- hasOwn()によるプロパティ保持チェック

# ES2023
- `Array.findLast()`、`Array.findLastIndex()`
- Hashbang Grammer `#!`

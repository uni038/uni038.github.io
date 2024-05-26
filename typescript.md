# 型
```ts
const num: number = 123;
```
- `boolean`, `number`, `string`, `null`, `undefined`, `symbol`, `bigint`
- リテラル型
  - ユニオン型と組み合わせることが多い
  ```ts
  const isTrue: true = true
  const num: 123 = 123
  const str: "foo" = "foo"
  ```
- `any`型
  - `noImplicitAny`オプションで暗黙のanyを規制できる
## オブジェクトのプロパティ
```ts
let box: { width: number; height: number };
let calc: {
    sum(x: number, y: number): number;  // メソッド構文
    // => でも可
    sum2(x: number, y: number) => number;  // 関数構文
}
```
- プロパティ区切りは`,`でもよい
- オブジェクトのプロパティは`readonly`にできる
    ```ts
    let obj: { readonly foo: number };
    ```
- オプションプロパティ `?`
    - そのプロパティを持たないオブジェクトも受け付ける
    ```ts
    let size: { width?: number };
    ```
- インデックス型
  - プロパティ名を指定せず型だけ指定する
  - `string`, `number`, `symbol`のみ可
    ```ts
    let obj: {
        [K: string]: number;
    }
    ```

## その他
- 配列
  - Type`[]`
  - `Array<T>`
- タプル
  - `[<type1>, <type2>, …]`
- 列挙型
    ```ts
    enum Posision {
        Top, Right, Bottom, Left,
    }
    ```
- ユニオン型 `|`
    ```ts
    let numberOrUndefined: number | undefined;
    ```
- インターセクション型 `&`
  - オブジェクトの交差型
  ```ts
  type a = { x: number; y: number};
  type b = { z: number };
  type c = a & b;
  ```
- 型エイリアス `type`
  ```ts
  type StringOrNumber = string | number
  ```
- `Record<Keys, Type>`

# アサーション
- constアサーション

# ジェネリクス


# インターフェース





# コンパイルオプション


# 構造的部分型

# `tsconfig.json`

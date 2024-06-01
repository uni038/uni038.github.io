# プリミティブ型
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
  - 何にでも代入できる
  - `noImplicitAny`オプションで暗黙のanyを規制できる
- `unknown`型
  - 何にも代入できない
- タプル型
  ```ts
  const list: [number, string, boolean];
  ```
- ユニオン型
  ```ts
  let numberOrUndefined: number | undefined;
  ```
  - 判別可能なユニオン型

# 関数の型
```ts
// アロー関数を使う構文
type Ftype1 = (num: number, …) => number;
// メソッド構文
type Ftype2 = {
    (num: number, …): number;
};
```
- 関数に対して`typeof`を使うと関数の型が得られる。
    ```ts
    type t1 = typeof f1;
    ```
- `void`型
  - 戻り値がない関数の戻り値に使う
- `never`型
  - `return`もしない（最後まで到達しない）関数の戻り値に使う
- オプション引数 `?`
  - `undefined`とのユニオン型になる
  ```ts
  function hello(person?: string) { … }
  ```

## オーバーロード
```ts
// 関数シグネチャ部分
function hello(person: string): void; // シグネチャ1
function hello(persons: string[]): void; // シグネチャ2
// 関数の実装部分
function hello(person: string | string[]): void {
  if (typeof person === "string") {
    console.log(`Hello ${person}`);
  } else {
    console.log(`Hello ${person.join(",")}`);
  }
}
```
- シグネチャを列挙し、本体を1つだけ書く
- シグネチャは具体度が高い順に書く

# 配列の型
```ts
// []
let array: number[];

// Array<>
let array: Array<number>;
```
- 挙動の違いはない

# オブジェクトの型
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
- インターセクション型 `&`
  - オブジェクトの交差型
  ```ts
  type a = { x: number; y: number};
  type b = { z: number };
  type c = a & b;
  ```
- constアサーション
  - オブジェクトリテラルのプロパティを再帰的に`readonly`にする

# その他
- 型エイリアス `type`
  ```ts
  type StringOrNumber = string | number
  ```
- 型アサーション
  - 型情報を指定する
  ```ts
  const value: string | number = "***";
  const len: number = (value as string).length;
  ```
- `Record<Keys, Type>`


# ジェネリクス
- `Awaited<T>`
- `Partial<T>`
  - オブジェクト型Tに対し、そのすべてのプロパティをオプショナルにした型
- `Required<T>`
  - オブジェクト型Tに対し、そのすべてのプロパティを必須にした型
- `Readonly<T>`
  - オブジェクト型Tに対し、そのすべてのプロパティをreadonlyにした型
- `Record<K,T>`
- `Pick<T,K>`
- `Omit<T,K>`
- `Exclude<U,E>`
  - ユニオン型Uの型のうち、型Eにも属する型をすべて除外した型
- `Extract<T,U>`
  - 型Tの中の型のうち、ユニオン型Uにも属する型をすべて取り出した型
- `NonNullable<T>`
  - Tからnull, undefinedを取り除いた型
- `Parameters<T>`
  - 関数型Tに対し、その引数からなるタプル型
- `ConstructorParameters<T>`
  - クラス型Tに対し、そのコンストラクターの引数からなるタプル型
- `ReturnType<T>`
  - 関数型Tに対し、その戻り値の型
- `InstanceType<T>`
  - Tのコンストラクタが返す型
- `NoInfer<T>`
  - 型推論を防ぐ
- `ThisParameterType<T>`
- `OmitThisParameter<T>`
- `ThisType<T>`
- テンプレートリテラルタイプ
  - `Uppercase<T>`
  - `Lowercase<T>`
  - `Capitalize<T>`
  - `Uncapitalize<T>`

# インターフェース
```ts
interface I1 {
    f1(): void;
}
```



# 
#### コンパイルオプション
#### 構造的部分型
#### `tsconfig.json`

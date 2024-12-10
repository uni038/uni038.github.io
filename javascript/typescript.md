# typescript
> https://www.typescriptlang.org/docs/

# プリミティブ型

```ts
const num: number = 123;
```

- `boolean`, `number`, `string`, `null`, `undefined`, `symbol`, `bigint`
- リテラル型
  - ユニオン型と組み合わせることが多い
  ```ts
  const isTrue: true = true;
  const num: 123 = 123;
  const str: "foo" = "foo";
  ```
- `any`型
  - 何にでも代入できる
  - `noImplicitAny`オプションで暗黙の any を規制できる
- `unknown`型
  - 何にも代入できない
- タプル型
  ```ts
  const list: [number, string, boolean];
  ```

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

- シグネチャを列挙し、本体を 1 つだけ書く
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
- インターセクション型 `&`
  - オブジェクトの交差型
  ```ts
  type a = { x: number; y: number };
  type b = { z: number };
  type c = a & b; // { x: number, y: number, z: number }
  ```
- インデックス型
  - プロパティ名を指定せず、キーの型だけ指定する
  - `string`, `number`, `symbol`のみ可
    ```ts
    let obj: {
      [K: string]: number;
    };
    ```
  - キーの型が string の場合、keyof は `string | number` を返す
- Mapped Types
  - キーの型が柔軟になったインデックス型
    ```ts
    type SystemSupportLanguage = "en" | "fr" | "it" | "es";
    type Butterfly = {
      [key in SystemSupportLanguage]: string;
    };
    ```
  - インデックス型と違い、宣言されたフィールド以外のプロパティは追加できない。追加したい場合はインターセクションを使う
- const アサーション
  - オブジェクトリテラルのプロパティを再帰的に`readonly`にする

# 型の演算

- 型エイリアス `type`
  ```ts
  type StringOrNumber = string | number;
  ```
- ユニオン型
  ```ts
  let numberOrUndefined: number | undefined;
  ```
- 判別可能なユニオン型
- `typeof`型演算子
  - 変数の型を返す
  - 識別子のみ受け取れる。値は受け取れない
- `keyof`型演算子
  - あるオブジェクトに対し、それのプロパティのキーを表すユニオン型
  ```ts
  type Book = {
    title: string;
    price: number;
  };
  type BookKey = keyof Book; // "title" | "price"
  ```
- インデックスアクセス型
  - オブジェクト型に対し、指定のプロパティ名でアクセスしたときに返る型
    ```ts
    type A = { foo: number; bar: string };
    type Foo = A["foo"]; // number
    type FooBar = A[keyof A]; // number | string
    ```
  - 配列型に対し、それの要素のユニオン型
    ```ts
    type MixedArray = (string | undefined)[];
    type T = MixedArray[number]; // string | undefined
    ```
  - タプル型に対し、それの要素の型
    ```ts
    type Tuple = [string, number];
    type T = Tuple[0];
    ```
- Conditional Types (`extends`)
  ```ts
  type IsString<T> = T extends string ? true : false;
  const a: IsString<"a"> = true;
  ```
  - `infer`

# ジェネリクス（ユーティリティタイプ）

- `Awaited<T>`
- `Partial<T>`
  - オブジェクト型 T に対し、そのすべてのプロパティをオプショナルにした型
- `Required<T>`
  - オブジェクト型 T に対し、そのすべてのプロパティを必須にした型
- `Readonly<T>`
  - オブジェクト型 T に対し、そのすべてのプロパティを readonly にした型
- `Record<K,T>`
  - キーの型が K で値の型が T であるインデックス型
- `Pick<T,K>`
  - オブジェクト型 T から、キー K だけを抜き出した型
- `Omit<T,K>`
  - オブジェクト型 T から、キー K を取り除いた型
- `Exclude<U,E>`
  - ユニオン型 U の型のうち、型 E にも属する型をすべて除外した型
- `Extract<T,U>`
  - 型 T の中の型のうち、ユニオン型 U にも属する型をすべて取り出した型
- `NonNullable<T>`
  - T から null, undefined を取り除いた型
- `Parameters<T>`
  - 関数型 T に対し、その引数からなるタプル型
- `ConstructorParameters<T>`
  - クラス型 T に対し、そのコンストラクターの引数からなるタプル型
- `ReturnType<T>`
  - 関数型 T に対し、その戻り値の型
- `InstanceType<T>`
  - T のコンストラクタが返す型
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
- 型引数の制約 (`extends`)
  ```ts
  function f1<T extends P>(args) {…}
  ```
- ユニオン分配
  - T がユニオン型 `X | Y` である場合、 `Generics<T>` は `Generics<X> | Generics<Y>`として解釈される
  - 分配したくない場合は型変数を `[]` で囲む

# インターフェース

```ts
interface I1 {
  f1(): void;
}
```
- 使わない。typeでよい
> https://zenn.dev/luvmini511/articles/6c6f69481c2d17

# その他

- 型アサーション
  - 型情報を指定する
    ```ts
    const value: string | number = "***";
    const len: number = (value as string).length;
    ```

## コンパイルオプション

## 構造的部分型

## `tsconfig.json`

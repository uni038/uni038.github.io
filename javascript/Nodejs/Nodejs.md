# Node.js
- https://nodejs.org/docs/latest/api/synopsis.html
- v24.5.0

```sh
node [options] [V8 options] [script.js | -e "script" | - ] [arguments]
```

## モジュール形式
### CommonJS
https://nodejs.org/docs/latest/api/modules.html
- Node.jsのモジュール形式
    ```js
    // circle.js
    const { PI } = Math;
    exports.area = (r) => PI * r ** 2;
    exports.circumference = (r) => 2 * PI * r;
    ```
    ```js
    const circle = require('./circle.js');
    console.log(`The area of a circle of radius 4 is ${circle.area(4)}`);
    ```
- `exports`自体に別のオブジェクトを割り当てることもできる
    ```js
    // Assigning to exports will not modify module, must use module.exports
    module.exports = class Square {
        constructor(width) {
            this.width = width;
        }

        area() {
            return this.width ** 2;
        }
    };
    ```
- デフォルトでは、Node.jsは以下のものはCommonJSとして扱う
  - `*.cjs`
  - 一番近い親package.jsonに `"type": "commonjs` が定義されている `*.js`
  - `*.js`または拡張子なしのファイルで、一番近い親package.jsonに `"type"` が定義されていないか、または親package.jsonがないファイル
    - ただし、CommonJSであっても`"type"`フィールドは明示的に定義すべき
  - `*.mjs`, `*.cjs`, `*.json`, `*.node`, `*.js`のいずれでもないファイル
- `require()`は常にモジュールをCommonJSとしてロードする。`import()`は常にESModuleとしてロードする

### ESModules (ECMA Script Modules)
https://nodejs.org/docs/latest/api/esm.html
- ブラウザ環境のモジュール形式
    ```js
    // addTwo.mjs
    function addTwo(num) {
        return num + 2;
    }

    export { addTwo };
    ```
    ```js
    import { addTwo } from './addTwo.mjs';

    console.log(addTwo(4));
    ```
- ESModulesを使う
  - `*.mjs`
  - `"type": "module`
  - `node --input-type="module"`
  - 指定がない場合、ソースコードを読んでESmodulesの文法があればESmodulesでロードする


## ライブラリ
- `node:assert`
- `node:async_hooks`
- `node:buffer`
- `node:child_process` サブプロセス
- `node:cluster` スレッドクラスター
- `node:console`
- `node:crypto` 暗号化関連
- `node:diagnostics_channel` 診断メッセージ用のメッセージチャンネル
- `node:dns` 名前解決
- `node:events`
- `node:fs` ファイルシステム
- globals
- `node:http`
- `node:http2`
- `node:https`
- `node:inspector` V8 inspector. いわゆる開発者ツール関連
- `node:module` モジュールのインスタンスを扱う
- `node:net` TCP通信用の非同期ネットワークAPI
- `node:os`
- `node:path`
- `node:perf_hooks` Web Performance API
- `node:process` 現在のプロセス
- `node:querystring` URLクエリ文字列のパース、フォーマット
- `node:readline`
- `node:repl` REPL
- `node:sqlite`
- `node:stream` ストリーム
- `node:string_decoder` Bufferを文字列にデコードする
- `node:test` テストツール
- `node:timers`
- `node:tls` TLS/SSL
- `node:trace_events`
- `node:tty`
- `node:dgram` UDP
- `node:url` URLの解決とパースのユーティリティ
- `node:util`
- `node:v8` V8エンジン
- `node:vm` V8仮想機械の中でコードを実行する
- `node:wasi` WebAssembly System Interface
- `node:crypto` Web Crypto API
- `node:worker_threads`
- `node:zlib` 圧縮


# nvm

# 参考
- V8 JavaScript engine https://v8.dev/





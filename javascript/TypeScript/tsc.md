# tsc
https://www.typescriptlang.org/docs/handbook/compiler-options.html

```sh
# カレントディレクトリにあるtsconfig.jsonを使ってコンパイルする
tsc
# tsconfig.jsonを使わずにデフォルトのコンパイルオプションでコンパイルする
tsc app.ts util.ts
# tsconfig.jsonをカレントディレクトリに作成する
tsc --init
# 指定したパスにあるプロジェクトをコンパイルする
tsc --project ./path/to/tsconfig.json

# その他使いそうなもの
tsc --watch
tsc --target esnext
tsc --module esnext
tsc --declaration <value>
```


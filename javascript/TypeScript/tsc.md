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

# tsconfig.json
- `files`: 含めるファイルのリスト。存在しないファイルがあるとエラー。globを使いたい場合は`include`を使う
- `extends`: 設定を継承する他の設定ファイル
- `include`: 含めるファイルのパターン(glob)。filesが指定されている場合は`[]`、されていない場合は`**/*`
- `exclude`: includeから除外するファイルのパターン
- `references` プロジェクトを論理的に分割し、参照する
- `compilerOptions`: 下記
- `watchOptions`: 下記
- `typeAcquisition`: 下記

## compilerOptions
### type checking関連
- allowUnreachableCode
- allowUnusedLabels
- alwaysStrict
- exactOptionalPropertyTypes
- noFallthroughCasesInSwitch: フォールスルー禁止
- noImplicitAny
- noImplicitOverride
- noImplicitReturns
- noImplicitThis
- noPropertyAccessFromIndexSignature
- noUncheckedIndexedAccess
- noUnusedLocals: 未使用変数
- noUnusedParameters: 未使用引数
- strict: ストリクトモード
- strictBindCallApply: `call`, `bind`, `apply`の引数を厳格化する
- strictBuiltinIteratorReturn
- strictFunctionTypes
- strictNullChecks
- strictPropertyInitialization
- useUnknownInCatchVariables

### Modules関連
- allowArbitraryExtensions
- allowImportingTsExtensions: TypescriptファイルがTypescript用拡張子(ts, mts, tsx)をインポートすることを許可する
- allowUmdGlobalAccess
- baseUrl
- customConditions
- module: プログラムのモジュールシステムを指定する (commonjs, es****)
- moduleResolution: モジュール解決
- moduleSuffixes
- noResolve
- noUncheckedSideEffectImports: "side effect imports"を禁止する
- paths
- resolveJsonModule
- resolvePackageJsonExports
- resolvePackageJsonImports
- rewriteRelativeImportExtensions
- rootDir: 型定義ファイル以外のすべてのファイルのルートパス。デフォルトで自動検知する
- rootDirs
- typeRoots
- types: コンパイルに含める型定義。`node_modules/@types`以下

### Emit関連
- declaration
- declarationDir
- declarationMap
- downlevelIteration
- emitBOM
- emitDeclarationOnly
- importHelpers
- inlineSourceMap
- inlineSources
- mapRoot
- newLine
- noEmit: 
- noEmitHelpers
- noEmitOnError
- outDir
- outFile
- preserveConstEnums
- removeComments
- sourceMap
- sourceRoot
- stripInternal

### JavaScript Support関連
- allowJs
- checkJs
- maxNodeModuleJsDepth

### Editor Support関連
- disableSizeLimit
- plugins

### Interop Constraints関連
- allowSyntheticDefaultImports
- erasableSyntaxOnly: enumやnamespaceなど実行に影響を与える構文を禁止する
- esModuleInterop
- forceConsistentCasingInFileNames
- isolatedDeclarations
- isolatedModules
- preserveSymlinks
- verbatimModuleSyntax: コンパイル時に、import/exportで`type`が付いているものは残し、ないものは消去する

### Backwards Compatibility関連
- charset
- importsNotUsedAsValues
- keyofStringsOnly
- noImplicitUseStrict
- noStrictGenericChecks
- out
- preserveValueImports
- suppressExcessPropertyErrors
- suppressImplicitAnyIndexErrors

### Language and Environment関連
- emitDecoratorMetadata
- experimentalDecorators
- jsx
- jsxFactory
- jsxFragmentFactory
- jsxImportSource
- lib: 使用するビルトインライブラリの種類。`ES2022`, `DOM`など
- libReplacement
- moduleDetection: スクリプトかモジュールかの判定。
- noLib
- reactNamespace
- target: コンパイル先の環境。`es2022`など
- useDefineForClassFields: 

### Compiler Diagnostics関連
- diagnostics
- explainFiles
- extendedDiagnostics
- generateCpuProfile
- generateTrace
- listEmittedFiles
- listFiles
- noCheck
- traceResolution

### Projects関連
- composite
- disableReferencedProjectLoad
- disableSolutionSearching
- disableSourceOfProjectReferenceRedirect
- incremental
- tsBuildInfoFile

### Output Formatting関連
- noErrorTruncation
- preserveWatchOutput
- pretty

### Completeness関連
- skipDefaultLibCheck
- skipLibCheck: 型定義ファイルの型検査をスキップする

### Command Line関連
- (none)

### Watch Options関連
- assumeChangesOnlyAffectDirectDependencies

## watchOptions
- watchFile
- watchDirectory
- fallbackPolling
- synchronousWatchDirectory
- excludeDirectories
- excludeFiles

## typeAcquisition
- enable
- include
- exclude
- disableFilenameBasedTypeAcquisition

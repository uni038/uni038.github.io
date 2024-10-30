# Prettier

> https://prettier.io/docs/en/

設定ファイルは以下の順で参照する。グローバル設定は存在しない。

1. npm
   - `package.json`
   - `package.yml`
2. `.prettierrc` (JSON / YAML)
3. 拡張子付き .prettierrc
   - `.prettierrc.json`
   - `.prettierrc.yml`
   - `.prettierrc.yaml`
   - `.prettierrc.json5`
4. js ソース
   - `.prettierrc.js`
   - `prettier.config.js`
5. JS モジュール
   - `.prettierrc.mjs`
   - `prettier.config.mjs`
6. cjs
   - `.prettierrc.cjs`
   - `prettier.config.cjs`
7. TOML
   - `.prettierrc.toml`

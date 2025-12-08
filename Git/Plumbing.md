# Plumbing Commands

## cat-file

## check-ignore - gitignoreのデバッグ
```sh
git check-ignore <pathname>…
git check-ignore --stdin
```
与えられたパスのうち、.gitignoreの対象になるもの(ignoreされるもの)を返す


## checkout-index - インデックスからファイルを作業ツリーにコピーする
## commit-tree - 新しいコミットオブジェクトを作成する
## count-objects - unpackedなオブジェクトの数とそのディスク消費量を見る
## diff-index - 
ツリーオブジェクトのblobを、作業ツリーまたはインデックスにある対応するパスのファイルと比較する。
```sh
git diff-index <tree-ish> [<path>…]
```

## for-each-ref - refの情報を出力
```sh
git for-each-ref [--stdin | <pattern>…]
```
- `pattern` : 指定されたパターンの１つ以上にマッチするrefを表示する


## hash-object

## ls-files - 作業ツリーやインデックスのファイルの情報を見る
```sh
git ls-files [<options>] [--] [<file>…]
```
- `-c | --cached` all files in index (default)
  - `-d | --deleted` - unstaged deletion
  - `-m | --modified` - unstaged modification
  - `-o | --others` - untracked files
  - `-s | --stage` - staged
  - `-u | --unmerged` - unmerged files
  - `-k | --killed`
  - `--resolve-undo`
- `-i | --ignored` - ignored files
  - `-c` または `-o` が同時に必要
  - `--exclude*` も必要
- `-x <pattern> | --exclude=<pattern>`
- `-X <file> | --exclude-from=<file>`
  - read exclude pattern from file
- `--exclude-standard`
  - デフォルトのignoreパターンを使う (`.git/info/exclude`, `.gitignore`)
- `-t` - ステータスを表示する
  - H : tracked (not unmerged or skip-worktree)
  - S : tracked and skip-worktree
  - M : tracked and unmerged
  - R : tracked file with unstaged removal/deletion
  - C : tracked file with unstaged modification/change
  - K : tracked fileと衝突しているuntracked file
  - ? : untracked file
  - U : resolve-undo information


## ls-tree - ツリーオブジェクトの内容を見る
```sh
git ls-tree <tree-ish> [<path>…]
```

## merge-base - マージに適した共通祖先を探す
```sh
git merge-base <commit> <commit>…
```

## read-tree
## rev-list
## rev-parse
## show-ref - refの一覧
```sh
git show-ref [<pattern>…]
```
- `--head` : HEADも表示する
- `--branches` : ローカルのブランチだけ表示する
- `--tags` : ローカルのタグだけ表示する
- `-d | --dereference` : タグをオブジェクトIDに解決して表示する
- `--verify`
- `--exists`

## symbolic-ref - symbolic refを確認・修正・削除する
```sh
# 参照先の表示
git symbolic-ref <name>
# 作成・修正
git symbolic-ref <name> <ref>
# 削除
git symbolic-ref --delete <name>
```
- `<name>`
  - symbolic refの名前
- `<ref>`
  - 新しい参照先
- `--no-recurse`

## update-index
## update-ref
## verify-pack
## write-tree

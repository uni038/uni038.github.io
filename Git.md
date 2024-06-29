- [対象バージョン: Git 2.43](#対象バージョン-git-243)
- [用語](#用語)
  - [remote-tracking branch (追跡ブランチ)](#remote-tracking-branch-追跡ブランチ)
  - [pathspec](#pathspec)
  - [ref, refs](#ref-refs)
  - [refspec](#refspec)
  - [git clone - リポジトリを複製する](#git-clone---リポジトリを複製する)
- [ローカル](#ローカル)
  - [git add - ファイルをインデックスに追加する](#git-add---ファイルをインデックスに追加する)
  - [git rm -ファイルをインデックスと作業ツリーから除外する](#git-rm--ファイルをインデックスと作業ツリーから除外する)
  - [git commit - インデックスをコミットする](#git-commit---インデックスをコミットする)
    - [全般](#全般)
    - [コミットメッセージ関連](#コミットメッセージ関連)
  - [git diff - 差分を取る](#git-diff---差分を取る)
    - [作業ツリー](#作業ツリー)
    - [コミット間](#コミット間)
  - [git log - コミットログを見る](#git-log---コミットログを見る)
  - [git restore - ファイルの復元](#git-restore---ファイルの復元)
  - [git stash - 一時的な退避](#git-stash---一時的な退避)
  - [git worktree -](#git-worktree--)
- [ブランチ](#ブランチ)
  - [git branch - ブランチの一覧・作成・削除](#git-branch---ブランチの一覧作成削除)
    - [ブランチを作成する](#ブランチを作成する)
    - [ブランチの一覧](#ブランチの一覧)
    - [上流ブランチを設定する](#上流ブランチを設定する)
    - [ブランチをリネーム/コピー/削除する](#ブランチをリネームコピー削除する)
  - [git show-branch - ブランチの分岐状況を見る](#git-show-branch---ブランチの分岐状況を見る)
  - [git checkout - インデックスと作業ツリーを指定した版にする](#git-checkout---インデックスと作業ツリーを指定した版にする)
    - [ブランチの切り替え](#ブランチの切り替え)
    - [ブランチの作成](#ブランチの作成)
    - [detached HEAD](#detached-head)
    - [インデックスからチェックアウト (git restore)](#インデックスからチェックアウト-git-restore)
  - [git switch - ブランチの切り替え](#git-switch---ブランチの切り替え)
  - [git merge - ブランチのマージ](#git-merge---ブランチのマージ)
- [リモートリポジトリ](#リモートリポジトリ)
  - [git remote - リモートリポジトリ情報の操作](#git-remote---リモートリポジトリ情報の操作)
    - [git remote](#git-remote)
    - [git remote add](#git-remote-add)
    - [git remote rename](#git-remote-rename)
    - [git remote remove](#git-remote-remove)
    - [git remote set-head](#git-remote-set-head)
    - [git remote set-branches](#git-remote-set-branches)
    - [git remote get-url](#git-remote-get-url)
    - [git remote set-url](#git-remote-set-url)
    - [git remote show](#git-remote-show)
    - [git remote prune](#git-remote-prune)
    - [git remote update](#git-remote-update)
  - [git fetch - 他のリポジトリから object や refs をダウンロードする](#git-fetch---他のリポジトリから-object-や-refs-をダウンロードする)
  - [git pull -](#git-pull--)
  - [git push - リモートの参照を更新する](#git-push---リモートの参照を更新する)
- [コミットの操作](#コミットの操作)
  - [git rebase - ブランチの根本を付け替える](#git-rebase---ブランチの根本を付け替える)
  - [git reset - HEAD を指定した状態にリセットする](#git-reset---head-を指定した状態にリセットする)
  - [git revert - 逆コミットを生成する](#git-revert---逆コミットを生成する)
- [コンフィグ](#コンフィグ)
  - [git config](#git-config)
  - [.gitattributes -](#gitattributes--)
  - [.gitignore -](#gitignore--)
- [その他のコマンド](#その他のコマンド)

Git コマンドリファレンス

# 対象バージョン: Git 2.43

# 用語

- `$GIT_DIR`
  - `.git`ディレクトリのこと。リポジトリ毎に作られる Git のシステムディレクトリ。コンフィグで変更可能。
- `HEAD`
- detached `HEAD`
- local branch (ローカルブランチ)
- upstream branch (上流ブランチ)

### remote-tracking branch (追跡ブランチ)

remote-tracking branch（リモート追跡ブランチ）、あるいは単に tracking branch（追跡ブランチ）。

### pathspec

ファイルパス。
形式は以下

> https://git-scm.com/docs/gitglossary#Documentation/gitglossary.txt-aiddefpathspecapathspec

### ref, refs

object name または他の ref を指し示す、`refs/`で始まる名前。（例：`regs/heads/master`）ブランチまたはタグ。`refs/`で始まらない特殊な ref もある（`HEAD`など）。

- `FETCH_HEAD`
  - リモートの各ブランチの先端が記録される。

### refspec

- リモートの ref とローカルの ref の対応関係を指定する文字列。`git fetch` (`git pull`), `git push`で使用。
- ```
  [+]<src>[:<dst>]
  ```
- `<src>`, `<dst>`は ref
- ワイルドカード`*`
- `^`で除外指定
- 例：.git/config
  ```
  fetch = +refs/heads/*:refs/remotes/origin/*
  ```
  - 左側はリモートにおける ref 名なので`heads`、右側はローカルにおける ref 名なので`remotes/`であることに注意。

### tree-ish

- ツリーオブジェクトそのもの、あるいは、辿っていくとツリーオブジェクトにたどり着く参照。
- 以下が tree-ish である。
  - commit-ish
  - tree object
  - tree object を指す tag object
  - tree object を指す tag object を指す tag object

# リポジトリ

## git init - リポジトリを初期化する

```sh
git init [<options>] [<directory>]
```

- `--bare`
  - bare directory（作業ツリーのないリポジトリ）を作成する。
- `--template=<directory>`
  - テンプレートディレクトリを指定する。
- `--separate-git-dir=<git-dir>`
  - `$GIT_DIR`を指定されたパスに作る。ディレクトリ内の.git には`$GIT_DIR` の場所が書かれたファイルが生成される。
- `-b <branch-name> | --initial-branch=<branch-name>`
  - イニシャルブランチ名を指定する。→`init.defaultBranch`

## git clone - リポジトリを複製する

```sh
git clone [<options>] [--] <repository> [<directory>]
```

- `<repository>`
  - クローン元。形式は以下。

|             |     |
| ----------- | --- |
| SSH         |     |
| GIT         |     |
| HTTP(S)     |     |
| FTP(S)      |     |
| SSH(scp 風) |     |

- `<directory>`
  - クローン先。既存ディレクトリの場合は空のディレクトリのみ可。
- `--bare`
  - ベアリポジトリを作成する
- `--mirror`
  - ソースリポジトリのミラーを作成する。--bare がローカルブランチしか複製しないのに対し、--mirror はリモートブランチもコピーする。
- `(-o | --origin) <name>`
  - origin 以外のリモート名を使う。
- `(-b | --branch) <name>`
  - ブランチの指定（＝チェックアウトされるブランチ）
- `--recurse-submodules[=<pathspec>]`
  - サブモジュールも再帰的にクローンする

参考

- [大きな Git リポジトリをクローンするときの工夫を図解します - DeNA Testing Blog](https://swet.dena.com/entry/2021/07/12/120000)

# ローカル

## git add - ファイルをインデックスに追加する

```sh
git add [<options>] [--] [<pathspec>…]
```

- `-i | --interactive`
  - インタラクティブに追加作業を行うモード
- `-p | --patch`
  - 追加する変更箇所をインタラクティブに選択する。
- `-e | --edit`
  - 差分エディタを開いて編集する
- `-f | --force`
  - .gitignore 対象ファイルを強制的に追加する
- `-u | --update`
  - `<pathspec>`がインデックスにすでに追加されているならそれを更新する。追加されていないパスは追加しない。`<pathspec>`が指定されていない場合、git 追跡下にあるすべてのファイルを更新する
- `-A | --all | --no-ignore-removal`
  - `<pathspec>`にマッチするファイルを更新するのに加えて、インデックスにすでに追加されているものも更新する。`-A`で`<pathspec>`が指定されていない場合はすべてのファイルを更新する。
- `--no-all | --ignore-removal`
  - インデックスに新しいファイルと修正されているファイルを追加するが、作業ツリーで削除されたファイルは無視する。`<pathspec>`が指定されていない場合は何もしない。
- `-N | --intent-to-add`
  - 空のエントリをインデックスに追加する。後で add する予定であることをマークするのに使う。
- `--refresh`
  - 情報を更新する。追加はしない。
- `--ignore-errors`
  - 追加するファイルの一部でエラーが起きても正常なファイルはそのまま追加する。
- `--no-warn-embedded-repo`
  - サブモジュールがある場合に、埋め込まれているリポジトリを`git submodule add`を使わずに追加しようとしたときの警告を無視する
- `--renormalize`
  - すべての追跡下ファイルを再度追加する。CRLF の正規化などに使う
- `--pathspec-from-file=<file>`
  - `<pathspec>`をファイルから読む

## git rm -ファイルをインデックスと作業ツリーから除外する

```sh
git rm [--] [<pathspec>…]
```

- `<pathspec>`
  - 除外するファイル。
- `-r`
  - ディレクトリ名が与えられた場合、再帰的に除外する
- `--cached`
  - インデックスからのみ除外する
- `--ignore-unmatch`
  - ファイルにマッチしなくてもエラーを出さない
- `--pathspec-from-file=<file>`
  - （略）

## git commit - インデックスをコミットする

```sh
git commit [<options>] [--] [<pathspec>…]
```

### 全般

- `-a | --all`
  - 変更のあるファイルと削除されたファイルを自動的にステージする
- `--amend`
  - カレントブランチの先端を新しいコミットで置き換える
- `-p | --patch`
  - インタラクティブ
- `--author=<author>`
  - author を上書きする。形式は`A U Thor<author@example.com>`
  - この形式に従わない場合、既存のコミットからその author を検索する。
- `--date=<date>`
  - 日付を上書きする
- `--reset-author`
  - `-C`などで再コミットする際に author を自分にする
- `--branch`
  - ブランチと追跡情報を表示する
- `-n | --no-verify`
  - pre-commit フックと commit-msg フックを飛ばす。
- `-u[<mode>] | --untracked-files[=<mode>]`
  - 追跡外ファイルを表示する。mode は`no`（表示しない）、`normal`（ファイルとディレクトリ）、`all`（ディレクトリの中のファイルも表示する）で、デフォルトは`all`。このオプションを指定しない場合のデフォルトは`normal`。
- `--fixup=[(amend|reword):]<commit>`
  - （rebase に関係あるらしいが不明）
- `--allow-empty`
  - 空コミットを許可する
- `-i | --include`
  - コミットを作る前に、コマンドラインで指定したパスをステージする。衝突したマージを解消する場合に使う
- `-o | --only`
  - 作業ツリーの指定したパスのファイルからコミットを作る。これはコマンドラインにパスが指定されたときの`git commit`の既定の挙動で、`-o`は必ずしも必要ない。
- `--pathspec-from-file=<file>`
  - （略）
- `<pathspec>`
  - 指定したファイルを、すでにインデックスにある変更を無視してコミットし、同時にインデックスにも追加する

### コミットメッセージ関連

- `-C <commit> | --reuse-message=<commit>`
  - コミットメッセージを再利用する
- `-c <commit> | --reedit-message=<commit>`
  - `-C` と同様だが、エディタを開いて編集できる
- `--squash=<commit>`
  - `rebase --autosquash`用のコミットメッセージを作る（→？）
- `-F <file> | --file=<file>`
  - コミットメッセージをファイルから読む
- `-m <msg> | --message=<msg>`
  - コミットメッセージ。複数指定すると別々の段落として結合する
- `-t <file> | --template=<file>`
  - コミットメッセージのテンプレートをファイルから読む。(→`commit.template`)
- `--allow-empty-message`
  - 空のコミットメッセージを許可する
- `-s | --signoff`
  - 署名を追加する？
- `--trailer <token>[(=|:)<value>]`
  - `<token>`と`<value>`からなる後書きを追加する。
- `--cleanup=<mode>`
  - コミットメッセージの整形モード。
    - `strip`
      - 不要な空行・空白およびコメントを削除する
    - `whitespace`
      - コメントを削除しない以外は`strip`と同じ
    - `verbatim`
      - 何も整形しない
    - `scissors`
      - メッセージが編集されている場合は、以下の行から下の行を削除する。それ以外は`whitespace`と同じ。
      - `# ------------------------ >8 ------------------------`
    - `default`
      - メッセージが編集されている場合は、`strip`と同じ。それ以外は`whitespace`と同じ。
- `-e | --edit`
  - `-F`や`-m`や`-C`で受け取ったメッセージを編集する
- `--no-edit`
  - メッセージを編集しない（`--amend`などのときに使う）
- `--status`
  - コミットメッセージに`git status`を含める。

## git diff - 差分を取る

### 作業ツリー

1. ```sh
   git diff [--] [<path>…]
   ```

   インデックスと作業ツリーの差分（＝`git add`対象）を取る。

2. ```sh
   git diff --no-index [--] <path> <path>
   ```

   ファイルシステム上の 2 ファイルの差分を取る。ファイルのどちらかが作業ツリー外のファイルである場合は`--no-index`は省略可。

3. ```sh
   git diff [--merge-base] <commit> [--] [<path>…]
   ```
   コミットと作業ツリーの差分を取る。
   - `--merge-base`
     - `<commit>`ではなく、「`<commit>`と HEAD の merge base（マージ起点）」との差分を取る。\
       `git diff $(git merge-base <commit> HEAD)`

### --cached

```sh
git diff --cached [--merge-base] [<commit>] [--] [<path>…]
```

コミットとインデックスの差分を取る。`<commit>`のデフォルトは HEAD。

- `--staged`と`--cached`は同じ。

### コミット間

1. ```sh
   git diff [--merge-base] <commit> <commit> [--] [<path>…]
   git diff [--merge-base] <commit>..<commit> [--] [<path>…]
   ```

   任意の 2 コミット間の差分を取る。`..`は有ってもなくても変わらない。`--merge-base`は、前者の`<commit>`として 2 コミットのマージベースを使う。`..`ありの形式ではコミットの片方を省略でき、その場合は HEAD が代わりに使われる。

2. ```sh
   git diff <commit> [<commit>…] <commit> [--] [<path>…]
   ```

   マージコミットの結果を見る。`<commit>`の 1 つ目はマージコミット、2 つ目以降はその親コミットでなければならない。

3. ```sh
   git diff <commit>...<commit> [--] [<path>…]
   ```
   2 つのコミットの共通祖先であるコミットを開始地点として、2 番目のコミットに到達するまでの差分を取る。コミットの片方は省略可能。\
   `git diff $(git merge-base <commit1> <commit2>) <commit2>`

## git status -

```sh
git
```

- `-`

## git log - コミットログを見る

```sh
git
```

- `-`

## git restore - ファイルの復元

```sh
git restore [--source=<tree>] [--staged] [--worktree] [--] <pathspec>…
```

作業ツリーまたはインデックスの指定されたパスにマッチするファイルを、復元ソースのコンテンツで復元する。復元ソースに存在しない場合は削除される。

- `<pathspec>`
  - restore される対象を制限する。
- `-s <tree> | --source=<tree>`
  - 復元元のツリー。省略した場合、`--staged`が指定されている場合は`HEAD`、指定されていなければインデックスが使われる。
- `-S | --staged`, `-W | --worktree`
  - それぞれインデックス、作業ツリーを復元する。併用可。どちらも指定されていない場合は作業ツリーを復元する。
- `--recurse-submodules`
  - 作業ツリーを復元する場合で pathspec がサブモジュールを指定している場合、サブモジュールはこのオプションを指定した場合のみ更新される。またこのとき、サブモジュールは親プロジェクトのコミットで復元される。
- `--overlay`
  - 復元時にファイルの削除を行わない。

## git stash - 一時的な退避

```sh
git stash list
git stash show
git stash drop
git stash pop
git stash apply
git stash branch
git stash save (deprecated)
git stash clear
git stash create
git stash store
```

- `-`

## git worktree -

```sh
git worktree
```

- `-`

# ブランチ

## git branch - ブランチの一覧・作成・削除

### ブランチを作成する

```sh
git branch <branchname> [<start-point>]
```

作成するだけで切り替えはしない。切り替えもする場合は`git switch -c`。

リモート追跡ブランチから新しいブランチを作成した場合、`branch.<name>.remote`や`branch.<name>.merge`が自動的に設定される。

- `<branchname>`
  - ブランチ名。
- `<start-point>`
  - 新しいブランチの`HEAD`の参照先、つまりブランチの開始地点となるコミット。デフォルトは現在の`HEAD`。
- `-f | --force`
  - 既にその名前のブランチが存在するなら上書きする。
- `-t | --track[=direct|inherit]`
  - 上流ブランチを設定する。
    - `direct`（デフォルト）
      - `<start-point>`に使用したブランチを上流ブランチとして設定する。`-t`はこの設定。
    - `inherit`
      - `<start-point>`に指定したブランチの上流ブランチ設定を継承する。
    - `--track`と`--no-track`のどちらもない場合の挙動は`branch.autoSetupMerge`を参照。
- `--no-track`
  - 上流ブランチを設定しない

### ブランチの一覧

```sh
git branch
git branch --list [<pattern>…]
```

現在のブランチは色付きで表示される。

- `<pattern>`
  - ブランチ名を指定する。複数指定、ワイルドカード可。指定する場合は`--list`を指定しないとブランチ作成として解釈されるので注意。
- `-r | --remotes`
  - リモート追跡ブランチを表示する。
- `-a | --all`
  - リモート追跡ブランチとローカルブランチの両方を表示する。
- `--contains [<commit>]`, `--no-contains [<commit>]`
  - 指定したコミットを含む（含まない）ブランチのみ表示する。`<commit>`のデフォルトは`HEAD`。
- `--merged`
- `--show-current`
  - カレントブランチの名前を表示する。

### 上流ブランチを設定する

```sh
git branch (--set-upstream-to=<upstream> | -u <upstream>) [<branchname>]
```

`<upstream>`を`<branchname>`の上流ブランチに設定する。`<branchname>`のデフォルトは`HEAD`。

### ブランチをリネーム/コピー/削除する

```sh
git branch (-m | -M) [<oldbranch>] <newbranch>
git branch (-c | -C) [<oldbranch>] <newbranch>
git branch (-d | -D) [-r] <branchname>
```

- `-m | --move`
  - ブランチを移動（リネーム）する。コンフィグや reflog も移動する。
- `-M`
  - `--move --force`の短縮
- `-c | --copy`
  - ブランチをコピーする。コンフィグや reflog もコピーする。
- `-C`
  - `--copy --force`の短縮
- `-d | --delete`
  - ブランチを削除する。
- `-D`
  - `--delete --force`の短縮

## git show-branch - ブランチの分岐状況を見る

```sh
git
```

- `-`

## git checkout - インデックスと作業ツリーを指定した版にする

作業ツリーのファイルを更新して、インデックスまたは指定したツリーの版に合わせる。`<pathspec>`を指定しなかった場合、`HEAD`も変更してカレントブランチを変更する。

### ブランチの切り替え

```sh
git checkout [<branch>]
```

インデックスと作業ツリーを`<branch>`の版に変更し、`HEAD`も`<branch>`に変更する。

- `<branch>`
  - チェックアウトするブランチ。
- `--guess`
  - `<branch>`が存在しないが、名前のマッチする追跡ブランチが単一のリモートにのみ存在するなら、その追跡ブランチを上流ブランチとするブランチを自動的に作成して切り替える。これはデフォルトの挙動である。 \
    `git checkout -b <branch> --track <remote>/<branch>`
- `-f | --force`
  - インデックスや作業ツリーの内容に`HEAD`と差異があっても、ディレクトリに未追跡ファイルがあっても、無視して切り替える。それらの変更は破棄される。
- `-m | --merge`
  - 現在のブランチと切り替え先ブランチで異なるファイルに、ローカルな変更が加えられている場合、デフォルトではコマンドが拒否されるが、拒否せずに 3way マージする。インデックスの変更は破棄される。

### ブランチの作成

```sh
git checkout (-b|-B) <new-branch> [<start-point>]
```

- `-b`
  - 新しいブランチを作成してチェックアウトする。
- `-B`
  - 既に存在しても強制的に作成する。
- `<start-point>`
  - 新しいブランチを作成するコミット位置

### detached HEAD

```sh
git checkout [--detach] <commit>
git checkout --detach [<branch>]
```

指定のコミットをチェックアウトし、HEAD を detached にする。`<commit>`がブランチの場合は`--detached`を指定すれば detached HEAD になる。作業ツリーにある変更は維持され、チェックアウトしたものに結合される。

### インデックスからチェックアウト (git restore)

```sh
git checkout [<tree-ish>] [--] <pathspec>…
```

指定パスのファイルを上書きする。

- `<tree-ish>`
  - チェックアウト元。通常はコミットを指定する。
  - 省略された場合はインデックスの内容を作業ツリーにチェックアウトする。
  - 与えられた場合は、インデックスと作業ツリー両方に`<tree-ish>`の内容をチェックアウトする。
- `--ours`, `--theirs`
  - 未マージのファイルを含むインデックスからチェックアウトするときに、どの側面の内容をチェックアウトするかを指定する。
- `--merge`
  - インデックスの未マージファイルをチェックアウトするときに、競合状態のマージを再作成する。
- `--no-overlay`
  - `<tree-ish>`に存在しないファイルを削除する。デフォルトでは削除しない（`--overlay`）。

## git switch - ブランチの切り替え

```sh
git switch <branch>
```

ブランチを切り替える。

- `<branch>`
  - 切り替え先ブランチ。
- `--guess`
  - `<branch>`が存在しないが、名前のマッチする追跡ブランチが単一のリモートにのみ存在するなら、その追跡ブランチを上流ブランチとするブランチを自動的に作成して切り替える。これはデフォルトの挙動である。 \
    `$ git switch -c <branch> --track <remote>/<branch>`
- `-f | --force`
  - 現在のブランチと切り替え先ブランチで異なるファイルに、ローカルな変更が加えられている場合、デフォルトではコマンドが拒否されるが、拒否せずに 3way マージする。

```sh
git switch (-c|-C) <new-branch> [<start-point>]
```

- `(-c | --create) <new-branch>`
  - ブランチ`<new-branch>`を`<start-point>`に作成して切り替える。
- `(-C | --force-create) <new-branch>`
  - ブランチ`<new-branch>`が既に存在する場合、`<start-point>`に再作成して切り替える。
- `<new-branch>`
  - 新しいブランチの名前。
- `<start-point>`
  - 新しいブランチの開始点。

```sh
git switch --detach [<start-point>]
```

detached HEAD に切り替える。

## git merge - ブランチのマージ

```sh
git
```

- `-`

# リモートリポジトリ

## git remote - リモートリポジトリ情報の操作

### git remote

```sh
git remote
```

リモートリポジトリの一覧を表示する。

### git remote add

```sh
git remote add <name> <URL>
```

リモートを追加する。

### git remote rename

```sh
git remote rename <old> <new>
```

リネームする。

### git remote remove

```sh
git remote remove <name>
```

削除する。

### git remote set-head

```sh
git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
```

リモートのデフォルトブランチを設定または削除する。デフォルトブランチを設定すると、ブランチ名を指定するところでリモート名を代わりに使用できる。

### git remote set-branches

```sh
git remote set-branches <name> <branch>…
```

リモート名によって追跡されるブランチを変更する。

### git remote get-url

```sh
git remote get-url <name>
```

リモートの URL を得る。

### git remote set-url

```sh
git remote set-url <name> <newurl> [<oldurl>]
git remote set-url --add <name> <newurl>
git remote set-url --delete <name> <URL>
```

リモートの URL を変更する。

### git remote show

```sh
git remote show <name>…
```

リモートの情報を表示する。

### git remote prune

```sh
git remote prune <name>…
```

`<name>`というリモートの古いリモート追跡ブランチを削除する。

### git remote update

```sh
git remote update [(<group> | <remote>)…]
```

更新をフェッチする。

## git fetch - 他のリポジトリから object や refs をダウンロードする

```sh
git fetch [<repository> [<refspec>…]]
git fetch <group>
git fetch --multiple [<options>] [(<repository> | <group>)…]
git fetch --all
```

refs（＝ブランチやタグ）およびそれらの履歴に必要なオブジェクトを他のリポジトリからフェッチし、リモート追跡ブランチを更新する。

リモートリポジトリを指定しなかった場合は、カレントブランチに上流ブランチが設定されていないかぎり、`origin`という名前のリモートからフェッチする。

デフォルトではタグはフェッチ対象となっている履歴を指しているもののみフェッチされる。すべてフェッチするには`--tags`を使う。

- `--all`
  - すべてのリモートをフェッチする
- `-a | --append`
  - フェッチした ref 名や object 名を、`FETCH_HEAD`に上書きするのではなく追加する
- `--atomic`
  - ローカル ref の更新をアトミックに行う。つまり、すべて更新されるか、1 つも更新しないかである。
- `--depth=<depth>`
  - フェッチするコミットの数を、リモートの各ブランチ先端から特定の個数までに制限する
- `--multiple`
  - 複数のリモートからフェッチする
- `-p | --prune`
  - フェッチする前に、すでにリモートに存在していないリモート追跡参照を削除する
- `-P | --prune-tags`
  - フェッチする前に、すでにリモートに存在していないローカルタグを削除する（`--prune`時のみ？）
- `--refetch`
  - すべて再フェッチする
- `--refmap=<refspec>`
  - `remote.*.fetch`の refspec ではなく指定した`<refspec>`を使ってフェッチする。空の refspec を指定すると、remote に構成されている refspec を無視して、コマンドラインで指定された refspec のみを使用する。
- `-t | --tags`
  - すべてのタグをフェッチする。
- `--recurse-submodules[=(yes|on-demand|no)]`
  - サブモジュールのフェッチを制御する。
    - `yes`
      - すべてフェッチする
    - `on-demand`
      - 変更されたサブモジュールのみフェッチする
    - `no`
      - しない
- `--recurse-submodules-default=[yes|on-demand]`
- `--set-upstream`
  - フェッチが正常に行われたら、上流への追跡参照を追加する。（引数なしの pull などで使われるもの）
- `<repository>`
  - フェッチ元になるリモートリポジトリ。URL またはリモート名。
- `<group>`
  - フェッチするグループ。グループは config で定義する。
- `<refspec>`
  - refspec。指定しない場合は`remote.<repository>.fetch`から読む。

## git pull -

```sh
git
```

- `-`

## git push - リモートの参照を更新する

```sh
git [<options>] [<repository> [<refspec>…]]
```

- `<repository>`
  - プッシュ先のリモートリポジトリ。URL またはリモート名。指定しなかった場合はカレントブランチの`branch.*.remote`を使う。それもないなら`origin`。
- `<refspec>`
  - refspec。左がローカル、右がリモート。指定しなかった場合（`--all`や`--mirror`, `--tags`もない）は`remote.*.push`を使う。それもないなら`push.default`。
- `--all | --branches`
  - すべてのブランチをプッシュする。
- `--prune`
  - 対応するローカルブランチのないリモートブランチを削除する。
- `--mirror`
  - すべての refs（`refs/`以下すべて）をリモートに対してミラーリングする。新規追加された ref は追加され、削除された ref は削除される。
- `-d | --delete`
  - 指定された refs をリモートリポジトリから削除する。
- `--tags`
  - すべてのタグをプッシュする。
- `-f | --force`
  - 通常はリモートの refs のうちローカルの ref の祖先でないものを更新することは拒否されるが、このチェックを無効化する。
- `--force-if-includes`
  - リモート追跡 ref の先端がローカルに組み込まれている場合のみ更新を強制する。
- `-u | --set-upstream`
  - プッシュ成功したブランチ（あるいはすでに最新であるブランチ）のそれぞれについて、upstream (tracking) reference を追加する。
- `--recurse-submodules=(check|on-demand|only|no)`

# コミットの操作

## git rebase - ブランチの根本を付け替える

```sh
git
```

- `-`

## git reset - HEAD を指定した状態にリセットする

restore がファイルを復元するだけなのに対し、reset は HEAD も変わる。そのため、reset 後にコミットするとそこより先にあった既存のコミットはなくなる場合がある

```sh
git reset [<tree-ish>] [--] <pathspec>…
```

`<pathspec>`にマッチするインデックスの項目を`<tree-ish>`の状態にリセットする。`<tree-ish>`のデフォルトは`HEAD`。

- 作業ツリーやカレントブランチには影響しない。
- `git reset <pathspec>` は `git restore [--source=<tree-ish>] --staged <pathspec>…`と同じで、 `git add <pathspec>` の逆である。

```sh
git reset [ --soft | --mixed [-N] | --hard | --merge | --keep ] [<commit>]
```

`HEAD`を`<commit>`にセットする。オプションでインデックスや作業ツリーも変更する。`<commit>`のデフォルトは`HEAD`。

- `--soft`
  - HEAD のみ reset する
- `--mixed` （デフォルト）
  - HEAD とインデックスを reset する。
- `--hard`
  - HEAD とインデックスと作業ツリーを reset する。作業ツリーの変更は失われる
- `--merge`
  - --hard と同じように HEAD、インデックス、作業ツリーを reset するが、作業ツリー内でまだステージしていない変更があるファイルは維持する。`<commit>`とインデックスで異なるファイルに未ステージの変更がある場合は中断する。
- `--keep`
  - --hard と同じように HEAD、インデックス、作業ツリーを reset するが、作業ツリーのファイルがローカルな変更を持っている場合は中断する。
- `<commit>`
  - 対象コミット。デフォルトは`HEAD`

## git revert - 逆コミットを生成する

```sh
git
```

- `-`

# コンフィグ

## git config

```sh
git config <name> [<value> [<value-pattern>]]
git config --add <name> <value>
git config --replace-all <name> <value> [<value-pattern>]
git config --get <name> [<value-pattern>]
git config --get-all <name> [<value-pattern>]
git config --get-regexp <name-regex> [<value-pattern>]
git config --get-urlmatch <name> <URL>
git config --unset <name> [<value-pattern>]
git config --unset-all <name> [<value-pattern>]
git config --rename-section <old-name> <new-name>
git config --remove-section <name>
git config (-l | --list)
git config (-e | --edit)
```

- `--add`
  - 新しい行を追加する。
- `--replace-all`
  - マッチするすべての行を置換する。
- `--get`
  - 値を返す。
- `--get-all`
  - 複数の値を持つキーの場合、すべての値を返す。
- `--get-regexp`
  - `--get-all`と同じだが、name を正規表現として解釈する。
- `--get-urlmatch`
  - `<name>`を`<section>.<key>`の形式で与えると、`<section>.<URL>.<key>`のうち URL が最もよくマッチするものの値を返す。
- `--unset`
  - マッチする行を削除する。
- `--unset-all`
  - マッチするすべての行を削除する。
- `--rename-section`
  - セクションをリネームする。
- `--remove-section`
  - セクションを削除する。
- `-l | --list`
  - すべての変数の一覧を表示する。
- `-e | --edit`
  - エディタを開いて編集する。
- `--system`
  - システム全体の設定。`/etc/gitconfig`
- `--global`
  - グローバル設定。`~/.gitconfig`
- `--local`
  - リポジトリ固有の設定。`.git/config`
- `--worktree`
  - `--local`と同じだが、`extension.worktreeConfig`が有効の場合は`$GIT_DIR/config.worktree`。

## .gitattributes -

## .gitignore -

# その他のコマンド

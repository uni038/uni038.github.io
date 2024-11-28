# `re`

正規表現。

- `re.compile()` 正規表現文字列を正規表現オブジェクトにコンパイルする
- `re.search()` 最初にマッチする箇所のマッチオブジェクトを返す
- `re.match()` 先頭がマッチする場合のみ、マッチオブジェクトを返す
- `re.fullmatch()` 全体がパターン文字列にマッチする場合のみ、マッチオブジェクトを返す
- `re.split()` マッチ箇所で分割した文字列を返す
- `re.findall()` すべてのマッチ文字列のリストを返す。パターンがグループを持つ場合はタプルのリストを返す
- `re.finditer()` マッチオブジェクトを yield するイテレータを返す
- `re.sub()` 一番左でマッチした箇所を置換した文字列を返す
- `re.subn()` 一番左でマッチした箇所を置換した文字列と、置換した数とのタプルを返す
- `re.escape()`
- 正規表現オブジェクト `re.Pattern`
  - `Pattern.search()`
  - `Pattern.match()`
  - `Pattern.fullmatch()`
  - `Pattern.split()`
  - `Pattern.findall()`
  - `Pattern.finditer()`
  - `Pattern.sub()`
  - `Pattern.subn()`
  - `Pattern.flags`
  - `Pattern.groups`
  - `Pattern.pattern` 元のパターン文字列
- マッチオブジェクト `re.Match`
  - `Match.expand()`
  - `Match.group()` マッチグループ
  - `Match.groups()` すべてのマッチグループのタプル
  - `Match.groupdict()` グループの辞書。キーはグループ名
  - `Match.start()`
  - `Match.end()`
  - `Match.span()`
  - `Match.pos()`
  - `Match.endpos()`
  - `Match.lastindex()`
  - `Match.lastgroup()`
  - `Match.re()` マッチに使用した正規表現オブジェクト
  - `Match.string()` 文字列

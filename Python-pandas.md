# データ型

# オブジェクト
## Series

## DataFrame

## Index

# インデクシング
## `.loc[]`
- 形式
  - `.loc[<row-label>]`
  - `.loc[<row-label>, <column-label>]`
  - `.loc[:, <column-label>]`
- 入力値
  - 単一のラベル。文字列か数値。
  - ラベルのリスト
  - ラベルのスライス (`'a':'f'`)
    - pythonの通常のスライスと違い始点と終点を指定する
    - 始点・終点どちらも省略可能
    - `:`ですべて
    - `::-1`
  - 行数または列数と同じ長さのbooleanのリスト
  - alignable boolean series ?
  - alignable index ?
  - 引数を1つ持つ関数。SeriesまたはDataFrameを受け取り、上記いずれかのオブジェクトを返す。

## `.iloc[]`
- 入力値
  - 整数
  - 整数のリスト
  - 整数のスライス
  - booleanのリスト
  - 引数を1つ持つ関数

## `[]` (`__getitem__`)
- Seriesの場合はインデックス、DataFrameの場合はラベルを指定して取り出す
- 配列も可
- スライスも可。DataFrameの場合、行のスライスになる

## 属性アクセス (`.`)
- Seriesはインデックス名、DataFrameはラベル名で直接アクセスできる
- 既に存在するラベルのみ可。新しいインデックス・ラベルは作れない
- python識別子として有効な名前のみ可
- メソッド名と重複していると使えない

## `s[ s > 0 ]`

# 属性
## Attributes
|Index|Series|DataFrame||
|-|-|-|-|
|-|`index`|`index`|インデックス|
|-|-|`axes`|軸のリスト|
|-|-|`columns`|列ラベル|
|`values`|`values`|`values`|値|
|-|`array`|-|値の保存されたExtensionArray|
|`dtype`|`dtype`|-|データ型|
|-|`dtypes`|`dtypes`|データ型|
|`shape`|`shape`|`shape`|形|
|`nbytes`|`nbytes`|-|バイト数|
|`ndim`|`ndim`|`ndim`|次元数|
|`size`|`size`|`size`|要素数|
|`T`|`T`|-|行列反転|
|`memory_usage()`|`memory_usage()`|`memory_usage()`|メモリ使用量|
|`hasnans`|`hasnans`|-|NaNがあるかどうか|
|`empty`|`empty`|`empty`|空であるかどうか|
|`name`|`name`|-|名前|
|`names`|-|-||
|-|`flags`|-||
|-|`set_flags()`|`set_flags()`||
|-|-|`info()`||
|-|-|`select_dtypes()`||

- Indexのみ
  - is_monotonic_increasing
  - is_monotonic_desreasing
  - is_unique
  - has_duplicates
  - inferred_type


## Conversion
||Series|DataFrame|
|-|-|-|
|`astype`|||
|`convert_dtypes`|||
|`infer_objects`|||
|`copy`|||
|`bool`|||
|`to_numpy`|||
|`to_period`|||
|`to_timestamp`|||
|`to_list`|||
|`__array__`|||

## Indexing, Iteration
||Series|DataFrame|
|-|-|-|
|`get`|||
|`at`|||
|`iat`|||
|`loc`|||
|`iloc`|||
|`__iter__`|||
|`items`|||
|`keys`|||
|`pop`|||
|`item`|||
|`xs`|||

## Binary Operator
|あとで

## Function Application, Groupby & Window
||Series|DataFrame|
|-|-|-|
|`apply`|||
|`agg`|||
|`aggregate`|||
|`transform`|||
|`map`|||
|`groupby`|||
|`rolling`|||
|`ewmexpanding`|||
|`pipe`|||

## Computations / descriptive stats
||Series|DataFrame|
|-|-|-|
|`abs`|||
|`all`|||
|`any`|||
|`autocorr`|||
|`between`|||
|`clip`|||
|`corr`|||
|`count`|||
|`cov`|||
|`cummax`|||
|`cummin`|||
|`cumprod`|||
|`cumsum`|||
|`describe`|||
|`diff`|||
|`factorize`|||
|`kurt`|||
|`max`|||
|`mean`|||
|`median`|||
|`min`|||
|`mode`|||
|`nlargest`|||
|`nsmallest`|||
|`pct_change`|||
|`prod`|||
|`quantile`|||
|`rank`|||
|`sem`|||
|`skew`|||
|`std`|||
|`sum`|||
|`var`|||
|`kurtosis`|||
|`unique`|||
|`nunique`|||
|`is_unique`|||
|`is_monotonic_increasing`|||
|`is_monotonic_decreasing`|||
|`value_counts`|||

## Reindexing / Selection / Label Manipulation
||Series|DataFrame|
|-|-|-|
|`align`|||
|`case_when`|||
|`drop`|||
|`droplevel`|||
|`drop_duplicates`|||
|`duplicated`|||
|`equals`|||
|`first`|||
|`head`|||
|`idxmax`|||
|`idxmin`|||
|`isin`|||
|`last`|||
|`reindex`|||
|`reindex_like`|||
|`rename`|||
|`rename_axis`|||
|`reset_index`|||
|`sample`|||
|`set_axis`|||
|`take`|||
|`tail`|||
|`truncate`|||
|`where`|||
|`mask`|||
|`add_prefix`|||
|`add_suffix`|||
|`filter`|||

## Missing Data Handling
||Series|DataFrame|
|-|-|-|
|`backfill`|||
|`bfill`|||
|`dropna`|||
|`ffill`|||
|`fillna`|||
|`interpolate`|||
|`isna`|||
|`isnull`|||
|`notna`|||
|`notnull`|||
|`pad`|||
|`replace`|||

## Reshaping
||Series|DataFrame|
|-|-|-|
|`argsort`|||
|`argmin`|||
|`argmax`|||
|`reorder_levels`|||
|`sort_values`|||
|`sort_index`|||
|`swaplevel`|||
|`unstack`|||
|`explode`|||
|`searchsorted`|||
|`ravel`|||
|`repeat`|||
|`squeeze`|||
|`view`|||

## Combining / Comparing / Joining / Merging
||Series|DataFrame|
|-|-|-|
|`compare`|||
|`update`|||

## Time Series Related
あとで

## Accessors
||Series|DataFrame|
|-|-|-|
|`Series.str`|||
|`Series.cat`|||
|`Series.dt`|||
|`Series.sparse`|||
|`DataFrame.sparse`|||
|`Index.str`|||
|``|||
|``|||
|``|||

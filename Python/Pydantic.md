# Pydantic
> https://docs.pydantic.dev/latest/

```sh
pip install pydantic
```

- BaseModel
  - `model_validate()` : オブジェクトのバリデート
  - `model_validate_json()` : JSONのバリデート
  - `model_construct()` : バリデーションなしにモデルを生成
  - `model_dump()` : 辞書表現を返す
  - `model_dump_json()` : JSON表現を返す
  - `model_copy()` : コピーを返す
  - `model_json_schema()` : モデルのJSONスキーマを表す辞書を返す
  - `model_fields` : フィールド名とその定義
  - `model_computed_fields` : 計算されたフィールド名とその定義
  - `model_extra` : バリデーション時の追加フィールド？
  - `model_fields_set` : モデル初期化時に明示的に指定されたフィールドのセット
  - `model_parametrized_name()` : 
  - `model_post_init()` : 
  - `model_rebuild()` : 


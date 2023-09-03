# データベースと SQL

## 導入

### なぜ DB である必要があるのか

- エクセルなどではだめなのか
- エクセルなどは以下を支える仕組みがない
  - 複数人による同時編集
  - 大量のデータ
  - 自動化
  - 万が一の対応

### データベースの種類

- リレーショナル
- 階層型
- NoSQL
- ネットワーク
- 時系列データベース
- キーバリュー型
  - シンプルな辞書型で、パフォーマンスが良いので Google の検索などに使われている

## SQL

- DBMS によって差異はあるが、標準的な記法が ISO によって定義されている
- 標準 SQL に含まれない例えばテーブル名の定義などは`EXEC`を先頭につける?

### SQL 文と種類

- DDL(Data Definition Language)
  - データベースやテーブルを作成/削除する

```SQL
CREATE
DROP
ALTER
```

- DML(Sata Manipulation Language)
  - テーブルの行を検索/変更する

```SQL
SELECT
INSERT
UPDATE
```

- DCL(Data Control Language)
  - データベースに対して行った変更を確定/取り消す
  - 権限の設定を行う

```SQL
COMMIT
ROLLBACK
GRANT
REVOKE
```

#### 型

- CHAR
  - 固定長
  - CHAR(10)だったら 10 byte
  - 満たない場合は半角スペースで埋める
- VARCHAR
  - 可変長
  - VARCHAR(10)だったら最大 10 byte
  - 満たない場合はその分だけメモリが確保される
  - ページングの都合上 8000byte まで、それを超える場合は`max`を指定する(メモリの扱い方が変わる)
  - Shift_JS(全角 2byte、半角 1byte)
    - nvarchar は unicode(全角半角 2byte)
      - nvarchar(10)は 10 文字まで
      - なのでこちらは最大 4000byte まで

### 句

- 別名

```SQL
select shohin_id as id
from Shohin
```

## 比較演算子

- NULL を抽出したい場合は`IS NULL`
  - 通常の演算に`NULL`を含めると真偽値が`UNKNOWN`になって出力されない
- NOT EQUAL を表す`!=`は実は標準 SQL ではない
  - `<>`を使うらしい

### 関数

#### 集合関数

- `COUNT`、`AVE`、`SUM`など、結果を集合する関数

  - `COUNT`は`NULL`を除外しない

##### `GROUP BY`

- 上記はテーブルの全体に対して行う演算
- `GROUP BY`はグループごとに切り分ける
- `GROUP BY`に指定するキーを集約キーなどという
- 集約キーに`NULL`の要素があると、`NULL`も一つの分類としてまとめられる
- `GROUP BY`を使用する時、`SELECT`できるの以下だけ
  - 定数
  - 集合関数
  - 集約キー
- グループ化後はグループが一つの単位になっている
- そのグループ名が集約キー
- では他のキーを指定した時なにがｄ

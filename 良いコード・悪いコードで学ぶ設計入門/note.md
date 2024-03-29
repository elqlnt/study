# 悪しき構造の弊害を知覚する

- 重複コード
- 修正漏れ
- 可読性低下
- 未初期化状態
- 不整地の混入

# 設計の初歩

- 適切な名前を付ける(リーダブルコード)
- 変数は使い回さない
- 適切な粒度でメソッド化する
  - 同列の関数が同じ粒度であることを意識する

# クラス設計

- 関心の分離
- クラスはそれ単体で正常に動作するようにしないといけない
  - インスタンス変数のバリデーションなど
  - 他のクラスが外部からあれこれ準備してやらないといけないようにはしない
- クラスはそれが機能を完結し、自己防衛機能を持つ必要がある
  - ドライヤーだったら、外部から動かせるのは、オン/オフ/ターボみたいなインターフェースだけがある
    - 不必要に動かせるようにはなっていない
    - 過度な電流を入れると動作を停止するとか
  - データクラスだったら自身でバリデーションを持つとか
    - <input>みたいなイメージ
- データクラスでは計算ロジックをデータ保持側に持たせる

- インスタンス変数が不正状態に陥らないように設計する
- デザインパターン
  - 完全コンストラクタ
    - 不正状態からの防御
  - 値オブジェクト
    - 特定の値に関するロジックを高凝縮にする
  - ストラテジ
    - 条件分岐を削減し、ロジックを単純化する
  - ポリシー
    - 条件分岐を単純化したり、カスタマイズできるようにする
  - ファーストクラスコレクション
    - 値オブジェクトの亜種で、コレクションに関するロジックを高凝縮にする
  - スプラウトクラス
    - 既存のロジックを変更せずに安全に新機能を追加する

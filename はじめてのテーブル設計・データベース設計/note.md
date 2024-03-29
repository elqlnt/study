# データベースとは

- 大量のデータを効率よくアクセスできる仕組み
  - 効率よくアクセスするためのものが DBMS

## そもそもテーブルとは

- 二次元表とテーブルの違いは?
  - カラムという共通点がある表
  - 本来テーブル名はすべて複数形でかけるはず
    - employeesなど

- テーブルの構成要素
  - 行と列
  - キー(特定のデータを引き出すためのもの)
    - 主キー
    - 外部キー

### 制約

- 主キー
  - この値を指定すれば、テーブルの中の要素が一意に定まる
  - テーブルに必ず1つ、かつ1つのみ
    - 複合キー
  - つまり、テーブルに重複行は存在できない
- 外部キー
  - テーブル間のカラムの関連性を設定する
  - テーブル間の整合性を保つ

- 他にもNOT NULL制約など

## データベースの種類

- リレーショナル
- 階層型
- NoSQL
- ネットワーク
- 時系列データベース
- キーバリュー型
  - シンプルな辞書型で、パフォーマンスが良いので Google の検索などに使われている

## データベース設計

- データの持ち方の設計
- システムの拡張性やパフォーマンスに大きな影響を与える

### 3 層スキーマ

- 外部スキーマ
  - ユーザーから見た DB、ビュー
- 概念スキーマ
  - 開発者から見た DB、テーブル
- 内部スキーマ
  - DBMS からみた DB、データの物理的配置

- 外部スキーマと内部スキーマが独立していて、概念スキーマだけがそれぞれを取り合っていると考える

- 論理設計とは概念スキーマの設計
- 物理設計とは内部スキーマの設計
  - DDL による実装ストレージの構成などの設計

- なぜ概念スキーマが必要?
  - データの独立性を確保する
    - 外部スキーマを変更しても内部スキーマを変更する必要がない状態(論理的データ独立性)
      - ビューなど?
    - 内部スキーマを変更しても外部スキーマを変更する必要がない状態(物理的データ独立性)
      - パーティションなど?
  - 内部スキーマを隠蔽する

- つまり、概念スキーマを変更すると、両者に変更が出るので、ここの設計は非常に重要

### 設計の手順

1. エンティティの抽出

- どんなテーブルが必要か

2. エンティティの定義

- どんなカラムか

3. 正規化

- 冗長性をなくす

4. ER図の作成

- 分割されたエンティティの関係性の可視化

#### エンティティの抽出・定義

- どんなデータを管理するか洗い出す
- 実現したいシステムが果たす機能の一連の流れを踏まえて抽出する
- どんなシステムを作るかにかなり依存するので、要件定義と重なるプロセス
- また、データがどのような属性を持つか決める
  - カラム、キー、制約
- 主キーは変更されないもの

#### 正規化

- エンティティの整理(冗長性の排除)
- データの重複が存在していると...
  - データ領域の無駄遣い
  - 更新の手間が増える

- 第5正規形まであるが、業務では第3正規形まででよい
  - ここまでやると自動的に第5まで満たされていることが多い
  - 正規化したテーブルは結合によってもとに戻せる(無損失分解)

- ビジネスルールをすべて見える形にすること

- 動画では第3正規形→第1正規形→第2正規形の順でやっていた
  - 第2正規形は複合キーが存在するときしか考えなくて良いから最後?

##### 第1正規形

- 「1つのフィールドには1つの値しか含まない」

- 複数の値を許すと、主キーが各列の値を一意に定められなくなる(主キーの定義に反する)

- 以下の場合、行と列に分割することが考えられるが、どちらも問題が発生する
  - 行分割の場合:主キーが設定できない
  - 列分割の場合:子供カラムを何個用意すればよいかわからない(NULLが大量発生)

|社員ID|名前|子供|
|:---:|:---:|:---:|
|1|佐藤|太郎、花子|
|2|鈴木||
|3|田中|次郎|

- この解決のために、テーブルを分割する
  - 社員テーブル:社員ID+名前
  - 子供テーブル社員ID+子供

- 第一正規形を満たすには？
  - テーブルのすべての列が、関数従属性を満たす(主キーを入力として各列が一意に決まる/従属する)
    - 関数従属性: y=f(x)において、全単射

##### 第2正規形

- 部分関数従属が解消されていて、完全関数従属のみのテーブルになっている形
  - 部分関数従属:複合キーを構成する一部のカラムに対してのみ従属する
  - 完全関数従属:複合キーに対してのみ従属する

- これは複合キーからなるものだけに発生しうる?
- 部分関数従属が含まれているということは、複数のエンティティが混ざってしまっている状態
  - あるものを変更する時、変更しなければいけないカラムが増える
  - 本当は存在しているはずの情報が、他のカラムに依存してしまっている事によって現れない事がある
- 解消すると、外部キーかつ主キーのカラムができる?
- 重複していたデータが消えることになる

##### 第3正規形

- 推移的関数従属が解消されている形
  - 推移的関数従属:2段階の関数従属がある状態
    - 1つのテーブル内でy=f(x)とz=g(y)が成り立っているような状態
  - こちらも本当は存在しているはずの情報が、他のカラムに依存してしまっている事によって現れない事がある

- テーブルに存在する関数が1つになるように分割すれば良い
- これをやると、主キーからは独立したテーブルができる

##### 演習問題

1 2018-1-1 佐藤 東京 070 封筒 100円
1 2018-1-1 佐藤 東京 070 ボールペン 200円
2 2018-1-1 鈴木 大阪 080 ノート 150円
3 2018-2-1 田中 京都 090 コピー用紙 500円
4 2018-3-1 佐藤 東京 070 消しゴム 50円

第一
注文テーブル
注文ID
1 2018-1-1 佐藤 東京 070
2 2018-1-1 鈴木 大阪 080
3 2018-2-1 田中 京都 090
4 2018-3-1 佐藤 東京 070

注文商品テーブル？
注文ID
1 封筒 100円
1 ボールペン 200円
2 ノート 150円
3 コピー用紙 500円
4 消しゴム 50円

第二
商品テーブル
商品ID
1 封筒 100円
2 ボールペン 200円
3 ノート 150円
4 コピー用紙 500円
5 消しゴム 50円

第三
顧客IS
1 佐藤 東京 070
2 鈴木 大阪 080
3 田中 京都 090

#### ER図

- Entity Relationship

- リレーションの種類
  - 1対1
  - 1対多(0以上?)

- ちゃんと正規化されていればほとんど1対多になるらしい
  - 重複を省くからそうなるか

- 1対1同士のテーブルで外部キーが張れるなら、まとめられるのでは？
  - 読み込み時に不必要なデータを読み込むことにも繋がりそう
  - やっぱり基本的に登場しないらしい(完全に独立したエンティティだけが存在する)

- ER図を描く時、1対多を表現するときは、0以上か、1以上か、2以上かを表現する必要がある
  - そういうケースを想定するか、など業務ロジックに直結する

1. テーブルを描く
2. 主キー属性と非主キー属性を分けて書く

### 実際に論理設計をやってみる

1. 流派はあるけど、UIから想像していく

- 何を実現するシステムか？
- 行為を考える(伝票だったら注文エンティティなど)

2. 5W1Hを通して、中心となるエンティティの周辺のエンティティを見出す
3. UI・仕様書上の項目を、エンティティの属性として入れていく

- もしかしたらエンティティ同士をまとめられるかも

4. 主キーにふさわしい属性があるか？なければIDをふる
5. 外部キーを張る

- エンティティに含めるべき他のテーブルの属性はあるか？

6. 正規形を満たさない場合は任意のタイミングで正規化を行う

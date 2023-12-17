# Dockerについて

- コンテナ型の仮想化プラットフォーム及びツールセット
- アプリケーション、依存関係、実行環境をパッケージングし、実行できるようにする
- 異なる環境やシステムで動かす際の依存関係や設定の問題を解消する

## 従来の仮想化と何が違うか？

- 従来(ホスト型仮想化)
  - ホストOSの上に仮想化ソフト/ハイパーバイザを使用して、仮想マシン/ゲストOSを立ち上げ、そのマシンの中でミドルウェアを構築し、アプリケーションを動かす
- コンテナ型仮想化
  - ゲストOSを起動せずに、ホストOSの上に動作しているDocker Engineからコンテナと呼ばれるミドルウェアの環境構築がされた実行環境を作成し、その中でアプリケーションを動作させる
  - 従来のものより圧倒的に軽量

## 何が嬉しい？

- Githubなどでコードは共有できても、実行環境は人それぞれ
- プログラムの実行環境の管理をするための仕組みとしてDockerがある
  - それを共有するためのDockerHubといったものもある

![全体像](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.amazonaws.com%2F0%2F209909%2F7da0cb86-e305-7fc0-1fe1-d7be4d86ffba.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&w=1400&fit=max&s=55ee7d88a71ceddd42df9d181dc0fa15)

## 用語

- Docker Engine
  - Dockerを利用するための常駐プログラム
- イメージ
  - コンテナの基盤となるファイルシステム、アプリケーションコード、依存関係、設定などが含まれたパッケージ
  - 設計図？
  - タグと紐付けられ、バージョン管理される
    - `nginx:latest`の`latest`のような
- コンテナ
  - イメージの実行可能なインスタンス
  - ホストシステムとは隔離された環境で実行される
  - 各コンテナは自身のファイルシステムとプロセスを持つ
- Dockerfile
  - イメージをビルドするためのスクリプト
  - イメージの構築手順や依存関係の定義が含まれる
- Docker Desktop
  - GUI上でコンテナ稼働状況の確認や、コンテナの停止、再開、廃棄が可能
  - ただし、コンテナ作成などはCLIから行う必要がある

## 実際にやってみる

- Imageを用意する
- 以下で取得しているImageを表示する

```sh
docker images
```

- Imageの準備方法は主に2通り
  - DockerHub

  ```sh
  docker pull イメージ名
  ```
  
  - 自分で作る

  ```dockerfile
  FROM イメージ名:タグ名 #どのimageをもとにimageを作成するか
  RUN パッケージのインストールコマンド #ミドルウェアをインストールするコマンド
  CMD コマンド #コンテナが作成されたあとで実行するコマンドを指定
  ```

  ```sh
  docker build -t ビルド後のイメージ名
  ```

- コンテナを起動する

```sh
docker create --name コンテナ名 イメージ名 #コンテナを作成
docker start コンテナ名
```

- 以下をまとめて`docker run イメージ名`もできる
  - `docker pull`
  - `docker create`
  - `docker start`

- 起動したコンテナ内で扱うデータは、コンテナレイヤーに置くこともできるが以下の理由からホストマシン上で管理し、それをコンテナにマウントする手法が取られる
  - コンテナが削除された時点で、そのデータは消える
  - コンテナ間でデータ共有できない
  - コンテナレイヤーへのデータ書き込みは通常よりも遅い
- ホストマシン上に自動生成されるディレクトリをコンテナにマウントする
  - ボリュームは**Dockerホスト**が管理する

```sh
docker volume create ボリューム名 #ディレクトリのパス
docker run -itd --name 作成するコンテナ名 --mount source=[マウントするvolume名],target=[コンテナ上のマウント先ディレクトリ] イメージ名
```

- `bind mount`では、ホストマシン上の任意のディレクトリをマウントでき、ホスト側で直接操作して良い
  - Dockerエンジンの管轄外
- `tmpfs mounts`はホストマシンのメモリ領域をコンテナ上にマウントする

## 複数コンテナ

### コンテナ間の通信

- APIサーバーコンテナとDBコンテナの通信など
- Bridgeネットワーク
  - 同一ネットワークに存在するコンテナとIPアドレスで通信する
  - DNS定義されていないのでコンテナ名では通信できない
  - `-p`オプションでポート開放ができる(外部からアクセスできる)
- Hostネットワーク
  - docker hostと同じネットワーク設定になる
- Noneネットワーク
  - 接続されたコンテナネットワークインターフェースがなくなる
- 独自ネットワーク
  - コンテナ名でコンテナ間通信を可能にできたりする

![通信](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.amazonaws.com%2F0%2F209909%2Fc29a5550-3907-cc67-dd4e-04ee7fe70fb2.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&w=1400&fit=max&s=7c64468a01f76fe9b22519f4dc113e95)

## Dockerアプリケーションを事前定義して実行する

- コンテナ1つ起動するにしてもコマンドはかなり複雑

```sh
docker run -itd —name mount-test —mount source=volume-test, destination=/etc/nginx,readonly nginx
```

- これを自動化できるのが`Docker Compose`
- 例えば、Webサーバー、DBサーバー、Cacheサーバーなどの定義を1つのdocker-compose.ymlに記述することで、それらをまとめて起動・設定できる

## Docker Machine

- Docker Engineを搭載した仮想マシンの管理をCLIでできるツール
- あるPCの中に仮想マシン(Docker Machine)を作ってその中でコンテナの実行などを行う

## Docker Swarm

- 複数台のDockerホストマシン間での通信設定や管理を自動化する手法
- 以前出てきた「コンテナ間の通信」は同一Dockerホストマシン内のコンテナ同士を扱う
- 例えば、通常Webシステムの本番環境は、単一のマシンではない
- 外部からのリクエストの負荷分散をしたりといった機能を提供する

## コマンド

```sh
docker ps #実行中のコンテナを表示
docker inspect コンテナ名 #コンテナの詳細情報
docker pause コンテナ名 #コンテナの一時停止
docker attach コンテナ名 #起動中のコンテナのシェルへ接続
docker exit コンテナ名 #シェルから抜けるが、-itオプションを付けないとコンテナ自体が終了する
docker volume ls #ボリュームの一覧
docker volume rm ボリューム名 #コンテナを削除してもボリュームは残るので、これで削除する必要がある
docker network ls #ネットワーク一覧を確認
docker network create #ネットワークを作成
docker network connect #ネットワークに接続
docker-compose ps #docker-composeで起動したコンテナの一覧を表示
docker-compose up #ymlに記述した設定からコンテナ起動/再起動
docker-compose run コンテナ名 コマンド #指定したサービスコンテナ内でコマンドを実行
docker-compose start #一連のコンテナ起動
docker-compose down #一連のコンテナ終了
```

## 参考

- [【図解】Dockerの全体像を理解する -前編-](https://qiita.com/etaroid/items/b1024c7d200a75b992fc)

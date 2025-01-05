---
theme: light-icons
title: SQL Server輪講
drawings:
  persist: false
transition: fade
mdc: true
overviewSnapshots: true
---

<div class="flex flex-col justify-center items-center">
  <div class="text-6xl font-bold" >
    <twemoji-pine-decoration />SQL Server輪講<twemoji-pine-decoration />
  </div>
  <div class="text-4xl mb-10" >
    第8回 ~ネットワーク~
  </div>
  <div class="text-xl" >
    2025/1/10 江袋 叡
  </div>
</div>

---

# 今回やること

- SQL Serverとクライアントの通信方法
  - プロトコル
  - どのように
  - クライアントからインスタンスを探す流れ
    - ポートを探す
    - キャッシュ

---
clicks: 1
---

# SQL Serverとクライアントが通信を行うには

- SQL Serverの通信では独自のフォーマットや抽象化アルゴリズムが用いられている
  - ホストとクライアントの双方にネットワークコンポーネントが必要
- プロトコルは何種類かある
  - この部分の差異はSNI(SQL Server Network Interface)層によって吸収されている

<div class="flex h-80 justify-center">
  <img src="./images/protocol.drawio.svg" alt="protocol" v-if="$clicks === 0"/>
  <img src="./images/protocol2.drawio.svg" alt="protocol" v-if="$clicks === 1"/>
</div>

---

# SNI層

- 通信時は基本的に1つのプロトコルが使われるが、別のプロトコルを有効化しておくこともできる
  - デフォルトのプロトコルで接続できない場合に、別のプロトコルを使って接続を試みる
  - 複数のクライアント毎に、それぞれ異なるプロトコルで待機する

<div class="text-xs">

| プロトコル                     | 説明                                                                                                                                                                                                                                  |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TCP/IP                         | 相互に接続されている<span class="text-red">ネットワーク上のコンピュータ間</span>の通信を実現<br>インターネットで広く使われている                                                                                                      |
| 名前付きパイプ                 | <span class="text-red">同一コンピュータ/ネットワークで実行されているプロセス間</span>で、共有メモリ領域を使用してやり取り                                                                                                             |
| 共有メモリ                     | SQL Serverとクライアントが<span class="text-red">同一のコンピュータ上で実行されている場合</span>に使用される<br>最も単純<br><span class="text-blue">設定もあまりできなくて多くの場面で使用されない、トラブルシューティングなど</span> |
| VIA(Virtual Interface Adaptor) | 仮想化専用ハードウェアで動作する<br><span class="text-blue">SQL Server2016以降では非サポート </span>                                                                                                                                  |

</div>

---

# SNI層

- [インストール後の構成](https://learn.microsoft.com/ja-jp/sql/database-engine/configure-windows/default-sql-server-network-protocol-configuration?view=sql-server-ver16)は↓
- [Named Pipes vs. TCP/IP Sockets](<https://learn.microsoft.com/ja-jp/previous-versions/sql/sql-server-2016/ms187892(v=sql.130)#named-pipes-vs-tcpip-sockets>)
  - WANやダイアルアップ接続などで低速環境の場合、名前付きパイプは非常にコストが掛かるらしい
  - また、名前付きパイプでホストとクライアントが同一環境にいる場合ｓ、カーネルモードで実行され非常に高速

<div class="text-xs">

| Edition            | 共有メモリ | TCP/IP  | 名前付きパイプ               |
| ------------------ | ---------- | ------- | ---------------------------- |
| Enterprise         | Enabled    | Enabled | ネットワーク接続に対して無効 |
| Standard           | Enabled    | Enabled | ネットワーク接続に対して無効 |
| SQL Server Express | Enabled    | 無効    | ネットワーク接続に対して無効 |

</div>

---

# アプリケーションプロトコル層

- アプリケーションプロトコル層では、<span class="text-red">TDS(Tabular Data Stream)</span>でデータを扱う
- SNI層では、TDSに各プロトコル毎のヘッダーを付与して送信している

<div class="flex h-80 justify-center">
  <img src="./images/protocol3.drawio.svg" alt="protocol"/>
</div>

---
clicks: 1
---

# Tabular Data Stream

- RDBMSにおいて効率的にデータを扱うためのプロトコル
- 基本的にSQL Serverにおいて使用されている
  - 昔のSybase Adaptive Server Enterpriseでも使用されていたらしいが、それぞれ独自に進化していった
  - Postgresでは[フロントエンド/バックエンドプロトコル](https://www.postgresql.jp/document/8.0/html/protocol.html)というものが使われているらしい

---

# Postgresでは...

- クライアントと呼ばれているものは、psqlなどと呼ばれているものが該当する
- [フロントエンド/バックエンドプロトコル](https://www.postgresql.jp/document/8.0/html/protocol.html)というものが使われているらしい
- サポートしているプロトコルは↓
  - TCP/IP
  - UNIXソケット

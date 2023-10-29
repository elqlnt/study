# Vue Fes

## 所感

- 意外とVue2.6以下のところ多い(めちゃくちゃ多い訳では無い)

![アンケート](https://pbs.twimg.com/media/F9hByJ-bwAA2FUR?format=jpg&name=large)

## 基調講演

- Evan自身もミスった部分とうまく行った部分があると感じている

- ミスった部分
    - 多くの小さな破壊的変更をしすぎた
    - とっつきにくい

- メリット
    - TypeScript
    - Composition API
    - DX(開発者環境)
        - Vite
        - ドキュメント

- うちの環境だとこの内の2つを捨てることになるな

## 走りながらエンジンを交換する 〜 大規模プロダクトを成長させつつVue 3にするには 〜

- Vue2.6以下使ってる人ほとんどいない...
- BEM使ってるらしい
- Vue2でもComposition API使えるんだ(外部ライブラリ)
- 今はVue2.7
    - 以下の話はVue2.7へのアップデート時の取り組み
- Vue3にアップデートしていない
    - ビジネス面
        - 機能追加が優先されている
    - 技術面
        - ライブラリ問題
        - 関連ライブラリを含む破壊的変更への対応
        - PRが巨大になる
- 解決策
    - プラットフォームチームの設立
        - 足回りの改善
        - 機能提供と別のチーム
    - 小さく始める
        - 2.7を経由
        - 社内用の管理画面など、部分的なところから

- 業務がら、超巨大PRはやはり避けたい
- それをラップするモジュールを作る
    - ソースコードの書き方を変更することなく、(他の開発者が意識することなく)アップデートできた
    - 4ヶ月くらい？
    - 全部で7ヶ月ぐらい？

- Vue3へは@vue/compat+エラー対応(うちと同じ)
- EventsAPI→mitt

- 弁護士ドットコムのテックブログにあるらしい

## 社内UIコンポーネントライブラリがエンジニアチームにもたらした本当の価値

- UI/UXの統一、社内用UIコンポーネントライブラリ開発
    - うちでいうBootstapを社内用にしているような感じ？

- フロント/バックエンドどっちもやれる人が多い(うちと似てる)
- 問題点
    - 統一されていないデザイン
        - 色が違う
    - 使いづらいコンポーネント

- これらを統一するために社内用UIコンポーネントライブラリ開発を行った

- Tailwind CSSを基本とした
- 社内向けなのでドキュメンテーション(Storybook)
    - PRの変更点がわかる
- **一個品質が高いプロジェクトがあれば、それがコード自体のリファレンスになる**

- chromatic(storybookのホスティングサービス)
    - スナップショット間の比較
        - **UIレビュー**→コードレビュー→コード修正のサイクル
        - ビジュアルリグレッションテスト(Vue3にも)

## Vue.jsを活用して開発リードタイムが1/3になった話(→価値を生む技術提案)

- 発案、提案ミスって皇族の開発評価が地獄だった
    - 現状・課題・理想・優先度
    - リファクタリングに関しては難しいが、費用対効果は出さないといけない
        - 例えばリードタイム
- 上記があやふやだと、技術的意思決定ができない
    - アイデアが発散して技術スタックが追いついてない

- 古いアーキテクチャは、文句はあるかもしれないけど実績がある

- Whyを提案してFBを受けてHowを見直す

## Vue 2のEOLまで二ヶ月ですが進捗どうですか？

- Vue3 migration guide
- webpack→rspack?

- 多分このセッションだからだと思うけど、結構Vue2使っている人多い

- EOLをすぎると
    - アップデートが入らなくなる
    - npm/cdnは引き続き使える
    - 準公式で引き続き有償でサポートを受けられるが、値段は非公開

- 使い続けていいのか？
    - 2.7であれば問題ない
        - setup script

### まずは可視化

#### 1つめ

- eslintでVue3のルールでエラーになったダイルを徐々にmigrate
- エラーが発生したファイルをエラー対象から除外
    - 別途読み込む(extends?)
- eslintのカスタムルールでVue2の記述を排除
    - 例えばv-modelがあったらeslintで落ちるようにする
- createAppのラッパーを追加

#### 2つめ

- Vue2とVue3が共存？？
    - package.jsonにエイリアスを設定
    - webpackとviteを共存

#### 3つめ

- 最初からCompositionAPI

## Vue.jsプロジェクト設計のベストプラクティスを求めて

- 迷わないための設計
    - 構造と名前を考える時間がかかっている
    - 遅くならないこと

## 画面遷移から考えるNuxtアプリケーションをアクセシブルにする方法

- 合理的配慮の提供が義務化される
- Vueで作っているアプリケーションがアクセシブルなのか？
    - あまり良くないらしい

- クライアントサイドルーティング
    - 早い
    - 状態を保持できる

- View transisions API
    - スムーズな画面遷移

### 観点

- ページが遷移されたことを通知できているか？
    - hiddenにするとアクセシビリティが検知できない
        - 資格上だけで消すようにする
- フォーカスマネジメント
    - タブキーとか

## 18営業日で350コンポーネント規模のVueアプリにデザインシステムを導入する方法

- デザインシステムを導入した
    - デザインはアプリケーション全体で統一が取れていないといけないので、必然的にビッグバンリファクタリングになった
    - でもビッグバンリファクタリングをすると、既存機能の開発と並行できないので、とにかく素早くリリースすることを目標とした

- ノウハウとして、全員が20%で勧めていくよりも、ある人が中心となって進めるほうが効率がいいらしい

- 方針
    - 進捗は数値化
    - マージンやパディングなどの細かい調整は後回し
    - デザイナーとエンジニアが一緒に並行してUIを構築するペアデザイン

- Tips
    - 例えばデザインの統一のために、テキストをコンポーネントでラップした、これを守っていないコードはeslintでレビュー前に排除するようにした
        - レビュー負荷を低減
    - Chromatic
        - プッシュにフックしてUIの変化を通知してくれる？
    - e2eテストで、主要機能はチェック
    - 可能な限り自動でマイグレーション
        - コード化することで、あるタイミングで一気にマイグレーションできる→他の人の街が発生しない
        - やり方は何個岡アルが、正規表現を使うとご検知する可能性がある
        - ASTを変更すると良いらしい

- AST(Abstract Syntax Tree)
    - ASt Explorerなどで見れるらしい
    - VueはtemplateとScriptとStyleから構成されているので、普通には使えない
    - VueをASTに変換するには正規表現/Recast?/Magic String?

- 公開してくれているらしい
    - vue-service-bay

## Vue Language Serverから生まれたVolar.jsと、それが秘める可能性

- エディタの言語機能
    - コード補完
    - 定義元への移動
    - 構文エラー
- このような機能はLanguage Server Protocolを用いている
    - VueだとVeturやVolar
- Vueは特殊で.vueにhtml・javascript・cssが混在している

- Veturとは別実装のVue Language Feature
    - こいつのコアがVolar.js

- Veturで直面した課題は、組み込み言語に対する共通のもの

- Volar.jsを使うとチェッカーやフォーマッターに使える
    - 社内フレームワークに対しても使える

## ライトニングトーク

- Vueは意識しなくてもSOLID原則を満たせるような構造になっている
- 基本状態は親に持つ
- ComposiotionAPIでPub/Subパターンを使うことでVuex/Piniaを使わずに状態管理できる
- errorCaptureeeed
    - コンポーネントや画面ごとのエラー処理
- Vue.config.errorHandler
    - グローバルのエラーハンドリング

## マルチスレッドフレンドリーなJavaScriptを求めて

- Javascriptはシングルスレッド
- 回避策
    - Javascriptのエンジン外で実行する
        - NodeAPI
            - Babelなど？
        - イメージは`fetch`
    - 複数のJaascriptエンジンのインスタンス
        - 単純に別プロセスを起動
        - Cluster
        - Worker Threads

- 単にマルチスレッドにすれば早くなる訳では無い
    - 参照の共有ができない
    - 関数やクラス情報はコピーできない
    - 値はコピーされても参照が別

- `structuredColne`

- マルチスレッドの対象とする処理の選定
    - 依存関係が少ない
    - 処理が多そう

- 上記のようにマルチスレッドにしたからといって、必ずパフォーマンスが改善することはないので、試行錯誤しましょう
    - それは面倒なので、artichokieを使ってみては

## eslint-plugin-vueの現状と今後

- Vue3へのマイグレーションツールとして

## 発表資料

- キーノート
- [走りながらエンジンを交換する 〜 大規模プロダクトを成長させつつVue 3にするには 〜](https://speakerdeck.com/bengo4com/20231028)
- [社内UIコンポーネントライブラリがエンジニアチームにもたらした本当の価値]()
- [Vue.jsを活用して開発リードタイムが1/3になった話(→価値を生む技術提案)](https://speakerdeck.com/lmi/vuefes2023-link-and-motivation)
- 「Youはなぜコントリビュータに？」論より動くもの.fm 出張版
- [Vue.jsプロジェクト設計のベストプラクティスを求めて](https://speakerdeck.com/cyber_snufkin/28-vue-fes-tokyo-vue-dot-js-puroziekutoshe-ji-nobesutopurakuteisuwoqiu-mete)
- [Vue 2のEOLまで二ヶ月ですが進捗どうですか？](https://www.slideshare.net/KazuhiroKobayashikzh/vue-2-eol-2)
- Nuxt 3ではじめるテスト導入戦略と初手
- [Nuxt 2から3へマイグレーションする方法考えてたら、マイクロフロントエンドのフレームワークができた話](https://tome.app/mewton-8cb/vue-fes-2023-clnjmh8ez0044l77dwardvtga)
- OpenAI APIをNuxt.jsに入れてみた的な話
- Nuxt to the Edge
- [Vueを使ってGrid Systemを実装した話](https://speakerdeck.com/t0yohei/vue-woshi-tute-grid-system-woshi-zhuang-sitahua)
- [WebGISとVue.jsの親和性について](https://docs.google.com/presentation/d/1KwLPyFLE0J3W9BwFmROHtgG0qQbGdYCnbEXjuJTYpJ4/edit?pli=1#slide=id.g24fad336807_0_0)
- [Nuxt3のモジュール開発は意外と簡単？ Module Author Guideをのぞいてみよう](https://www.docswell.com/s/kira_puka/ZRXM6E-2023-10-25-064822)
- [Vue 3/Electronで自作したマークダウンエディタをVue 3/Tauriにリプレイスした話](https://speakerdeck.com/yud0uhu/tauriniripureisusitahua)
- [画面遷移から考えるNuxtアプリケーションをアクセシブルにする方法](https://yamanoku.net/vuefes-japan-2023/ja/)
- A New Nuxt
- [18営業日で350コンポーネント規模のVueアプリにデザインシステムを導入する方法](https://speakerdeck.com/baseballyama/vue-fes-2023-18ying-ye-ri-de350konponentogui-mo-novueapurinidezainsisutemuwodao-ru-surufang-fa)
- Nuxt 3でJamstackテンプレートを作るときの考え方
- Anthony's Roads to Open Source - The Set Theory
- Demystifying Nuxt Bridge 〜 あなたがまだ見ぬ可能性とその活用法 〜
- [Vue Language Serverから生まれたVolar.jsと、それが秘める可能性](https://speakerdeck.com/mizdra/vue-language-server-karasheng-mareta-volar-dot-js-to-soregami-meruke-neng-xing)
- Vite: Stories of collaboration
- Deep Dive to UnJS and Nuxt 3
- [SOLID原則に基づくSFC実装](https://slides-one.vercel.app/1?clicks=1)
- Composition API時代のPub/Subパターンでの状態管理
- Exploring the Power of Error Handling in Vue JS
- [フルスクラッチECの基盤であるNuxt 2を3に移行し、開発の効率性とパフォーマンスを高める](https://speakerdeck.com/wakkn/hurusukuratutiecnoji-pan-dearunuxt-2wo3niyi-xing-si-kai-fa-noxiao-lu-xing-topahuomansuwogao-meru)
- Getting your head around your <head>
- [マルチスレッドフレンドリーなJavaScriptを求めて](https://vue-fes-japan-2023-multithread-slide.sapphi.red/1)
- [Vue.jsと3D可視化 - 産総研のOSS「AIST 3DDB Client」を例に](https://speakerdeck.com/sorami/vue-fes-japan-2023)
- [eslint-plugin-vueの現状と今後](https://ota-meshi.github.io/vue-fes-japan-2023-slide/)
- STUDIOの作り方 2023 ver.
- パネルディスカッション
- [Vueクリニック](https://twitter.com/punksy2/status/1718174713955090610?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1718174713955090610%7Ctwgr%5E279b4c0280f8ce64a4dc634582bcea337a73d831%7Ctwcon%5Es1_c10&ref_url=https%3A%2F%2Fembed.zenn.studio%2Ftweetzenn-embedded__3aa196ac1136d)

## その他

- [AI IDE](https://x.com/Samuraism/status/1718244099617407286?s=20)
- [script setupんい書き換える](https://x.com/pontaxx/status/1718184099775660268?s=20)
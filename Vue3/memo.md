# 以降メモ

- eslint
- prettier
  - フォーマットが2重にかかっている
- vite
  - es6?wikiにかいてる？

- babel
  - es5へのトランスパイル
  - 古いブラウザへの対応？
  - Promiseは変換されないらしいので、別に設定が必要

- CommonJS/ECMAModule
  - Node.jsとECMAScriptのモジュール管理
  - requireとimport

- オプショナルチェーンはes11から
  - トランスパイルするbabelのバージョンが古くて、できない？
  - エラー文みたい

- jsxどこかでつかってる？
- <https://zenn.dev/sprout2000/articles/9d026d3d9e0e8f>
- <https://www.sunapro.com/webpack-to-vite/>
- <https://qiita.com/SeijiNishiwaki/items/369342919774cbebc4e1>
- IE
  - plugin-legacy
  - <https://studist.tech/dropping-support-for-ie11-abbd36882c61>
  - type:moduleいる...?

- airbnbはreact用の設定を含んでいる
- airbnb-baseを使うべきだが、es6でしか動かない
  - parseroptionで2021とかを指定すればOK
  - parserOptionはあくまで構文解析
  - 新しく追加されたオブジェクトを扱うには(BigIntなど)envを指定する
  - だけどこれいいのかな

- babelが古かったので(2018)、そもそもes9しか動かん
  - es6で書くとか言っておいて、includes使っちゃってたし
  - 関数末尾のカンマ (,)はes8
  - airbnb-baseはparseroptionが2018(es9)だったから動いていた

ーjavascriptのバージョンを上げられるかどうかはパッケージに依存する？
    - パッケージのバージョンは上げたくない
        - 依存先が

- 結局対応したいブラウザのバージョンによるのか...
- vite自体はplugin-legacyでIE対応はできるんですね

- vue3を使うためにはnode12

- vite以降は必須ではないが、公式に推奨されているのでやる

- nodeのバージョンを上げなくてはいけないので、必然的にnode-sassとsass-loaderのバージョンを上げなければ行けない
  - ただし、node-sassは非推奨なので、dart sassのsassに乗り換えたい
    - メンテナンスリリースは続けるけど、機能追加は行わない
  - そうすると@importが使えなくなる

- Viteにする理由の一つとして、Nodeのバージョン上げたときにWebpackの動作検証するんだったら変えてしまえばいい

- blowserlist
  - これを元に他のOSSが自動で判断してくれる
    - [Babel](https://zenn.dev/sa2knight/articles/67f6f5cc4ed5e26e391c)
      - どのように変換するか？は本来開発者が適切なプラグインを入れる必要がある
      - 必要なプラグインを自動で選択して、最新のES6+を動く状態にしてくれるプラグインがbabel/preset-env
      - .babelrcのプラグインに設定する
      - あとはbrowserslistに記述
      - babelがやってくれるのは構文なので、Promiseを使うにはcore-jsが必要らしい
        - pluginsにuseBuiltInsとcorejsを指定する
    - ESLint
      - これもブラウザがそれぞれ対応しているやつ、そうでないやつを
      - eslint-plugin-compatをpluginsに記述する
      - あとrules
    - [PostCSS](https://morishitter.hatenablog.com/entry/2015/08/03/164424)
      - CSSパーサーとそのASTを操作するためのAPIのみを提供する
      - つまり、ユーザーがこれ単体で使うことはない？(依存先としてインストールされる？)
        - Autoprefixerやstylelintが利用
      - jsのトランスパイルのCSS版みたいな感じ？
      - 変数が使えたり、ネストができたりする
      - 生成されたCSSに対して後処理ができる(プリプロセッサとしても使える)
        - Autoprefixer
          - ベンダープレフィックスを自動で付与する
            - chromeだったらwebkit
          - 各ブラウザで機能を動作させるためには、プロパティや値の先頭にプレフィックスを付ける必要がある(試験的な機能とか)
          - ビルド時に設定するには、Viteのcssオプションに指定する
- [Browserslist でサポートブラウザを設定しよう](https://devblog.thebase.in/entry/2021/12/05/110000)

- eslintのenv:browserは、ブラウザを使うときに出てくる`window`などのグローバルな値を使ってもエラーが出ないようにする

- qsはクエリの解析、文字列化をするライブラリ
  - `parse`は文字列をオブジェクトに変換する
  - `stringigy`はオブジェ宇土をURL形式の文字列に変換する

- SassにはSASS記法とSCSS記法がある
- こいつをコンパイルするのがnode-sass

- stylelint?
  - プロパティの順番をアルファベット順にしてくれる？

## 参考

- [[LibSass非推奨化] node-sassとのお別れ ~ Dart Sassへ移行する](https://deep.tacoskingdom.com/blog/48)
- [巷で人気のViteを触ってみた](https://yurika1202.com/post/coding/vite/)

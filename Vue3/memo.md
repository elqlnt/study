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

## 参考

- [[LibSass非推奨化] node-sassとのお別れ ~ Dart Sassへ移行する](https://deep.tacoskingdom.com/blog/48)

# 概要

- 大規模開発への対応
    - 高速化
        - Tree Shaking
    - 長距離のProps
        - `Provide`や`Inject`
    - CompositionAPI
    - IE11未対応

# 特徴

- 宣言的にかけるようになった
    - エントリが`createApp`
    - vuexなどの読み込み時は`use`チェーンで繋げられる
- その他細かいところ
    - template内には複数のブロックをかける
    - devtoolは3系専用のものが必要
- Composition API

# Composition API

- 目的は**状態を持った**ロジックの抽出と再利用
- 肥大化したコンポーネントを関心事に小分けする
    - 今までは`computed`で定義されている`data`を確認するために上に行ったり下に行ったりしていた
    - vue2では1つのコンポーネントに状態・View・ロジックを閉じ込めておくことができたがこれ以上分割できなかった
    - これらを分離したいのがVue3

![compositionapi](https://ja.vuejs.org/assets/composition-api-after.e3f2c350.png)

- つまり大規模開発向けなので、小さいプロジェクトで使用しても旨味が少ない
- あとこいつは今までのOptions APIよりも遥かに自由なので、ちゃんとクリーンアーキテクチャなどを学ばないと大変なことになる
    - Vue2は様々な制限があったことで道を外れにくいような仕組みになっていた

## 具体的に何が変わったか？

- 抽出と再利用というように、必要なものを都度インポートする
    - `createApp/ref/computed`など
    - mixinでよいのでは？と思うが以下のデメリットが有るみたい
        - プロパティの発生元が不明確
        - 名前空間の衝突
        - 暗黙的なミックスイン間のやり取り
- ただし、今までのOptions APIと混ぜて書くこともできる

### コードの話

- Composition APIを使うには、`created`よりもはやい`setup`で色々と定義していく
- このタイミングでは`this`が使えない
    - アローを使おう
- ここで、今まで`data`とか`mounted`とかで定義していたことをまとめて`return`する
    - vue-routerやvuexもインポートして、ここで`return`する

#### 変数

- 変数をリアクティブにするには`ref()`や`reactive()`を用いる
    - `ref()`はプリミティブな値を対象とする
        - リアクティブを実現するためのオブジェクトになるので、使用する際は`変数.value`の用に使う
    - `reactive()`はオブジェクトを対象とできる
        - 引数に以前の`data`でやっていたようなオブジェクトを返す
    - こうすると、実際使いたい値はオブジェクトのプロパティとなって記述量が増えるため、避けたいならスプレット構文を使う
        - このときオブジェクトに対して`toRefs()`をしてからスプレッドしないと、リアクティブにならない

- 
#### 関数

- 関数も基本的に`setup`で`return`する
    - ただし、関数定義自体はどこでも良い
    - プレーンなjsで書ける
- ただ関数はComposition APIの目的でもあるように、他のコンポーネントでも使うことを前提とする(合成関数)
    - これを明示するために、慣例としてメソッド名の先頭に`use`をつける
- 使いたいときは、`setup`内で分割代入
- こうすることで、同じ機能を持ったもの同士でモジュール化することで、インポート時にも同じ役割を持った者同士で固まることになる

#### `computed`

- `computed`メソッドの引数に関数オブジェクトを渡す
- `getter`と`setter`を使う場合は、引数に`get`プロパティと`set`プロパティを持ったオブジェクトを渡す

#### `watch`

- 第一引数に監視対象の変数、第二引数にはコールバック変数
- `watchEffect`はより簡単にかける
    - 第一引数にコールバック関数、その中にリアクティブ変数を書く
    - `computed`みたいですね
    - 注意点は初回も実行される

#### イベント

- `emit`を使う場合は、`setup`の第二引数にオブジェクトで`{emit}`を渡すか`context`を渡す
    - 前者は`context`の分割代入
    - `this`が使えないので

#### `provide`/`inject`

- 今までは親子間のデータ受け渡しは`props`だった
    - `setup`時に引数として`props`を受け取ることができるらしい
- ただ、孫までやろうとするとバケツリレーのようになってしんどい
- これをオブジェクト参照で持ってこれるようにしたのがこいつ
- Composition APIでは状態とロジックをViewから分離・抽出し再利用したかったが、これは状態を共有するための仕組み
- 適宜必要であればインポートすることになるので、本来必要ないコンポーネントに情報を渡さなくて済む

#### `Teleport`

- 描画先の親を指定できるらしい
- モーダルで役立つそうだけど使うのか？

#### ライフサイクルフック

- 基本的にvue2と同じだが、`beforeCreated`や`created`は無い
- それ以外は`onMouted`のように頭に`on`がつく

### script setup

- vue3.2からの機能
- SFC内で、Composition APIをシンプルに書ける
- 色々パフォーマンスが向上しているらしい

- `export default`や`return`を記述しなくても良い
- 今までは`<template><script><style>`の順だったけど、`<script setup>`を最初に書くことが推奨されている
- `setup()`がなくなるので、`props`の書き方が変わる
    - `defineProps()`
- 同様に`emit`も変わる
    - `defineEmits()`


# 参考
- [Vue3 Composition APIにおいて、Providerパターン(provide/inject)の使い方と、なぜ重要なのか、理解する。](https://qiita.com/karamage/items/4bc90f637487d3fcecf0)
- [なぜ、Vue Composition APIを使うのか、理解する【メリット/デメリットまとめ】](https://qiita.com/karamage/items/7721c8cac149d60d4c4a)
- [Composition API に関するよくある質問](https://ja.vuejs.org/guide/extras/composition-api-faq.html)
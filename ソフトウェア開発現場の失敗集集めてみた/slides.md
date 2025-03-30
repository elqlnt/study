---
theme: light-icons
title: ソフトウェア開発現場の「失敗集」集めてみた
drawings:
  persist: false
transition: fade
mdc: true
overviewSnapshots: true
---

<div class="flex flex-col justify-center items-center">
  <div class="text-6xl font-bold text-center mb-4" >
    ソフトウェア開発現場の<br>「失敗集」<br>集めてみた
  </div>
  <div class="text-4xl mb-10" >
    第4回
  </div>
  <div class="text-xl" >
    2025/4/1 江袋 叡
  </div>
</div>

---

# 今回のお話

「仕様」で失敗シリーズ

- 実装できない「ふんわり仕様」
  - 仕様そのものがあいまいなお話
- 解読が必要な「難読仕様書」
  - 仕様書の書き方があいまいなお話

---
layout: image
image: images/7.jpg
---

<div class="size-full flex justify-center items-center bg-white bg-opacity-50">
  <div class="flex w-fit justify-center items-center bg-white bg-opacity-80 text-6xl font-bold text-pink-600 p-4">
    実装できない「ふんわり仕様」
  </div>
</div>

---

## データファイルの保護をしたい...

<div class="h-96 flex justify-center items-center gap-x-20">
  <div class="w-1/2 text-xl" >
    
  - セキュリティのサーベイがあって、データファイルを暗号化する仕様が追加になった
  - 暗号化だけならライブラリ呼び出すだけだし余裕そう
  - 2日あればできるかな
  - とりあえず要件はこんな感じで...
    - > 要件：データはパスワードで保護すること

  </div>
  <div class="w-1/4" >
    <img src="./images/2.png">
  </div>
</div>


---

## ...で、どう実装する?

> 要件：データはパスワードで保護すること


<div class="h-96 flex justify-center items-center">
  <div class="w-1/2 flex justify-center" >
    
  - 強度要件
    - 長さ
    - 文字種
  - 入力時
    - 入力値のマスク
    - コピペの禁止
    - 現在のパスワードの強度レベルの表示
    - 一時的に表示するボタン
  - 関連機能
    - パスワードリセット機能
  - 他にもありそう...

  </div>
  
  <div class="w-1/2 flex justify-center" v-click >

  <div>

  気軽に引き受けたはいいが、実装者の一存で決められないものが多い...

  <span class="text-blue">評価工数</span>も予定より増大<twemoji-chart-increasing />

  </div>

  </div>
  
</div>

---

## なぜこのようなことが起きてしまうのか


<div class="h-72 flex justify-center items-center">

- <span class="text-blue">設計者の経験が浅く</span>、十分な想定ができない
- 本当に必要な要件が、<span class="text-blue">一担当者では判断できない</span>
- 面倒なのでとりあえず書いたはいいが、<span class="text-blue">詳細を考えずにそのまま</span>
- 要件の粒度が大きすぎる

</div>

<div class="flex justify-center items-center text-2xl" v-click>

開発初期ほどふんわりして、工数見積も難しい...

</div>
<div class="flex justify-center items-center text-2xl" v-click>

なるべくふわふわ仕様<twemoji-cloud />を避けるにはどうすればよいか <twemoji-thinking-face />

</div>

---
clicks: 1
---

## ユーザーの利用シーンを具体的に想像してみる<twemoji-light-bulb />

ステークホルダーを集めて、ワークショップ形式で実践すると良いらしい。

> 「今日の仕事終わりにアームチェックの状況を確認しよう。」
> 
> そういって俺はアプリのデータ確認ボタンをクリックして、<span class="text-red">4桁のパスワード</span>を入力した。
>
> 「えーっと、パスワードは1,2,3,4っと...<span class="text-red">あ、声に出しちゃった</span>」
>
> 正直なところ、操作室への出入りは限られているので別にパスワードはなくてもいいと思うのだが、データにアクセスする権限を規制することで、<span class="text-red">ポカミスやカジュアルなデータ改ざんを防ぐ</span>狙いがあるらしい。

今回の例だと、具体的な要件と、簡単な確認ができれば良い機能である、ということがわかった。

<span v-if="$clicks === 1">利用シーンを明確にすることで、非機能要件まで見えてくる。</span>

<div class="flex justify-center items-center" v-if="$clicks === 1">

```mermaid {theme: 'neutral', scale: 0.6}

graph LR
    利用シーン仕様書 --> 機能/非機能仕様書
    利用シーン仕様書 --> UI仕様書
    利用シーン仕様書 -.-> 詳細設計書
    利用シーン仕様書 -.-> テスト仕様書
    機能/非機能仕様書 --> 詳細設計書
    機能/非機能仕様書 --> テスト仕様書
    UI仕様書 --> 詳細設計書
    UI仕様書 --> テスト仕様書

```

</div>



---

## 教訓

<div class="w-full h-96 flex flex-col justify-center items-center">
<table class="text-xl">
<tr>
<td>
  <div class="font-bold text-sky-600 flex justify-center items-center px-16">失敗<twemoji-weary-face /></div>
</td>
<td>

- <span class="text-blue">詳細があいまいな</span>「ふんわり仕様書」で日程遅れを出した

</td>
</tr>
<tr class="!border-0">
<td>
  <div class="font-bold text-pink-400 flex justify-center items-center px-16">回避策<twemoji-thumbs-up /></div>
</td>
<td>

- 最初に<span class="text-red">利用シーン仕様書を作成</span>し、システムのあるべき振る舞いを想定する

</td>
</tr>
</table>
</div>

---
layout: image
image: images/8.jpg
---

<div class="size-full flex justify-center items-center bg-white bg-opacity-50">
  <div class="flex w-fit justify-center items-center bg-white bg-opacity-80 text-6xl font-bold text-pink-600 p-4">
    解読が必要な「難読仕様書」
  </div>
</div>

---

## イイカンジのレイアウト

<div class="h-96 flex justify-center items-center gap-x-20">
  <div class="w-1/2 text-xl" >
    
  - ダイアログ内のUIパーツをバランスよく配置してほしい
  - 画面を拡大/縮小してもバランスを損なわないように
  - もちろん操作性を損なわないように
  - こんな感じの仕様で...
    - > 仕様：ダイアログは「サイズ変更グリップ」でウィンドウサイズを変更できる。その際各要素のバランスを崩さないようにすること。

  </div>
  <div class="w-1/4" >
    <img src="./images/1.png">
  </div>
</div>

---

## 作ってみたはいいものの...

> 仕様：ダイアログは「サイズ変更グリップ」でウィンドウサイズを変更できる。その際各要素のバランスを崩さないようにすること。

どちらも仕様通りに実装していると言える。
どうなれば正解?

<div class="w-full flex justify-center items-center">
  <img src="./images/dialog.drawio.svg" class="w-2/3">
</div>

---

## なぜこのようなことが起きてしまうのか

<div class="h-72 flex justify-center items-center">

- 仕様書の解釈が人によって分かれるような書き方をしてしまった
- 結論や伝えたいことが明確でない(<span class="text-blue">ロジカルシンキング</span>ができていない)
  - 外注する場合は共通認識も薄くなりがちなので更に注意が必要

</div>

<div class="flex justify-center items-center text-2xl" v-click>

なるべくあいまいな記述を避けるにはどうすればよいか <twemoji-thinking-face />

</div>

---

## いろんな手段で曖昧さを減らす<twemoji-memo />

ロジカルな文章を組み立てることができるのであればそれに越したことはないが、なかなか難しい。

- 仕様書に図や絵を添えてみる

<div class="flex justify-center items-center">

<img src="./images/dialog_size.drawio.svg" class="w-2/3 flex justify-center items-center">

</div>

<div v-click>

- 仕様を再考してみる
  - そもそもこの機能はユーザーにとって必要なのか?
  - ダイアログの大きさは変更できなくても良いのでは?

</div>

---

## 教訓

<div class="w-full h-96 flex flex-col justify-center items-center">
<table class="text-xl">
<tr>
<td>
  <div class="font-bold text-sky-600 flex justify-center items-center px-20">失敗<twemoji-weary-face /></div>
</td>
<td>

- <span class="text-blue">あいまいな文章で</span>で仕様書を記載し、設計ミスが発生

</td>
</tr>
<tr class="!border-0">
<td>
  <div class="font-bold text-pink-400 flex justify-center items-center px-20">回避策<twemoji-thumbs-up /></div>
</td>
<td>

- より<span class="text-red">シンプル</span>で伝わりやすい仕様に
- <span class="text-red">簡単な絵などを添えて</span>、意図をより明確に

</td>
</tr>
</table>
</div>

---

# まとめ

<div class="w-full h-96 flex flex-col justify-center  text-2xl">

- 仕様を考えるときは、利用シーンの認識を明確に
- 仕様はなるべくシンプルに、複雑になりがちな場合は図や絵を添えて意図を明確に

</div>

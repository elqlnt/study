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
  <div class="text-xl" >
    2025/7/29 江袋 叡
  </div>
</div>

---

# 今回のお話

「進捗管理」で失敗シリーズ

- メールが業務の起点「メールドリブンワークスタイル」
  - タスクの依頼をすべてメールでやってしまう
- 変更されない「完璧な計画書」
  - 何があっても当初の計画を守る

---
layout: image
image: images/mail.jpg
---

<div class="size-full flex justify-center items-center bg-white bg-opacity-50">
  <div class="flex flex-col w-fit justify-center items-center bg-white bg-opacity-80 text-6xl font-bold text-pink-600 p-4">
    <p>メールが業務の起点</p>
    <p>「メールドリブンワークスタイル」</p>
  </div>
</div>

---

## 業務の起点はメール/Teamsになりがち

<div class="h-96 flex justify-center items-center gap-x-20">
  <div class="w-1/2 text-xl">
  <v-clicks>

  - 「資料の作成をお願いします」
  - 「この仕様の確認をお願いします」
  - 「評価項目の確認をお願いします」
  - 「打ち合わせに参加してください」

  </v-clicks>
  </div>
  <div class="w-1/2" >
    <img src="./images/mail3.jpg">
  </div>
</div>


---

## メールなどの連絡は大量に来る

<div class="h-96 flex justify-center items-center gap-x-4">
  <div class="w-1/2 flex justify-center">
  <v-clicks depth="1">

  - そもそも全部ちゃんと目を通していると時間が足りない
    - Github<logos-github-icon />のメール設定: 「All Activity」+数日休んでいると、150件ぐらい溜まっていることも
      - 特にリーダー的な立場になると、もっと色んな人から連絡が来がちな気がする
  - 簡単なメールだと、背景がわからず優先度の判断が難しい
    - ただでさえ大量のメールが来るのに、ちゃんと判断しようとするとパンクしてしまう
    - かといって文章量が多いのも読むのに腰を据える必要が
  - だんだんメーラーを開くのも億劫に

  </v-clicks>
  </div>
  
  <div class="w-1/2" v-click >
  <div class="flex justify-center w-full">
  <img src="./images/funwari.drawio.svg" class="w-3/4">
  </div>
  <div>

  忙しいと業務依頼をTeamsの連絡などで済ませてしまいがちだが、<span class="text-red font-bold">業務の意義や価値、目的、期待などの説明</span>が十分でないと、思わぬ落とし穴になる。

  <span class="text-blue">プロジェクトの遅延<twemoji-turtle /></span>、<span class="text-blue">顧客対応の遅れ<twemoji-turtle /></span>、<span class="text-blue">事業継続のリスク<twemoji-bomb /></span>...

  </div>

  </div>
  
</div>

---

## もちろんテキストベースの連絡はいいところも大いにある


<div class="h-72 flex justify-center items-center">

- <span class="text-red font-bold">自分のタイミング</span>で確認できる
  - 今やっている業務を中断せずに済む
  - 一度中断すると、集中状態に戻るには時間が必要
- <span class="text-red font-bold">エビデンス</span>になる
  - あとから自分で振り返ることができる
  - 言った言わないのトラブルを防ぐ

</div>

<div class="flex justify-center items-center text-2xl" v-click>

...が、認識のすれ違いを抑えるにはどうすればよいか <twemoji-thinking-face />

</div>

---

## 直接会って要請する<twemoji-speaking-head />

結局直接会って、重要性や期待を話すのが一番早い。

進めるべきタスクがあるときは、<span class="text-red font-bold">お互い相手の事情を共有</span>する必要がある。

リモートワークのときも、Web会議を活用する。

<div class="flex justify-center w-full">
<img src="./images/mail2.jpg" class="w-2/3">
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

- <span class="text-blue">業務要請をメールだけ</span>で済ませ、期待する成果が出なかった。

</td>
</tr>
<tr class="!border-0">
<td>
  <div class="font-bold text-pink-400 flex justify-center items-center px-16">回避策<twemoji-thumbs-up /></div>
</td>
<td>

- メールだけで済まさず、<span class="text-red">直接会って</span>要請する。
- 要請をする際には、<span class="text-red">業務の重要性や価値、成果への期待</span>を伝える。

</td>
</tr>
</table>
</div>

---
layout: image
image: ./images/schedule.jpg
---

<div class="size-full flex justify-center items-center bg-white bg-opacity-50">
  <div class="flex w-fit justify-center items-center bg-white bg-opacity-80 text-6xl font-bold text-pink-600 p-4">
    <p>変更されない</p>
    <p>「完璧な計画書」</p>
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

  <img src="./images/aimai.drawio.svg" class="w-1/4 absolute" v-click>
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

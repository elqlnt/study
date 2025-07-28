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
  - 「仕様書の確認をお願いします」
  - 「評価項目の確認をお願いします」
  - 「打ち合わせに参加してください」
  - ...

  </v-clicks>
  </div>
  <div class="w-1/2" >
    <img src="./images/mail3.jpg">
  </div>
</div>

<!-- 
- 聞いてる側も、仕様書レビューとか、誰の確認を取ればいいかわからなかったりする
-->

---

## メールなどの連絡は大量に来る

<div class="h-96 flex justify-center items-center gap-x-4">
  <div class="w-1/2 flex justify-center">
  <v-clicks depth="1">

  - 全部ちゃんと目を通していると時間が足りない
    - Github<logos-github-icon />のメール設定: 「All Activity」+数日休んでいると、150件ぐらい溜まっていることも
      - 特にリーダー的な立場になると、もっと色んな人から連絡が来がちな気がする
  - 簡単なメールだと、背景がわからず優先度の判断が難しい
    - ただでさえ大量のメールが来るのに、ちゃんと判断しようとするとパンクしてしまう
    - かといって文章量が多いのも読むのに腰を据える必要が
  - だんだんメーラーを開くのも億劫に
  - メール以外にも...<logos-microsoft-teams />

  </v-clicks>
  </div>
  
  <div class="w-1/2" v-click >
  <div class="flex justify-center w-full">
  <img src="./images/explain.drawio.svg" class="w-3/4">
  </div>
  <div>

  忙しいと業務依頼をTeamsの連絡などで済ませてしまいがちだが、<span class="text-red font-bold">業務の意義や価値、目的、期待などの説明</span>が十分でないと、思わぬ落とし穴になる。

  - <span class="text-blue">プロジェクトの遅延<twemoji-turtle /></span>
  - <span class="text-blue">顧客対応の遅れ<twemoji-turtle /></span>
  - <span class="text-blue">事業継続のリスク<twemoji-bomb /></span>...

  </div>
  </div>
</div>

---

## もちろんチャットベースの連絡はいいところも大いにある

<div class="h-72 flex justify-center items-center">

- <span class="text-red font-bold">自分のタイミング</span>で確認できる
  - 今やっている業務を中断せずに済む
  - 一度中断すると、集中状態に戻るには時間が必要
    - 最近はチャットベースでも業務が中断されると感じるケース[^1]も多いらしいが...
- <span class="text-red font-bold">エビデンス</span>になる
  - あとから自分で振り返ることができる
  - 言った言わないのトラブルを防ぐ

</div>

<div class="flex justify-center items-center text-2xl" v-click>

...認識のすれ違いを抑えるにはどうすればよいか <twemoji-thinking-face />

</div>

[^1]: [仕事中の“集中力の途切れ”で日本は25.8兆円の損失、Dropbox調査](https://ascii.jp/elem/000/004/175/4175165/)

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

- <span class="text-blue font-bold">業務要請をメールだけ</span>で済ませ、期待する成果が出なかった。

</td>
</tr>
<tr class="!border-0">
<td>
  <div class="font-bold text-pink-400 flex justify-center items-center px-16">回避策<twemoji-thumbs-up /></div>
</td>
<td>

- メールだけで済まさず、<span class="text-red font-bold">直接会って</span>要請する。
- 要請をする際には、<span class="text-red font-bold">業務の重要性や価値、成果への期待</span>を伝える。

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

## 当初の計画から色々ありどんどん遅延...

<div class="h-96 flex justify-center items-center gap-x-20">
  <div class="w-1/2 text-xl" >
    
  <v-clicks>

  - 機能実装が思ったよりも時間がかかった
  - 実装したはいいものの、アーキテクチャを守れていなかったので作り直し
  - 実装後に仕様がひっくりかえる
  - 全く別の仕事が舞い込む
  - メンバー離脱
  - ...

  </v-clicks>

  </div>
  <div class="w-1/2" >
    <img src="./images/schedule3.jpg">
  </div>
</div>

<!--
- 仕様のレビューが思ったよりも時間がかかる、このため実装完了と逆転する
- プロトタイプまで作ったけど、思ったものじゃない
-->
---

## それでも引き直されない計画

<div class="h-96 flex justify-center items-center gap-x-4">
  <div class="w-1/2 flex justify-center">
  <v-clicks depth="1">

  - 開発計画を立ててスケジュールを守るように進めないことには破綻してしまう
    - 後続工程への影響
  - ただし、時によって<span class="text-blue font-bold">極端な残業</span>でなんとかしてしまうことも
    - 間に合ってしまうと、次もそれが前提となった計画となってしまう
    - エスカレートするとメンバーの心身の健康を害してしまう

  </v-clicks>
  </div>
  
  <div class="w-1/2" v-click >
  <div class="flex justify-center w-full">
  <img src="./images/plan.drawio.svg" class="w-3/4">
  </div>
  <div>

  あまりにも現実的ではない状況に陥ってもリスケされないことが常態化すると、<span class="text-blue font-bold">メンバーも相談しなくなる。</span><twemoji-skull />

  結果的に<span class="text-blue font-bold">課題を隠蔽</span>することになる。

  </div>
  </div>
</div>

---

## ソフトウェア開発は遅れるもの

大体いつも想定を超えたことが起こる。

計画を立てることは非常に重要ではあるが、計画通りに完璧にはいかないだろうな、ということだけはなんとなくわかる。

<div class="h-72 flex justify-center items-center">

- 要望があとから追加された
- メンバーが突然入院
- 市場で重篤な問題が発生
- メンバーが引き抜かれた
- プログラムの基礎になるコンポーネントが販売中止/商用利用停止/致命的なバグ
- プログラムがかけないメンバーがいた
- 発注ミス
- 作るものを間違えた

</div>

<div class="flex justify-center items-center text-2xl" v-click>

想定される想定外の事態にはどう対応すればよいか<twemoji-thinking-face />

</div>

<!--
- 重なるインシデント
-->
---

## 変化に強いスケジュール&ツール<twemoji-toolbox />


<div class="h-96 flex justify-center items-center">
  <div class="w-1/2 text-xl" >
    
  - どうせ遅れるので、ある程度バッファを入れておく
  - <span class="text-red font-bold">日程変更に対応できるスケジュール管理ツール</span>
    - <span class="text-red font-bold">クリティカルパス[^1]</span>と<span class="text-red font-bold">人員</span>を可視化できるもの
      - [Microsoft Project](https://www.microsoft.com/ja-jp/microsoft-365/project/project-management)
      - [Lychee Redmine](https://lychee-redmine.jp/)
    - 今の管理ツールはどうでしょう?
      - Githubの[Projects](https://docs.github.com/ja/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/changing-the-layout-of-a-view)
      - エクセルはしんどい
    - 日程見直しのチェックポイントも設ける

  </div>
  <div class="w-1/2" >
    <img src="./images/schedule2.jpg">
  </div>
</div>

[^1]: 「前のタスクが終わらないと次のタスクが始められない」という依存関係で結んだときに、日数が最長になる経路のこと

---
layout: iframe
url: https://www.microsoft.com/ja-jp/microsoft-365/project/project-management
---

---
layout: iframe
url: https://lychee-redmine.jp/
---

---

## 教訓

<div class="w-full h-96 flex flex-col justify-center items-center">
<table class="text-xl">
<tr>
<td>
  <div class="font-bold text-sky-600 flex justify-center items-center px-20">失敗<twemoji-weary-face /></div>
</td>
<td>

- <span class="text-blue font-bold">計画を変更せず、</span>課題対応の遅れとメンバーへの負担を増やした。

</td>
</tr>
<tr class="!border-0">
<td>
  <div class="font-bold text-pink-400 flex justify-center items-center px-20">回避策<twemoji-thumbs-up /></div>
</td>
<td>

- 計画に<span class="text-red font-bold">リスクを組み込む。</span>(バッファとチェックポイント)
- <span class="text-red font-bold">クリティカルチェーンが管理</span>でき、日程変更に強いツールを使う。

</td>
</tr>
</table>
</div>

---

# まとめ

<div class="w-full h-96 flex flex-col justify-center  text-2xl">

- 重要な業務は直接会って、背景を共有する。
- 計画を立てるときはバッファを十分に、適宜見直す。

</div>

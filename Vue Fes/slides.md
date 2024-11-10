---
theme: light-icons
# https://lightvue.org/getting-started/light-icons/
layout: intro
image: 'https://vuefes.jp/2024/main-visual.jpg'
title: VueFes2024
class: text-left
drawings:
  persist: false
transition: fade
mdc: true
overviewSnapshots: true
---

<div class="flex justify-center items-center absolute left-12 bottom-2 mb-60">
    <span class="text-8xl font-bold text-primary-lighter text-opacity-80" >
      <a href="https://vuefes.jp/2024/" target="_blank"
    class="text-8xl font-bold text-primary-lighter text-opacity-80">
      Vue Fes 2024
      </a>
    </span>
  </div>

---
layout: center
level: 2
---

# [Slidev<logos-slidev/>](https://sli.dev/)を使ってスライドを作成してみています

<div v-click class="absolute transform">
  マークダウンベース+TailwindCSSの形式でスタイリングが可能
  <br>
  表示制御にVueのディレクティブが使用可能
  <br>
  pdfやpptxに変換可能
</div>

---
layout: image-right
image: 'https://pbs.twimg.com/media/GaOMcVQbUAEards?format=jpg'
---

# 握力で技術的負債を粉砕しよう！<twemoji-flexed-biceps/>

---

# 今回のテーマ

- Vueを含めたWebアプリケーション開発のエコシステムなど
- Vue3系の機能紹介系
- AI活用術/技術的課題を乗り越えたお話

去年はVue2がEOLを迎える直前だったため、マイグレーションの話題がホットでしたが、今年はVueの最先端～将来の話が多かったです。
<br>
去年も同様でしたが、セッションが同時進行していくため、聴講できなかったセッションも多くあります。<span class="opacity-50">(<twemoji-star />が聴講したセッション)</span>

---

# Vueを含めたWebアプリケーション開発のエコシステムなど

- [Oxc - The JavaScript Oxidation Compiler](https://jjdlwtezpdclgxxagxpj.supabase.co/storage/v1/object/public/common_asset/archives/boshen.pdf)<twemoji-star />
- UnJS: The Missing Tools for the Modern Web
- [Anthony's Road to Open Source - Yak Shaving](https://talks.antfu.me/2024/vue-fes-japan/1)

---

# 機能紹介系(Vue/Vue Router/Pinia/Vite)

- [Vue Vapor: Reinvention](https://talks.sxzz.moe/2024-10-vue-fes-japan/1)
- [Vaporモードを大規模サービスに最速導入して学びを共有する](https://speakerdeck.com/kazukishimamoto/vapormodowoda-gui-mo-sabisunizui-su-dao-ru-sitexue-biwogong-you-suru)<twemoji-star />
- [Vue 3 と Svelte 5 のランタイムを比較する 〜技術を一段深く理解する〜](https://docs.google.com/presentation/d/1xvcDewSssDweawP3ZnkQi0L-1AjaOl5oD8YFiiZuk3A/edit#slide=id.p)
- [Trusted Types APIとVue.js](https://speakerdeck.com/lycorptech_jp/20241024a)<twemoji-star />
- [v-modelの歩みを振り返る](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-2)<twemoji-star />
- [Vue SFCのtemplateでTypeScriptの型を活用しよう](https://speakerdeck.com/tsukkee/vue-sfcnotemplatetetypescriptnoxing-wohuo-yong-siyou)<twemoji-star />
- [段階的なレンダリングを実装してUXを最大化するためのTips](https://speakerdeck.com/reibomaru/duan-jie-de-narentarinkuwoshi-zhuang-siteuxwozui-da-hua-surutamenotips)<twemoji-star />
- Vue.jsプロジェクトに出てくるeslintと仲良くなる
- [Async State Management with Vue Router](https://data-loaders.netlify.app/1)
- [Piniaの現状と今後](https://speakerdeck.com/waka292/pinianoxian-zhuang-tojin-hou)<twemoji-star />
- [Demystifying Vite Internals](https://speakerdeck.com/nozomuikuta/demystifying-vite-internals)
- [Vitest Browser Mode への期待](https://speakerdeck.com/odanado/vitest-browser-mode)

---

# 機能紹介系(Nuxt関連)

-  Gems of Nuxt: 8 Features Every Nuxt Developer Should Know!
- [Nuxt UI Pro、NuxtHub、Nuxt Scripts、Nuxtエコシステムをふんだんに利用して開発するコーポレートサイト](https://speakerdeck.com/shingangan/nuxt-ui-pro-nuxthub-nuxt-scripts-nuxtekosisutemuwohundannili-yong-sitekai-fa-surukoporetosaito-at-vue-fes-japan-2024)
- [Deep dive into Nuxt Server Components](https://speakerdeck.com/wattanx/deep-dive-into-nuxt-server-components)
- [Protocol BuffersとNuxt3で開発生産性を上げるためのスキーマファースト開発の紹介](https://speakerdeck.com/tokuda109/protocol-bufferstonuxt3dekai-fa-sheng-chan-xing-woshang-gerutamenosukimahuasutokai-fa-noshao-jie)
- [Nuxt × Vue Router の力を最大限を引き出す機能を紹介 ～Typed Pages, Nested Routes, Routes' Matching Syntax～](https://speakerdeck.com/ytr0903/nuxt-x-vue-router-noli-wozui-da-xian-niyin-kichu-suji-neng-woshao-jie)
- [Nuxtベースの「WXT」で開発用のChrome拡張を作成する](https://speakerdeck.com/moshi1121/nuxtbesuno-wxt-dechromekuo-zhang-wozuo-cheng-suru-vue-fes-2024-rantisetusiyon)

---

# AI活用術

- [AIとともに歩んだライブラリアップデートの道のり](https://speakerdeck.com/lmi/vue-fes-japan-2024-link-and-motivation)<twemoji-star />
- [Vueでサクッと作って試す：STUDIOでのプロトタイピング開発](https://speakerdeck.com/ryunosukeheaven/vue-desakututozuo-ru-studio-denopurototaipingukai-fa)<twemoji-star />
- [Vaporモードを大規模サービスに最速導入して学びを共有する](https://speakerdeck.com/kazukishimamoto/vapormodowoda-gui-mo-sabisunizui-su-dao-ru-sitexue-biwogong-you-suru)<twemoji-star />
  - 機能紹介系でも登場しましたが、Options API<light-icon icon="arrow-right" />Composition APIにAIを使ったそうです

---

# 技術的課題を乗り越えたお話

- [普通のエンジニアが頑張って30万行のNuxt3バージョンアップした話](https://speakerdeck.com/konkarin/vue-fes-japan-2024-nuxt3-version-up)
- [フロントエンドエンジニアのいない組織でVue.jsを導入するまで](https://speakerdeck.com/paycloud/arara_vue-fes-japan-2024)
- [VueとViteで作るUIコンポーネントライブラリ ~デザインシステムとプロダクトの理想的な分離を目指して~](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-1)<twemoji-star />
- [Vue.js、Nuxtの機能を使い、大量のコピペコードをリファクタリングする](https://speakerdeck.com/igayamaguchi/vue-dot-js-nuxtnoji-neng-woshi-i-da-liang-nokopipekodoworihuakutaringusuru)<twemoji-star />
- [2万ページのSSG運用における工夫と注意点](https://speakerdeck.com/chinen/vue-fes-japan-2024)
- [Vue3の一歩踏み込んだパフォーマンスチューニング 2024](https://speakerdeck.com/hal_spidernight/vue3no-bu-ta-miip-ndapahuomansutiyuningu2024)<twemoji-star />

--- 

# その他

- [IT未経験者をVue.jsで開発できるITコンサルタントに育てあげる秘訣 - フューチャーの新人研修の取り組み](https://speakerdeck.com/yut0naga1_fa/futures-new-employee-training)<twemoji-star />
- 同期する都市のキャンバス：Vue.jsによる大規模メディアインスタレーションの舞台裏
- [/←このスケジュール表に立ち向かうフロントエンド開発戦略](https://speakerdeck.com/nrslib/a-front-end-development-strategy-to-tackle-a-single-slash-schedule)
  - アフターパーティで発表されたモノ

---

# After Talk(10/29)

- [ts-morphで簡単に始めるAST操作](https://speakerdeck.com/aoseyuu/ast-manipulation-with-ts-morph)
- [Unlocking the potential of Nuxt Server Components](https://speakerdeck.com/wattanx/unlocking-the-potential-of-nuxt-server-components)
- [RadixとArk UIを併用したマルチフレームワーク対応デザインシステムの道はあるか](https://speakerdeck.com/konkarin/multi-framework-designsystem-with-arkui-and-radixui)
  - ありそうらしい

---

# After Night(10/30)

- [Claude vs GitHub Copilot - Vueのコード変換丸投げしてみた](https://speakerdeck.com/kazukishimamoto/claude-vs-github-copilot-vuenokodobian-huan-wan-tou-gesitemita)
- [Pinia Colada が実現するスマートな非同期処理](https://speakerdeck.com/naokihaba/pinia-colada-gashi-xian-surusumatonafei-tong-qi-chu-li)
  - TanStack Queryのような非同期状態管理ツールのお話[<logos-pinia />](https://pinia-colada.esm.dev/)
- Rust で初めての npm package 開発
- [初学者向けモダンフロントエンドとVue.jsを理解する](https://speakerdeck.com/tsukuha/chu-xin-zhe-ni-vue-dot-js-wo-jiao-eruniha)
- Potential of Vapor (仮)
- [ベイビーステップで実現！地図検索機能のVue2→3移行話](https://speakerdeck.com/codmoninc/achieving-baby-steps-transitioning-map-search-functionality-from-vue-2-to-vue-3)
- [VueでWebコンポーネントを作ってReactで使う](https://speakerdeck.com/bengo4com/20241030-cloudsign-vuefes-after-night)
  - フレームワークに依存しないWebコンポーネントを作るお話[<logos-lit />](https://lit.dev/)

---

# After Meetup(11/1)

- VitePressで見つけたアウトプット習慣
- [ReactからVueへの転向：思考の変化とアプローチの違い](https://speakerdeck.com/calm1205/vue-fes-after-party-shift-from-react-to-vue)
- [1つのtsxコンポーネントをVueとReact向けにビルドする](https://vue-fes-after-meetup-2024-ushironokos-projects.vercel.app)

---
layout: center
---

# 今回<logos-nuxt />などの話題についてはお話しません。

---
layout: center
---

# エコシステムのお話<mdi-leaf class="text-green" />

---
layout: two-cols
---

ビルドツールを例にとると、近年Webpackに代わる存在としてViteが急躍進

<v-click>

どんどん新しいツールが出てきている

</v-click>

<v-click>

<light-icon icon="arrow-down" />...が最初に登場したこれは何？

- [Oxc - The JavaScript Oxidation Compiler](https://jjdlwtezpdclgxxagxpj.supabase.co/storage/v1/object/public/common_asset/archives/boshen.pdf)

</v-click>

::right::

<div class="flex justify-center items-center h-full">
  <img class="px-10 size-auto" src="https://www.publickey1.jp/2023/stjs202206.png"/>
</div>

---
layout: iframe-right
url: 'https://oxc.rs/'
---

- Oxidation Compiler<span class="opacity-50 text-xs px-1">錆(Rust)/酸化(Oxidation)?</span>
- Rustで記述されたJavaScriptのツールチェイン
  - Parser
  - Linter
  - Resolver
  - Transformer🚧
  - Minifier🚧
  - Formatter🚧
  - Rolldown Bundler🚧
  - Nova JavaScript Engine🚧

機能が盛りだくさん

<v-click>

しかし、これらのツールはすでに色々あるのでは？

- Linter<light-icon icon="arrow-right" />ESLint<logos-eslint/>
- Transformer<light-icon icon="arrow-right" />Babel<logos-babel/>

</v-click>

---

# 既存ツールに対し、なぜこのようなものが開発されているのか

[Announcing VoidZero - Next Generation Toolchain for JavaScript](https://voidzero.dev/posts/announcing-voidzero-inc)

<div v-if="$clicks === 0">

> Over the years, many excellent tools have emerged to address the increasing scale and complexity of JavaScript applications. However, <span class="text-red">the ecosystem has always been fragmented: every application relies on a myriad of third-party dependencies</span>, and configuring them to work well together remains one of the most daunting tasks in the development cycle.

> As the author of one of the most widely used frontend frameworks, I’ve spent significant effort researching every layer of the JavaScript tooling stack, assembling hundreds of dependencies, and designing complex abstractions on top of them. The goal was always to give end users a cohesive, out-of-the-box development experience. These efforts eventually led to the creation of Vite in 2020.

> The trust the community has placed in Vite made me reflect deeply on its future. While Vite has greatly improved the high-level developer experience, internally, it still relies on various dependencies, with abstractions and workarounds to smooth over inconsistencies. Performance-wise, <span class="text-red">it remains bottlenecked by duplicated parsing and serialization costs across different tools, and it can't fully leverage native tooling like esbuild due to feature constraints and limited customizability.</span>

</div>
<div v-else>

> これまでの間、JavaScriptアプリケーションの規模や複雑さの増大に対応するために、多くの優れたツールが登場しました。しかし、<span class="text-red">エコシステムは常に断片的であり、各アプリケーションは無数のサードパーティの依存関係に依存しており</span>、それらをうまく組み合わせて動作させることは、開発プロセスの中でも最も難しい作業の一つであり続けています。

> 最も広く使われているフロントエンドフレームワークの一つの作者として、私はJavaScriptツールチェーンの各層を調査し、何百もの依存関係を組み合わせ、それらの上に複雑な抽象化を設計するために多大な努力を注ぎました。常に目指していたのは、エンドユーザーに対して統一された、即座に使える開発体験を提供することでした。この努力が最終的に2020年にViteの誕生へと繋がったのです。

> Viteに対するコミュニティの信頼を受け、私はその未来について深く考えるようになりました。Viteは高いレベルでの開発者体験を大幅に向上させましたが、内部では依然として多くの依存関係に頼っており、矛盾を解消するための抽象化や回避策が必要です。<span class="text-red">パフォーマンス面では、異なるツール間で重複するパースやシリアライゼーションによるボトルネックがあり、機能制約やカスタマイズ性の限界のため、esbuildのようなネイティブツールを十分に活用できていません。</span>

</div>

<v-clicks at="2">

- エンドユーザーに対して統一された開発体験を提供することを念頭に作られたViteは今やVue以外でも広く使われるように
- しかし...
  - 無数のサードパーティ性のライブラリに依存しており、一貫性を保つために色々無理をしている
  - 異なるツール間でのパースやシリアライズの重複によってパフォーマンスが頭打ちに

</v-clicks>

---
layout: center
---

<span class="font-bold text-emerald text-2xl">これはViteに限った話ではなく、JavaScriptのエコシステム全体の問題</span>

---
layout: iframe-right
url: 'https://voidzero.dev/'
clicks: 2
---

Evan達はこのような課題を解決するべく、VoidZeroを立ち上げて活動を始めました。

<div v-if="$clicks === 0">

> - <span class="text-red">Unified</span>: It should use the same AST, resolver, and module interop for all tasks, eliminating inconsistencies and reducing redundant parsing costs.
> - <span class="text-red">High Performance</span>: The foundational components should be written in a compile-to-native language and designed from the ground up for speed, unlocking more ambitious optimizations.
> - <span class="text-red">Composable</span>: Each component of the toolchain should be independently consumable, offering building blocks for advanced customization.
> - <span class="text-red">Runtime Agnostic</span>: The core of the toolchain should not be coupled to any specific JavaScript runtime so that developers can enjoy the same benefits across all environments.

</div>
<div v-else>

> - <span class="text-red">統一性</span>: すべてのタスクで同じAST、リゾルバ、およびモジュールインタロップを使用し、不整合を排除し、冗長なパースコストを削減するべきです。
> - <span class="text-red">高パフォーマンス</span>: 基本的なコンポーネントはネイティブにコンパイルされる言語で記述され、速度を最優先に設計されるべきで、より野心的な最適化を可能にします。
> - <span class="text-red">コンポーザブル</span>: ツールチェーンの各コンポーネントは独立して使用可能で、高度なカスタマイズのためのビルディングブロックを提供するべきです。
> - <span class="text-red">ランタイム非依存</span>: ツールチェーンのコアは特定のJavaScriptランタイムに依存せず、すべての環境で同じメリットを享受できるようにするべきです。

</div>

<v-click at="2">

Oxcとともに最初に登場したUnJSもおそらく同じ思想
- UnJS: The Missing Tools for the Modern Web

</v-click>

---

# Viteにおける課題

- 開発環境と本番環境で異なるビルドツール
  - 開発環境：esbuild<logos-esbuild/>
  - 本番環境：Rollup<logos-rollup/>
- esbuild(Go製)のパフォーマンスを最大限に活かせていない

先程出てきたRolldownも、先の課題を解決するために新たにRustで作成されているものです。
<br>
これによって差異がなくなる上に、パフォーマンスが非常に向上します。

<div class="flex justify-center">
  <img class="px-10 h-60" src='https://pbs.twimg.com/media/GaN_1qcbUAEHvj8?format=jpg'/>
</div>

---

# 時代はRust🦀

Oxcのツール群はメモリ効率やパフォーマンス、バンドルサイズで優位性があるRust製

||比較対象|速さ|互換性|
|---|---|---|---|
|Parser|swc<span class="opacity-50" style="font-size: 0.5em">←これもRust製ですが...</span>|3x|<mdi-check class="text-emerald"/>|
|Linter|ESLint|50~100x|一部|
|Resolver|enhanced-resolve|28x|<mdi-check class="text-emerald"/>|
|Transformer|swc/Babel|4x/40x|<mdi-check class="text-emerald"/>|
|Formatter|Prettier||<mdi-check class="text-emerald"/>|
|Rolldown Bundler|Rollup|100x|<mdi-check class="text-emerald"/>

<div v-click class="absolute transform">
  ちなみにWebPack互換の<a href="https://rspack.dev/">Rspack</a>もあり、フロントエンドエコシステムのRust化が進んでいます。
</div>

---
layout: center
---

<span class="text-5xl">次のVite6からこれらに置き換わっていきます</span>

---
layout: center
---

<span class="text-2xl">Viteと同様にOxcはWeb開発において広く使われていくことになるかもしれません。</span>

#### 余談1

このようなツールを統一しようとする思想はOxc以外にも[<logos-biomejs/>](https://biomejs.dev/blog/biome-v1-6/)(旧Rome)というものがありました
<br>
[RomeとOxcの立ち位置について](https://zenn.dev/cybozu_frontend/articles/thinking-about-oxc)

#### 余談2

RustでJavaScriptのパーサーを書くことに興味がある方は[こちら](https://oxc-project.github.io/javascript-parser-in-rust/ja/)

---
layout: center
---

少し思想的なお話...([Anthony's Road to Open Source - Yak Shaving](https://talks.antfu.me/2024/vue-fes-japan/1)より)

---
layout: iframe-right
url: 'https://talks.antfu.me/2024/vue-fes-japan/2'
---

<div class="flex justify-center items-center h-full">
  Anthony FuさんはVue Vite Nuxtのコアメンバーです。
  <br>
  OSS開発にあたってのマインドが興味深かったので紹介します。
  (発表スライドを一部そのまま掲載します)
</div>

---
layout: iframe
url: 'https://talks.antfu.me/2024/vue-fes-japan/5?clicks=2'
---

---
layout: iframe
url: 'https://talks.antfu.me/2024/vue-fes-japan/8?clicks=4'
---

---
layout: iframe
url: 'https://talks.antfu.me/2024/vue-fes-japan/7?clicks=8'
---

---
layout: iframe
url: 'https://talks.antfu.me/2024/vue-fes-japan/9?clicks=5'
---

---
layout: iframe
url: 'https://talks.antfu.me/2024/vue-fes-japan/10?clicks=18'
---

---
layout: center
---

Anthonyさんの場合はOSSを舞台としていますが、開発チームレベルにも活かせるマインドなのかなと思いました。

---
layout: center
---

# Vueの機能のお話<logos-vue />

---
layout: two-cols
---

# Vueの歩み

- Vue2
  - Options API
- Vue2.7
  - Composition API
- Vue3.3
  - TypeScript連携の強化
  - `defineSlots`など
- Vue3.4<span class="text-red">←イマココ</span>
  - `defineModel`など

::right::

<v-click>

- Vue3.5←最新はココ
  - メモリ効率<light-icon icon="trending-up" />(**-56%**)
  - Trusted Types API
  - `useTemplateRef`など
- Vue3.6
  - `Suspense`
  - Vaporモード(実験的)
  - さらなる最適化

</v-click>

<v-click>

ちなみにVue3.5のコードネームは
<br>
<div class="h-10 flex items-center">
  <span class="font-bold text-3xl text-rose">Tengen Toppa Gurren Lagann</span>
</div>
<br>
らしい

</v-click>

---
layout: center
---

# ...ほとんどComposition API/TypeScriptの話

---

- そもそもOptions APIはTypeScriptとの親和性が微妙
  - 内部的にめちゃくちゃに複雑なことをしなければならない
  - 様々な機能に対して型推論が完璧にはできていない

↓[Vueの公式](https://ja.vuejs.org/guide/extras/composition-api-faq.html#relationship-with-options-api)より

>ここ数年、多くのフロントエンドの開発者たちが TypeScript を取り入れ、より堅牢なコードを書き、より安心して変更を加えられるようにしていて、また IDE のサポートと共にすばらしい開発体験を提供してくれています。しかしながら、2013 年に Options API が生まれた当時、型推論の考慮がない状態でデザインされました。 Options API に型推論を取り入れるためには <span class="text-red">とてもありえない複雑な型定義</span>をしなければなりませんでした。これだけの努力をしても、 Options API の型推論は<span class="text-red">ミックスインや依存関係の注入により壊れてしまいます。</span>

---
layout: two-cols
---

- また、大規模開発になるほどコードを読むのがツライ
  - `data`<light-icon icon="arrows-horizontal" />`computed`<light-icon icon="arrows-horizontal" />`methods`が分離

<v-clicks depth="2">

- Vue2.6で満を持してのComposition APIサポート
  - 論理的関心の対象がコード上でまとまるように
  - 状態を持つ関数を再利用する仕組み(コンポーザブル)
    - ミックスインに頼らなくて良くなった
- このため、Options API<light-icon icon="arrow-right" />Composition APIの書き換えをするプロジェクトも多くある
- 実はこれは[ReactHooks](https://ja.vuejs.org/guide/extras/composition-api-faq#comparison-with-react-hooks)と似ている

</v-clicks>

::right::

<div class="flex justify-center items-center h-full">
  <img class="px-10 size-auto" src="https://ja.vuejs.org/assets/composition-api-after.ZXskY_32.png"/>
</div>

---

[Options APIでもコンポーザブルを使えるらしい。](https://ja.vuejs.org/guide/reusability/composables#using-composables-in-options-api)

````md magic-move {lines: true}

```ts {*|5-9|10-13}
import { useMouse } from './mouse.js'
import { useFetch } from './fetch.js'

export default {
  setup() {
    const { x, y } = useMouse()
    const { data, error } = useFetch('...')
    return { x, y, data, error }
  },
  mounted() {
    // setup() で公開したプロパティは `this` でアクセスできる
    console.log(this.x)
  }
  // ...他のオプション
}
```

````

---
layout: center
---

- Options APIは非推奨ではないが、今後Vueとして機能の強化がはかられていくのはComposition APIになりそう
- 上記の前提で、以下のようなお話をします
  - TypeScriptでこんなものが型推論できるようになった！
  - Composition APIでこんなことができる！
- 意外とまだ対応されていなかったものも結構あるという印象を持つかも🦆しれません

---
clicks: 1
---

# 講演で取り上げられていた機能を見てみる

Vueの機能を全部を追うことはできないので、講演であったものをベースに...
- マクロ/ヘルパー
  - [`defineSlots`](https://ja.vuejs.org/api/sfc-script-setup#defineslots)(3.3)
  - [`defineModel`](https://ja.vuejs.org/api/sfc-script-setup#definemodel)(3.4)
  - [`useTemplateRef`](https://ja.vuejs.org/api/composition-api-helpers#usetemplateref)(3.5)
  - [`Suspense`](https://ja.vuejs.org/guide/built-ins/suspense)(3.6)
- <span :class="$clicks > 0 && 'opacity-50'">Trusted Types API</span>
  - <span :class="$clicks > 0 && 'opacity-50'">XSS対策</span>
  - <span :class="$clicks > 0 && 'opacity-50'">テンプレート内での型安全なDOM操作</span>
- <span :class="$clicks > 0 && 'opacity-50'">Vaporモード</span>

---

- [`defineSlots`](https://ja.vuejs.org/api/sfc-script-setup#defineslots)(3.3)
  - Slotsの型付け
- <span class="opacity-50">[`defineModel`](https://ja.vuejs.org/api/sfc-script-setup#definemodel)(3.4)</span>
- <span class="opacity-50">[`useTemplateRef`](https://ja.vuejs.org/api/composition-api-helpers#usetemplateref)(3.5)</span>
- <span class="opacity-50">[`Suspense`](https://ja.vuejs.org/guide/built-ins/suspense)(3.6)</span>

````md magic-move {lines: true}

```vue
<script setup lang="ts">
const slots = defineSlots<{
  default: (props: { message: string }) => void
  header?: () => void
}>()
</script>

<template>
  <div>
    <header v-if="slots.header">
      <slot name="header"></slot>
    </header>
    <main>
      <slot :message="'Hello from slot!'"></slot>
    </main>
  </div>
</template>
```

````

---

- <span class="opacity-50">[`defineSlots`](https://ja.vuejs.org/api/sfc-script-setup#defineslots)(3.3)</span>
- [`defineModel`](https://ja.vuejs.org/api/sfc-script-setup#definemodel)(3.4)
  - 親<light-icon icon="arrows-horizontal" />子<light-icon icon="arrows-horizontal" />孫でデータを受け渡す(`v-model`)ときは子コンポーネントに煩雑な記述が必要だったが、簡潔に書けるように
- <span class="opacity-50">[`useTemplateRef`](https://ja.vuejs.org/api/composition-api-helpers#usetemplateref)(3.5)</span>
- <span class="opacity-50">[`Suspense`](https://ja.vuejs.org/guide/built-ins/suspense)(3.6)</span>

````md magic-move {lines: true}

```vue
<script setup>
// 子コンポーネントはデータの仲介役
// Options APIでも仲介役はmodelValueを記述してemitとしてと記述が煩雑...
import { defineProps, defineEmits, computed } from "vue";

const props = defineProps(["modelValue"]);
const emit = defineEmits(["update:modelValue"]);
const model = computed({
  get: () => props.modelValue,
  set: (inputted) => emit("update:modelValue", inputted)
});
</script>

<template>
  <input type="text" v-model="model" />
</template>
```

```vue
<script setup>
// defineModelで一発で済むように
const model = defineModel();
</script>

<template>
  <input type="text" v-model="model" />
</template>
```

```vue
<script setup>
// 引数に名前を入れてあげれば名前付きになる
const username = defineModel("username");
const age = defineModel("age");
</script>

<template>
  <input type="text" v-model="username" />
  <input type="number" v-model="age" />
</template>
```

````

---

- <span class="opacity-50">[`defineSlots`](https://ja.vuejs.org/api/sfc-script-setup#defineslots)(3.3)</span>
- <span class="opacity-50">[`defineModel`](https://ja.vuejs.org/api/sfc-script-setup#definemodel)(3.4)</span>
- [`useTemplateRef`](https://ja.vuejs.org/api/composition-api-helpers#usetemplateref)(3.5)
  - `ref`を自動で型推論
- <span class="opacity-50">[`Suspense`](https://ja.vuejs.org/guide/built-ins/suspense)(3.6)</span>

````md magic-move {lines: true}

```vue {*|5}
<script setup>
// ネイティブタグの例
import { useTemplateRef, onMounted } from 'vue'

const inputRef = useTemplateRef('input')
onMounted(() => {
  inputRef.value.focus()
})
</script>

<template>
  <input ref="input" />
</template>
```

```vue
<script setup lang="ts">
// カスタムコンポーネントの例
import { useTemplateRef } from 'vue'
import Foo from './Foo.vue'
import Bar from './Bar.vue'

type FooType = InstanceType<typeof Foo>
type BarType = InstanceType<typeof Bar>

const compRef = useTemplateRef<FooType | BarType>('comp')
</script>

<template>
  <component :is="Math.random() > 0.5 ? Foo : Bar" ref="comp" />
</template>
```

````

---

- <span class="opacity-50">[`defineSlots`](https://ja.vuejs.org/api/sfc-script-setup#defineslots)(3.3)</span>
- <span class="opacity-50">[`defineModel`](https://ja.vuejs.org/api/sfc-script-setup#definemodel)(3.4)</span>
- <span class="opacity-50">[`useTemplateRef`](https://ja.vuejs.org/api/composition-api-helpers#usetemplateref)(3.5)</span>
- [`Suspense`](https://ja.vuejs.org/guide/built-ins/suspense)(3.6)
  - 非同期コンポーネントが解決されるまでフォールバックを表示できる(`isLoading`等の状態変数を使わなくて良くなる)

````md magic-move {lines: true}

```vue
<script setup>
import AsyncComponent from './components/AsyncComponent.vue'
// 非同期コンポーネントとは以下のいずれか
// <script setup>にトップレベルawaitがあるもの
// async setup()と記述されているもの
</script>

<template>
  <Suspense>
    <template #default>
      <AsyncComponent />
    </template>
    <template #fallback>
      <span>Loading...</span>
    </template>
  </Suspense>
</template>
```

````

---
clicks: 1
---

# 講演で取り上げられていた機能を見てみる

- <span :class="$clicks > 0 && 'opacity-50'">関数系</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`defineSlots`](https://ja.vuejs.org/api/sfc-script-setup#defineslots)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`defineModel`](https://ja.vuejs.org/api/sfc-script-setup#definemodel)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`useTemplateRef`](https://ja.vuejs.org/api/composition-api-helpers#usetemplateref)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`Suspense`](https://ja.vuejs.org/guide/built-ins/suspense)</span>
- Trusted Types API
  - XSS対策
  - テンプレート内での型安全なDOM操作
- <span :class="$clicks > 0 && 'opacity-50'">Vaporモード</span>

---

# 今話題のXSS<mdi-security-lock class="text-yellow" />

- XSS(Cross-Site Scripting)
  - 攻撃者が、ターゲットユーザーに対して悪意のあるスクリプトを実行する攻撃
  - 脆弱性があると任意のスクリプトが実行されるので、なんでもアリ状態になってしまう
    - クッキーに保存されたセッションIDの盗み出し/固定化
    - クッキーに保存された個人情報の盗み出し
    - CSRFトークンの盗み出し
    - 画面改ざん
    - なりすまし
    - アカウント締め出し
  
---

# 今話題のXSS<mdi-security-lock class="text-yellow" />

<v-clicks depth="2" at="+0">

- いくつかタイプが有る
  - 反射型
    - URLのクエリパラメータなどでスクリプト受け取り、それがそのままレスポンスに反映されるときに実行される
    - 攻撃者が罠URLを踏ませる
  - 保存型
    - DBに保存されたスクリプトを表示する際に実行される
    - DBに保存されているので永続化している
  - DOM Based
    - 反射型と似ているが、サーバーを経由しないもの
    - 反射型と同様攻撃者が罠URLを踏ませる
    - ログに残りづらい

</v-clicks>

---

# 今話題のXSS<mdi-security-lock class="text-yellow" />

<v-clicks depth="2" at="+0">

- 対策
  - とにかく外部入力のコンテンツは信頼しない、必ずエスケープする
  - サーバーからのレスポンスをhtmlとして解釈しないようにする(`Content-Type: application/json;`)
    - ブラウザはhtmlが返るとそれをそのまま表示する

Vueの公式ページで、[Vueのセキュリティについての記事](https://ja.vuejs.org/guide/best-practices/security)があるので、一読したほうが良いかもしれません。

</v-clicks>


---
layout: iframe-right
url: 'https://caniuse.com/mdn-api_trustedtypes'
---

# Trusted Types API？

- ブラウザレベルでXSSを防ぐための[Web標準API](https://developer.mozilla.org/en-US/docs/Web/API/Trusted_Types_API)
  - HTTPSまたは`localhost`環境が対象
- <span class="text-red">処理済みであることを保証する型(TrustedType)</span>を導入し、DOM操作時に満たしていない場合はエラー
  - `innerHTML`
  - `outerHTML`など
  - 「型」とあるがJavaScriptでも利用可能
- 主にDOM Based XSSが対象
- Googleでは導入後にDOM Based XSSの報告が0になったらしい

<v-click>

- [<logos-lit />](https://lit.dev/)や[<logos-angular />](https://v17.angular.io/docs)では対応済み

</v-click>

---

# Vueの対応状況は？

- 2023年末に[RFC](https://github.com/vuejs/rfcs/discussions/614)が提出
- Vue3.5に含まれる形で2024/9にリリース
  - 新しすぎてVueにドキュメントがまだない(2024/10/25)
  - RFC提出した方(講演者)によると、`v-html`に対してこの仕組みを適用できるようになった

<v-click>

...はずなのですが、手元で試してもうまくいきませんでした(何も処理しなくてもエラーが表示されない)

</v-click>

---
clicks: 3
---

# とりあえず[使い方](https://web.dev/articles/trusted-types)

基本的な流れは、ポリシーを作成して、そのポリシーの使用宣言をします。

<div v-if="$clicks === 0">

- ポリシーを作成する
  - 例えば`myPolicy.createHTML()`で生成した文字列が`TrustedHTML`扱いになる

````md magic-move {lines: true}

```ts {*|2-5|8-}
const myPolicy = window.trustedTypes.createPolicy('my-policy', {
  createHTML: (unsafeValue) => unsafeValue.replace(/</g, '&lt;').replace(/>/g, '&gt;'),
  createURL:       (unsafe) => {/*..*/},
  createScriptURL: (unsafe) => {/*..*/},
  createScript:    (unsafe) => {/*..*/},
});

const evilScript = '<script>EvilScript</script>';
const elem = document.createElement('div');

elem.innerHTML = content; // コンソールエラー
elem.innerHTML = myPolicy.createHTML(evilScript); // OK
```

````

</div>
<div v-if="$clicks === 1">

- IISやNginxなどのWebサーバーでCSP(Content Security Policy)を設定する(使用宣言)
  - `vue`は必ず宣言します(おそらく`vue`内部で`innerHTML`等を使用している箇所があるため)

```
Content-Security-Policy: require-trusted-types-for 'script'; trusted-types vue my-policy
```

- または、index.htmlなどのmetaタグに記述する
  - 前者の方が一般的？

```html
<meta http-equiv="Content-Security-Policy" content="require-trusted-types-for 'script'; trusted-types vue my-policy">
```

</div>

<div v-if="$clicks > 1">

- この状態で`innerHTML`などを普通に使用しようとするとエラーになる(画面が真っ白になる)
  - 使用中のエスケープ処理をこれに置き換えていくこともできると思いますが、対策されていないところを踏むと真っ白になる...?
  - TypeScriptで静的に検出できると良いなと思いました

````md magic-move {lines: true}

```ts {*|*|*|8-}
const myPolicy = window.trustedTypes.createPolicy('my-policy', {
  createHTML: (unsafeValue) => escapeHTML(unsafeValue),
  createURL:       (unsafe) => {/*..*/},
  createScriptURL: (unsafe) => {/*..*/},
  createScript:    (unsafe) => {/*..*/},
});

const evilScript = '\\<script\\>EvilScript\\</script\\>';
const elem = document.createElement('div');

elem.innerHTML = content; // コンソールエラー
elem.innerHTML = myPolicy.createHTML(evilScript); // OK
```

````

</div>

---

# よくわからないところ

- ポリシーが複数されたときの動作
  - ポリシーが複数あっても、どれかで処理されたらTrustedTypeになる
  - そのため、よろしくないポリシーを設定してそれで`createHTML`してしまうと意味がない
    - <span class="opacity-50">`v-html`でうまく動かない件はここらへんと関連している...?</span>

````md magic-move {lines: true}

```ts {*|4-7,11}
const myPolicy = window.trustedTypes.createPolicy('my-policy', {
  createHTML: (unsafeValue) => escape(unsafeValue),
});
const badPolicy = window.trustedTypes.createPolicy('bad-policy', {
  createHTML: (unsafeValue) => unsafeValue,
});

const evilScript = '\\<script\\>EvilScript\\</script\\>';
const elem = document.createElement('div');

elem.innerHTML = badPolicy.createHTML(evilScript); // OKになってしまう
```

````

---
clicks: 2
---

# 講演で取り上げられていた機能を見てみる

- <span :class="$clicks > 0 && 'opacity-50'">関数系</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`defineSlots`](https://ja.vuejs.org/api/sfc-script-setup#defineslots)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`defineModel`](https://ja.vuejs.org/api/sfc-script-setup#definemodel)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`useTemplateRef`](https://ja.vuejs.org/api/composition-api-helpers#usetemplateref)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[`Suspense`](https://ja.vuejs.org/guide/built-ins/suspense)</span>
- <span :class="$clicks > 0 && 'opacity-50'">Trusted Types API</span>
  - <span :class="$clicks > 0 && 'opacity-50'">XSS対策</span>
  - <span :class="$clicks > 0 && 'opacity-50'">テンプレート内での型安全なDOM操作</span>
- Vaporモード<span class="text-red" v-click="2">←？</span>

---
layout: image
image: 'https://cdn.hashnode.com/res/hashnode/image/upload/v1695757332997/e2e526c6-1a25-419e-9222-f6dfecfca6d1.png'
---

---
layout: iframe
url: 'https://talks.sxzz.moe/2024-10-vue-fes-japan/5?clicks=5'
---

---
layout: iframe-right
url: 'https://speakerdeck.com/player/f34ec1469d5244b7a791f40fca66b41e?slide=15'
---

# 新たなレンダリング戦略

- Vue<logos-vue />やReact<logos-react />はレンダリング時にDOMを直接更新せず、仮想DOM(`VNode`のオブジェクトツリー)を通して管理している
  - 更新のたびにDOMツリー全体が再構築されることを防ぐため

<v-clicks>

もし仮想DOMを介さずにレンダリングできたら...

- レンダリングコスト<light-icon icon="trending-down" />
- ランタイムコード<light-icon icon="trending-down" />
- メモリ効率<light-icon icon="trending-up" />

</v-clicks>

---
layout: iframe-right
url: 'https://speakerdeck.com/player/f34ec1469d5244b7a791f40fca66b41e?slide=74'
---

<div class="flex justify-center items-center h-full">
  バンドルサイズ(コンポーネント数：130)
</div>

---
layout: iframe-right
url: 'https://speakerdeck.com/player/f34ec1469d5244b7a791f40fca66b41e?slide=107'
---

<div class="flex justify-center items-center h-full">
  初期描画(コンポーネント数：1000)
</div>

---
layout: iframe-right
url: 'https://speakerdeck.com/player/f34ec1469d5244b7a791f40fca66b41e?slide=110'
---

<div class="flex justify-center items-center h-full">
  更新描画(コンポーネント数：1000)
  <br>
  レンダリングとペイントがVaporオンのときに遅いのは、更新回数が多いかららしい
</div>

---

# Vaporモードを導入するには？

- Vueを更新してVaporモードをONにするだけ
  - Vue2<light-icon icon="arrow-right" />Vue3の破壊的変更の多さはEvanも言及しており、それが意識されていると思います
- element-plus<logos-element/>も対応

<v-click>

[Vue Vapor: Reinvention](https://talks.sxzz.moe/2024-10-vue-fes-japan/1)のスピーカーはelement-plusでよく出てくるこの方

<div class="flex justify-center">
  <iframe src="https://xlog.sxzz.moe/" class="h-72 w-96"/>
</div>

</v-click>

---

# 注意点

<v-clicks depth="2">

- Vaporモードは現在開発途中
- <span class="text-red">Composition API限定😢</span>
  - 講演された方は元々Options API(130コンポーネント)で構成されていたものを、AIを駆使して書き換えたそうです

</v-clicks>

<div class="flex justify-center" v-show="$clicks > 2 ">
  <iframe src="https://speakerdeck.com/player/f34ec1469d5244b7a791f40fca66b41e?slide=40" class="h-72 w-96"/>
</div>

---
layout: center
---

<span class="text-2xl">ちなみに元々仮想DOMを使用していない[<logos-svelte />](https://svelte.jp/)というフレームワークもあります。</span>
<br>
<span class="text-xl">噂によるとVaporモードではSvelteやReactのコンポーネントをインポートして普通に使えるらしい...</span>


---
layout: two-cols
---

# その他技術周りのお話し

- AIを活用した事例
  - 構文書き換え
    - [Vue3マイグレーション](https://speakerdeck.com/lmi/vue-fes-japan-2024-link-and-motivation)
    - Composition API
  - [テストコードの生成](https://speakerdeck.com/lmi/vue-fes-japan-2024-link-and-motivation)
  - Storybook自動生成
  - [プロトタイピング](https://speakerdeck.com/ryunosukeheaven/vue-desakututozuo-ru-studio-denopurototaipingukai-fa)
- <span :class="$clicks > 0 && 'opacity-50'">デザインとプロダクト</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[<logos-zeroheight/>](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-1)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[Figma<logos-figma/>](https://speakerdeck.com/igayamaguchi/vue-dot-js-nuxtnoji-neng-woshi-i-da-liang-nokopipekodoworihuakutaringusuru)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[<logos-storybook/>](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-1)</span>

::right::

<v-click hide>

以下も面白い講演内容でしたが細かい話になってしまうので割愛します

- リファクタリング系
  - [Vue.js、Nuxtの機能を使い、大量のコピペコードをリファクタリングする](https://speakerdeck.com/igayamaguchi/vue-dot-js-nuxtnoji-neng-woshi-i-da-liang-nokopipekodoworihuakutaringusuru)
    - Composition API
    - 責務ごとに細かく分けたら管理しやすくなった
    - デザイン部との連携
  - パフォーマンスチューニング系
  - [Vue3の一歩踏み込んだパフォーマンスチューニング 2024](https://speakerdeck.com/hal_spidernight/vue3no-bu-ta-miip-ndapahuomansutiyuningu2024)
    - キャッシュの活用、リアクティブシステムの手動制御
    - Vue3.5にしたら内部処理が最適されて<twemoji-thumbs-up />
  
</v-click>

---
layout: center
---

# [Aider](https://aider.chat/)を用いたVue3マイグレーション+Storybookの作成

---
layout: iframe
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=6'
---

---
layout: iframe-right
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=10'
---

<div class="flex justify-center items-center h-full">

- [Aider](https://aider.chat/)
  - 主に開発者向けの対話式CLI
  - Gitとの連携
    - リポジトリを読んでくれる
    - コミット、PR作成など
  - スクリプトによる自動化
- 以下の事例が紹介されていました
  - Vueの非推奨構文の書き換え
  - テストコード自動生成

</div>

---
layout: iframe-right
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=19'
---

# 非推奨構文の書き換え

今回は`slot-scope`<light-icon icon="arrow-right" />`v-slot`への書き換え
- プロンプトを与える
  - これをこんな感じに修正してほしいなど
- 行けそうだったらAiderに自分を自動化してもらう
  - ブランチ切って
  - 自分を実行して
  - pushして
  - PR作成

---
layout: iframe
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=22'
---

---
layout: iframe
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=23'
---

---
layout: iframe-right
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=29'
---

# テスト生成(Storybook)

- ChatGPTなどにテスト観点を考えてもらう
  - 使用する技術ややりたいことの目的を明示して
  - 評価観点を絞りながら
- <span class="text-red">**テストの結果をAider自身にフィードバックする仕組みを入れる**</span>
  - 完璧なモノを一発で出してくることを期待しない
- 行けそうだったらAiderに自分を自動化してもらう
  - ブランチ切って
  - 自分を実行して
  - pushして
  - PR作成

---
layout: iframe
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=31'
---

---
layout: iframe
url: 'https://speakerdeck.com/player/2b48eef29f194ab6bd5b2df9f10850f7?slide=32'
---

---

# 他にも

- Storybookの自動生成とVRT<twemoji-check-mark-button />
- `script setup`への移行<twemoji-check-mark-button />
- ESLint errorの修正<twemoji-check-mark-button />
- TypeScript移行(未検証)
- PRを自動で直す(未検証)

Github Copilot<logos-github-copilot/>に期待したい部分でもあるような...<light-icon icon="arrow-right" />

---
layout: center
---

# [<logos-claude/>](https://claude.ai/)を使ったOptions API<light-icon icon="arrow-right" />Composition API

After Nightのスライドを見てみたものです。

---
layout: iframe-right
url: 'https://speakerdeck.com/player/a8b8aa83e01b4de6b59b777b2b43cccb?slide=26'
---

<div class="flex justify-center items-center h-full">

- [<logos-claude/>](https://claude.ai/)
  - 2023年に公開された汎用的な対話型AIアシスタント
  - Claude Sonnetエンジン
- 以下の事例が紹介されていました
  - Options API<light-icon icon="arrow-right" />Composition API変換のパフォーマンス
    - Atomic Designでの例
  - Github Copilot Chat<logos-github-copilot/>との比較

</div>

---

# Options API<light-icon icon="arrow-right" />Composition APIにおいては...

||Claude|Github Copilot Chat|
|:---:|:---:|:---:|
|atoms|<twemoji-thumbs-up/>|<twemoji-thumbs-up/>|
|molecules|<twemoji-thumbs-up/>|ヌケモレがある|
|organisms|<twemoji-thumbs-up/>|応答制限に引っかかる<twemoji-crying-face/>|

Github Copilot Chatにあまり複雑なことを求めないほうが良さそう。
リアルタイムで&少ない入力に対して補助をする、あくまでCopilotとして使う。
<br>
長文の指示はClaudeの方が良さそう。Vuex<light-icon icon="arrow-right" />Piniaの書き換えも行けたらしい。

<v-click>

最近ではCopilotのエンジンとしてClaude Sonnetが選択できるようになっているので、用途に合わせて使ってみるのも良さそう。

</v-click>

---

# ところで...

AIとかではなく、Composition APIに変換するツールがあるらしい...

- [Composition API Converter](https://wattanx-converter.vercel.app/)

---
layout: center
---

# [<logos-claude/>](https://claude.ai/)を使ったプロトタイピング

---
layout: iframe
url: 'https://speakerdeck.com/player/734f1e95fd8641edb2a7b2cd3116daf7?slide=12'
---

---
layout: center
---

- 先ほども出てきた[<logos-claude/>](https://claude.ai/)はプロトタイピング
- 雑に指示を出せばそれっぽいコード+**イメージ**も出してくれる
  - ライブラリやフレームワークも考えてくれる<light-icon icon="arrow-right" />

---
layout: iframe
url: 'https://speakerdeck.com/player/734f1e95fd8641edb2a7b2cd3116daf7?slide=18'
---

---
layout: center
---

実アプリケーションに完全にマッチするものを出すのは難しいかもしれませんが、文字通りプロトタイピングには良さそう。

---
clicks: 1
---

# その他技術周りのお話し

- <span :class="$clicks > 0 && 'opacity-50'">AIを活用した事例</span>
  - <span :class="$clicks > 0 && 'opacity-50'">構文書き換え([Vue3マイグレーション](https://speakerdeck.com/lmi/vue-fes-japan-2024-link-and-motivation)、Composition API)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[テストコードの生成](https://speakerdeck.com/lmi/vue-fes-japan-2024-link-and-motivation)</span>
  - <span :class="$clicks > 0 && 'opacity-50'">Storybook自動生成</span>
  - <span :class="$clicks > 0 && 'opacity-50'">[プロトタイピング](https://speakerdeck.com/ryunosukeheaven/vue-desakututozuo-ru-studio-denopurototaipingukai-fa)</span>
- デザインとプロダクト
  - [<logos-zeroheight/>](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-1)
  - [Figma<logos-figma/>](https://speakerdeck.com/igayamaguchi/vue-dot-js-nuxtnoji-neng-woshi-i-da-liang-nokopipekodoworihuakutaringusuru)
  - [<logos-storybook/>](https://speakerdeck.com/igayamaguchi/vue-dot-js-nuxtnoji-neng-woshi-i-da-liang-nokopipekodoworihuakutaringusuru)

<div v-if="$clicks === 1" class="opacity-50">

<light-icon icon="arrow-up" />の話題は弁護士ドットコム株式会社さんの[講演](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-1)を参考にしています。
講演資料以外に[こちらの記事](https://note.com/yoshiba03/n/n16eb382c2817)も参考にしています。

</div>

---
layout: two-cols
---

[<logos-zeroheight/>](https://zeroheight.com/)

スタイルガイド・ドキュメントの作成ツール

- デザインの設計を司る(デザイントークン)
  - 役割・目的・手順を記述
  - ステータスの使い分け
  - Do/Don'tの例
- 後述のFigmaで設定したカラーやタイポグラフィを連携可能
- 色やタイポグラフィをSass変数として書き出すこともできる

::right::

<div class="flex justify-center items-center h-full">
  <img class="px-2 size-auto" src="https://assets.st-note.com/img/1650420484150-hSM43kpHge.png"/>
</div>

---
layout: two-cols
---

[Figma<logos-figma/>](https://www.figma.com/ja-jp/)

UIデザインやワイヤーフレームの作成が可能なクラウドベースのデザイン(プロトタイピング)ツール

- 画面のデザインや画面遷移を表現する
  - zeroheightへのインポートも可能
- UIライブラリのプラグインをサポート
- リアルタイムで共同編集が可能

::right::

<div class="flex justify-center items-center h-full">
  <img class="px-2 size-auto" src="https://cdn.clipkit.co/tenants/591/item_images/images/000/055/091/large/ac8c22b7-a0fe-4ab1-9a18-28a1774b9d27.gif?1715930735"/>
</div>

---
layout: two-cols
---

[<logos-storybook/>](https://storybook.js.org/)

UIコンポーネントにフォーカスした管理ツール

- UIコンポーネントのドキュメント化
  - propsなどの状態のバリエーションのカタログ化
- コンポーネントのテスト
  - ビジュアルテスト
  - アクセシビリティテスト
- UIワークフローの自動化
  - CIステップとしてテストの自動化、レビュー
  - [<logos-chromatic/>](https://www.chromatic.com/)

::right::

<div class="flex justify-center items-center h-full">
  <img class="px-2 size-auto" src="https://storage.googleapis.com/zenn-user-upload/ac7ddb6dc1d7-20221227.png"/>
</div>

---

# これらの関係と目的

- zeroheightでスタイルガイドを定める&Figmaでデザイン(画面やコンポーネント)を作成する
  - どちらかといえばデザイナーが頑張る領域
- StorybookでFigmaで設計したコンポーネントの実装を管理し、テストやプレビューを行う
  - どちらかといえばエンジニアが頑張る領域
- 様々な立場の人がこれらを確認し、デザインに対する共通認識を持つ

<v-click>

[こちらの記事](https://note.com/yoshiba03/n/n16eb382c2817)より引用...

> - コンポーネントの定義・用途が明確に定められている。
> - デザインルールなどの情報は、誰でもわかる場所に明記されている。
> - デザインルールなどの情報は、常に最新化されており、全員が認知している状態である。

</v-click>

---

# デザインをプロダクトに落とし込むときの課題

- しかし、プロダクトの成長や開発チーム体制等の要因で課題が出てくることも...
  - Storybookの肥大化
  - プロダクトをまたいだデザインの管理
    - デザインシステムの横展開
  - デザインの意図に対する実装者の理解不足
    - variantやカラーパレットの意図
    - アプリケーション共通で使われるコンポーネントなのか、共通化するべきか

---
layout: center
---

# 取り組み①(システムとして)

- デザインシステムのコンポーネントをライブラリ化
  - Storybookの分離
  - プロダクトを横断して使えるように

---
layout: iframe
url: 'https://speakerdeck.com/player/687a08786b3b48d89efd1fb7daa09dc0?slide=25'
---

---
layout: iframe
url: 'https://speakerdeck.com/player/687a08786b3b48d89efd1fb7daa09dc0?slide=26'
---

---
layout: center
---

# 取り組み②(開発体制として)

- Figma<light-icon icon="arrow-right" />実装の前に認識合わせのフェーズを設置
  - デザインの意図の認識共有
  - コンポーネント指向

---
layout: iframe
url: 'https://speakerdeck.com/player/38e14879cd874059b67ff0bf9942b793?slide=25'
---

---
layout: center
---

新規プロダクトといったレベルでなくとも、新機能に対してどのようなデザインコンセプトであるのか、について部門を横断して共通認識を持てるような仕組み/体制があると良いと思いました。

---

# まとめ

- フロントエンドのエコシステムは更に進化し続ける
  - 進むRust化
- Vue自身もどんどん便利に
  - 新機能
  - Vaporモード
- Composition API + TypeScriptが主流に
  - Vue自身の強化もこれを前提にしたものになっていきそう
- AI活用がアツい
- デザイン<light-icon icon="arrow-right" />プロダクトの連携・管理
- <span class="text-red">最近OSS活動で燃え尽きる方がﾁﾗﾁﾗ出てきているらしいので、OSS活動に興味がある人大募集中らしいです</span>

---

# 学習サイト

- Vue自体の仕組みをもっと知りたい→[ChibiVue](https://ubugeeei.github.io/chibivue/)
- Vite自体の仕組みをもっと知りたい→[ChibiVite](https://nozomuikuta.github.io/chibivite/)

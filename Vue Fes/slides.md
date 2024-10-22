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

# [Slidev](https://sli.dev/)を使ってスライドを作成してみています

<div v-click class="absolute transform">
  マークダウンベース+TailwindCSSの形式でスタイリングが可能
  <br>
  pdfやpptxに変換可能
</div>

---
layout: image-right
image: 'https://pbs.twimg.com/media/GaOMcVQbUAEards?format=jpg'
---

# 握力で技術的負債を粉砕しよう！💪

---

# 今回のテーマ

- Vueを含めたJavaScriptの将来像など
- 機能紹介系
- 技術的課題を乗り越えたお話

去年も同様でしたが、セッションが同時進行していくため、聴講できなかったセッションも多くあります。

---

# Vueを含めたJavaScriptの将来像など

- Oxc - The JavaScript Oxidation Compiler⭐
- UnJS: The Missing Tools for the Modern Web
- [Anthony's Road to Open Source - Yak Shaving](https://talks.antfu.me/2024/vue-fes-japan/1)

---

# 機能紹介系

- Gems of Nuxt: 8 Features Every Nuxt Developer Should Know!
- [Demystifying Vite Internals](https://speakerdeck.com/nozomuikuta/demystifying-vite-internals)
- Async State Management with Vue Router
- [Vue Vapor: Reinvention](https://talks.sxzz.moe/2024-10-vue-fes-japan/1)
- [Vaporモードを大規模サービスに最速導入して学びを共有する](https://speakerdeck.com/kazukishimamoto/vapormodowoda-gui-mo-sabisunizui-su-dao-ru-sitexue-biwogong-you-suru)⭐
- Piniaの現状と今後⭐
- [Vue3の一歩踏み込んだパフォーマンスチューニング 2024](https://speakerdeck.com/hal_spidernight/vue3no-bu-ta-miip-ndapahuomansutiyuningu2024)⭐

---

# 機能紹介系

- Trusted Types APIとVue.js⭐
- [v-modelの歩みを振り返る](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-2)⭐
- [Vue SFCのtemplateでTypeScriptの型を活用しよう](https://speakerdeck.com/tsukkee/vue-sfcnotemplatetetypescriptnoxing-wohuo-yong-siyou)⭐
- [Vue 3 と Svelte 5 のランタイムを比較する 〜技術を一段深く理解する〜](https://docs.google.com/presentation/d/1xvcDewSssDweawP3ZnkQi0L-1AjaOl5oD8YFiiZuk3A/edit#slide=id.p)
- [Deep dive into Nuxt Server Components](https://speakerdeck.com/wattanx/deep-dive-into-nuxt-server-components)
- [Vitest Browser Mode への期待](https://speakerdeck.com/odanado/vitest-browser-mode)
- Protocol BuffersとNuxt3で開発生産性を上げるためのスキーマファースト開発の紹介
- Nuxt × Vue Router の力を最大限を引き出す機能を紹介 ～Typed Pages, Nested Routes, Routes' Matching Syntax～
- Vue.jsプロジェクトに出てくるeslintと仲良くなる


---

# 技術的課題を乗り越えたお話

- [普通のエンジニアが頑張って30万行のNuxt3バージョンアップした話](https://speakerdeck.com/konkarin/vue-fes-japan-2024-nuxt3-version-up)
- フロントエンドエンジニアのいない組織でVue.jsを導入するまで
- [VueとViteで作るUIコンポーネントライブラリ ~デザインシステムとプロダクトの理想的な分離を目指して~](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-1)⭐
- [AIとともに歩んだライブラリアップデートの道のり](https://speakerdeck.com/lmi/vue-fes-japan-2024-link-and-motivation)⭐
- [Vue.js、Nuxtの機能を使い、大量のコピペコードをリファクタリングする](https://speakerdeck.com/igayamaguchi/⭐vue-dot-js-nuxtnoji-neng-woshi-i-da-liang-nokopipekodoworihuakutaringusuru)
- [段階的なレンダリングを実装してUXを最大化するためのTips](https://speakerdeck.com/reibomaru/duan-jie-de-narentarinkuwoshi-zhuang-siteuxwozui-da-hua-surutamenotips)⭐
- [2万ページのSSG運用における工夫と注意点](https://speakerdeck.com/chinen/vue-fes-japan-2024)

--- 

# その他/未聴講のため不明

- IT未経験者をVue.jsで開発できるITコンサルタントに育てあげる秘訣 - フューチャーの新人研修の取り組み⭐
- [Vueでサクッと作って試す：STUDIOでのプロトタイピング開発](https://speakerdeck.com/ryunosukeheaven/vue-desakututozuo-ru-studio-denopurototaipingukai-fa)⭐
- Nuxtベースの「WXT」で開発用のChrome拡張を作成する
- 同期する都市のキャンバス：Vue.jsによる大規模メディアインスタレーションの舞台裏
- Nuxt UI Pro、NuxtHub、Nuxt Scripts、Nuxtエコシステムをふんだんに利用して開発するコーポレートサイト

---
layout: center
---

# エコシステムのお話

---
layout: center
---

# 最初に登場したOxcとは

---
layout: iframe-right
url: 'https://oxc.rs/'
---

- Oxidation Compiler
- Rustで記述されたJavaScriptのツールチェイン
  - Parser
  - Linter
  - Resolver
  - Transformer🚧
  - Minifier🚧
  - Formatter🚧
  - Rolldown Bundler🚧
  - Nova JavaScript Engine🚧

---

# なぜこのようなものが開発されているのか

[Announcing VoidZero - Next Generation Toolchain for JavaScript](https://voidzero.dev/posts/announcing-voidzero-inc)

> Over the years, many excellent tools have emerged to address the increasing scale and complexity of JavaScript applications. However, the ecosystem has always been fragmented: every application relies on a myriad of third-party dependencies, and configuring them to work well together remains one of the most daunting tasks in the development cycle.

> As the author of one of the most widely used frontend frameworks, I’ve spent significant effort researching every layer of the JavaScript tooling stack, assembling hundreds of dependencies, and designing complex abstractions on top of them. The goal was always to give end users a cohesive, out-of-the-box development experience. These efforts eventually led to the creation of Vite in 2020.

<v-clicks>

- フロントエンド開発のエコシステムは進化を続けているが課題を抱えている
  - 無数のサードパーティ性のライブラリに依存しており、一貫性を保つために色々無理をしている
  - 異なるツール間でのパースやシリアライズの重複によってパフォーマンスが頭打ちに
- **これはJavaScriptのエコシステム全体の問題**

</v-clicks>

---
layout: iframe-right
url: 'https://voidzero.dev/'
---

# 

Evan達はこのような課題を解決するべく、VoidZeroを立ち上げて活動を始めました

> - Unified: It should use the same AST, resolver, and module interop for all tasks, eliminating inconsistencies and reducing redundant parsing costs.
> - High Performance: The foundational components should be written in a compile-to-native language and designed from the ground up for speed, unlocking more ambitious optimizations.
> - Composable: Each component of the toolchain should be independently consumable, offering building blocks for advanced customization.
> - Runtime Agnostic: The core of the toolchain should not be coupled to any specific JavaScript runtime so that developers can enjoy the same benefits across all environments.

---

# Viteが抱えている課題

- 開発環境と本番環境で異なるビルドツール
  - 開発環境：esbuild
  - 本番環境：Rollup

先程出てきたRolldownは、上記の課題を解決するために、新たにRustで作成されているものです。
<br>
これによって差異がなくなる上に、パフォーマンスが非常に向上します。

<div class="flex justify-center">
  <img class="px-10 h-60" src='https://pbs.twimg.com/media/GaN_1qcbUAEHvj8?format=jpg'/>
</div>

---

# 時代はRust

メモリ効率やパフォーマンス、バンドルサイズで優位性があるRustに...

||比較対象|速さ|互換性|
|---|---|---|---|
|Parser|swc<span class="opacity-50" style="font-size: 0.4em">←これもRust製ですが...</span>|3x|✅|
|Linter|ESlint|50~100x|一部|
|Resolver|enhanced-resolve|28x|✅|
|Transformer|Babel|40x|✅|
|Formatter|Prettier||✅|
|Rolldown Bundler|Rollup|100x|✅

<div v-click class="absolute transform">
  ちなみにWebPack互換の<a href="https://rspack.dev/">Rspack</a>もあり、フロントエンドエコシステムのRust化が進んでいます。
</div>

---
layout: center
---

# 次のVite6からこれらに置き換わっていきます

---
layout: center
---

# Vueのお話

- Vue3.5について
- Vaporモード

---

# Vueの歩み

- Vue2
  - Options API
- Vue2.7
  - Composition API
- Vue3.3
  - TypeScript連携の強化
- Vue3.4←イマココ
  - `defineModel`
- Vue3.5←最新はココ
  - Trusted Types API
- Vue3.6
  - Vaporモード(実験的)
  - より良いパフォーマンス

---

# 便利そうな機能

- Trusted Types API
  - XSS対策
  - テンプレート内での型安全なDOM操作
- `defineModel`
  - v-modelのカスタム定義
- `slot`の型安全化

---

# Vaporモード？

---
layout: iframe
url: 'https://talks.sxzz.moe/2024-10-vue-fes-japan/5?clicks=4'
---

---
layout: center
---

# その他技術周りのお話し

---

# その他技術周りのお話し

- デザインシステムとプロダクトの分離
  - Zeroheight
- AIを活用した事例
  - Composition API/TypeScriptへの書き換え
  - プロトタイピング

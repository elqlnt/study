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
  表示制御にVueのディレクティブが使用可能
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
- Vue3系の機能紹介系
- AI活用術/技術的課題を乗り越えたお話

去年はVue2がEOLを迎える直前だったため、マイグレーションの話題がホットでしたが、今年はVueの最先端～将来の話が多かったです。
<br>
去年も同様でしたが、セッションが同時進行していくため、聴講できなかったセッションも多くあります。<span class="opacity-50">(⭐が聴講したセッション)</span>

---

# Vueを含めたJavaScriptの将来像など

- [Oxc - The JavaScript Oxidation Compiler](https://jjdlwtezpdclgxxagxpj.supabase.co/storage/v1/object/public/common_asset/archives/boshen.pdf)⭐
- UnJS: The Missing Tools for the Modern Web
- [Anthony's Road to Open Source - Yak Shaving](https://talks.antfu.me/2024/vue-fes-japan/1)

---

# 機能紹介系

- Gems of Nuxt: 8 Features Every Nuxt Developer Should Know!
- [Demystifying Vite Internals](https://speakerdeck.com/nozomuikuta/demystifying-vite-internals)
- [Async State Management with Vue Router](https://data-loaders.netlify.app/1)
- [Vue Vapor: Reinvention](https://talks.sxzz.moe/2024-10-vue-fes-japan/1)
- [Vaporモードを大規模サービスに最速導入して学びを共有する](https://speakerdeck.com/kazukishimamoto/vapormodowoda-gui-mo-sabisunizui-su-dao-ru-sitexue-biwogong-you-suru)⭐
- [Piniaの現状と今後](https://speakerdeck.com/waka292/pinianoxian-zhuang-tojin-hou)⭐
- [Vaporモードを大規模サービスに最速導入して学びを共有する](https://speakerdeck.com/kazukishimamoto/vapormodowoda-gui-mo-sabisunizui-su-dao-ru-sitexue-biwogong-you-suru)⭐

---

# 機能紹介系

- Trusted Types APIとVue.js⭐
- [v-modelの歩みを振り返る](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-2)⭐
- [Vue SFCのtemplateでTypeScriptの型を活用しよう](https://speakerdeck.com/tsukkee/vue-sfcnotemplatetetypescriptnoxing-wohuo-yong-siyou)⭐
- [Vue 3 と Svelte 5 のランタイムを比較する 〜技術を一段深く理解する〜](https://docs.google.com/presentation/d/1xvcDewSssDweawP3ZnkQi0L-1AjaOl5oD8YFiiZuk3A/edit#slide=id.p)
- [Deep dive into Nuxt Server Components](https://speakerdeck.com/wattanx/deep-dive-into-nuxt-server-components)
- [Vitest Browser Mode への期待](https://speakerdeck.com/odanado/vitest-browser-mode)
- [Protocol BuffersとNuxt3で開発生産性を上げるためのスキーマファースト開発の紹介](https://speakerdeck.com/tokuda109/protocol-bufferstonuxt3dekai-fa-sheng-chan-xing-woshang-gerutamenosukimahuasutokai-fa-noshao-jie)
- [Nuxt × Vue Router の力を最大限を引き出す機能を紹介 ～Typed Pages, Nested Routes, Routes' Matching Syntax～](https://speakerdeck.com/ytr0903/nuxt-x-vue-router-noli-wozui-da-xian-niyin-kichu-suji-neng-woshao-jie)
- Vue.jsプロジェクトに出てくるeslintと仲良くなる


---

# AI活用術/技術的課題を乗り越えたお話

- [普通のエンジニアが頑張って30万行のNuxt3バージョンアップした話](https://speakerdeck.com/konkarin/vue-fes-japan-2024-nuxt3-version-up)
- [フロントエンドエンジニアのいない組織でVue.jsを導入するまで](https://speakerdeck.com/paycloud/arara_vue-fes-japan-2024)
  - 聴講していませんが面白そうだったのでちゃんと見てみます
- [VueとViteで作るUIコンポーネントライブラリ ~デザインシステムとプロダクトの理想的な分離を目指して~](https://speakerdeck.com/bengo4com/20241019-cloudsign-vuefesjapan2024-1)⭐
- [AIとともに歩んだライブラリアップデートの道のり](https://speakerdeck.com/lmi/vue-fes-japan-2024-link-and-motivation)⭐
- [Vue.js、Nuxtの機能を使い、大量のコピペコードをリファクタリングする](https://speakerdeck.com/igayamaguchi/⭐vue-dot-js-nuxtnoji-neng-woshi-i-da-liang-nokopipekodoworihuakutaringusuru)
- [段階的なレンダリングを実装してUXを最大化するためのTips](https://speakerdeck.com/reibomaru/duan-jie-de-narentarinkuwoshi-zhuang-siteuxwozui-da-hua-surutamenotips)⭐
- [2万ページのSSG運用における工夫と注意点](https://speakerdeck.com/chinen/vue-fes-japan-2024)
- [Vue3の一歩踏み込んだパフォーマンスチューニング 2024](https://speakerdeck.com/hal_spidernight/vue3no-bu-ta-miip-ndapahuomansutiyuningu2024)⭐

--- 

# その他/未聴講のため不明

- IT未経験者をVue.jsで開発できるITコンサルタントに育てあげる秘訣 - フューチャーの新人研修の取り組み⭐
- [Vueでサクッと作って試す：STUDIOでのプロトタイピング開発](https://speakerdeck.com/ryunosukeheaven/vue-desakututozuo-ru-studio-denopurototaipingukai-fa)⭐
- Nuxtベースの「WXT」で開発用のChrome拡張を作成する
- 同期する都市のキャンバス：Vue.jsによる大規模メディアインスタレーションの舞台裏
- [Nuxt UI Pro、NuxtHub、Nuxt Scripts、Nuxtエコシステムをふんだんに利用して開発するコーポレートサイト](https://speakerdeck.com/shingangan/nuxt-ui-pro-nuxthub-nuxt-scripts-nuxtekosisutemuwohundannili-yong-sitekai-fa-surukoporetosaito-at-vue-fes-japan-2024)
- [/←このスケジュール表に立ち向かうフロントエンド開発戦略](https://speakerdeck.com/nrslib/a-front-end-development-strategy-to-tackle-a-single-slash-schedule)
  - アフターパーティで発表されたモノ

---
layout: center
---

# エコシステムのお話<mdi-leaf class="text-green" />

---
layout: center
---

# いきなりですが、最初に登場したOxcについて...

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

- エンドユーザーに対して統一された開発体験を提供することを念頭に作られたViteは、今やVue以外でも広く使われるように
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

> - Unified: It should use the same AST, resolver, and module interop for all tasks, eliminating inconsistencies and reducing redundant parsing costs.
> - High Performance: The foundational components should be written in a compile-to-native language and designed from the ground up for speed, unlocking more ambitious optimizations.
> - Composable: Each component of the toolchain should be independently consumable, offering building blocks for advanced customization.
> - Runtime Agnostic: The core of the toolchain should not be coupled to any specific JavaScript runtime so that developers can enjoy the same benefits across all environments.

</div>
<div v-else>

> - 統一性: すべてのタスクで同じAST、リゾルバ、およびモジュールインタロップを使用し、不整合を排除し、冗長なパースコストを削減するべきです。
> - 高パフォーマンス: 基本的なコンポーネントはネイティブにコンパイルされる言語で記述され、速度を最優先に設計されるべきで、より野心的な最適化を可能にします。
> - コンポーザブル: ツールチェーンの各コンポーネントは独立して使用可能で、高度なカスタマイズのためのビルディングブロックを提供するべきです。
> - ランタイム非依存: ツールチェーンのコアは特定のJavaScriptランタイムに依存せず、すべての環境で同じメリットを享受できるようにするべきです。

</div>


---

# Viteにおける課題

- 開発環境と本番環境で異なるビルドツール
  - 開発環境：esbuild
  - 本番環境：Rollup
- esbuild(Go製)のパフォーマンスを最大限に活かせていない

先程出てきたRolldownも、先の課題を解決するために新たにRustで作成されているものです。
<br>
これによって差異がなくなる上に、パフォーマンスが非常に向上します。

<div class="flex justify-center">
  <img class="px-10 h-60" src='https://pbs.twimg.com/media/GaN_1qcbUAEHvj8?format=jpg'/>
</div>

---

# 時代はRust🦀

Oxcのツール群はメモリ効率やパフォーマンス、バンドルサイズで優位性があるRust製...

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

# 🍢

---
layout: center
---

<span class="text-5xl">次のVite6からこれらに置き換わっていきます</span>

---
layout: center
---

<span class="text-2xl">また、Viteと同様にOxcはWeb開発において広く使われていくことになるかもしれません</span>

---
layout: center
---

# Vue自身のお話<logos-vue />

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
  - メモリ効率<light-icon icon="trending-up" />
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

# ...Composition API+TypeScriptの話しかない

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
  <img class="px-10 h-80" src="https://ja.vuejs.org/assets/composition-api-after.ZXskY_32.png"/>
</div>

---
layout: center
---

- Options APIは非推奨ではないが、今後Vueとして機能の強化がはかられていくのはComposition APIになりそう
- 上記の前提で、以下のようなお話をします
  - TypeScriptの型推論がよくなった！
  - Composition APIでこんなことができる！
- 意外と対応されていないものも結構あるという印象を持つかも🦆しれません

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
// OptionsAPIでも仲介役はmodelValueを記述してemitとしてと記述が煩雑...
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

````md

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

# Trusted Types API？

最近過ぎて情報があまりない...

---
layout: iframe-right
url: 'https://github.com/vuejs/rfcs/discussions/614'
---

# VueのRFC

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
layout: center
---

# Vaporモード？

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
- element-plusにも対応

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
  - このあとにAIを活用した書き換えのお話もします

</v-clicks>

---

# その他技術周りのお話し

---

# その他技術周りのお話し

- AIを活用した事例
  - Composition API/TypeScriptへの書き換え
  - プロトタイピング
- デザインシステムとプロダクトの分離
  - Zeroheight
- リファクタリング
- パフォーマンスチューニング

---

# Composition APIに変換するツールがあるらしい...

[Composition API Converter](https://wattanx-converter.vercel.app/)

---

# まとめ

- フロントエンドのエコシステムは更に進化し続ける
  - 進むRust化
- Vue自身もどんどん便利に
- Composition API + TypeScriptが主流に
  - Vue自身の強化もこれを前提にしたものになっていきそう
- 最近OSS活動で燃え尽きるがﾁﾗﾁﾗ出てきているらしいので、OSS活動に興味がある人大募集中らしいです

---

# 学習サイト

- Vue自体の仕組みをもっと知りたい→[ChibiVue](https://ubugeeei.github.io/chibivue/)
- Vite自体の仕組みをもっと知りたい→[ChibiVite](https://nozomuikuta.github.io/chibivite/)

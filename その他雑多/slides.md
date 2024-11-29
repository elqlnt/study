---
theme: light-icons
title: プログラムはなぜ動くのか
drawings:
  persist: false
transition: fade
mdc: true
overviewSnapshots: true
---

<div class="flex flex-col justify-center items-center">
  <div class="text-6xl font-bold" >
    プログラムはなぜ動くのか
  </div>
  <div class="text-4xl mb-10" >
    第11回
  </div>
  <div class="text-xl" >
    2024/12/3 江袋 叡
  </div>
</div>

---

# アセンブリ言語からプログラムの本当の姿を知る

- 今回やること
  - C言語の基本的な機能がアセンブリでどのように実現されているかを知る
- 今回の目標
  - プログラムの生の動きを知ることで、問題解決のアプローチを広げる
  - 自動車の仕組みを知ることで、燃費良く<twemoji-evergreen-tree />運転できるようなイメージ

---

# ウォーミングアップ

1. アセンブリ言語において、ネイティブコードの命令の前に、その機能を表す英語の略称を付けたものを何と呼ぶ？
   - <v-click><span class="text-teal-500" v-text="'ニーモニック'"/></v-click>
2. アセンブリ言語のソースコードをネイティブコードに変換することを何と呼ぶ？
   - <v-click><span class="text-teal-500" v-text="'アセンブル'"/></v-click>
3. ネイティブコードをアセンブリ言語のソースコードに逆変換することを何と呼ぶ？
   - <v-click><span class="text-teal-500" v-text="'逆アセンブル'"/></v-click>
4. アセンブリ言語のソースファイルの拡張子は何？
   - <v-click><span class="text-teal-500" v-text="'.asm/.s'"/></v-click>
5. アセンブリ言語のプログラムにおけるセクションとは何？
   - <v-click><span class="text-teal-500" v-text="'プログラムを構成する命令やデータをまとめたグループ'"/></v-click>
6. アセンブリ言語のジャンプ命令は何のために使われる？
   - <v-click><span class="text-teal-500" v-text="'プログラムの流れを任意のアドレスに移す'"/></v-click>

---

# ネイティブコード・アセンブリ言語・高級言語の関係

| 言語                                                              | 特徴                                                                                                                                         | 例                                                              |
| ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| ネイティブコード                                                  | ハードウェアに直接実行可能                                                                                                                   | `0x89, 0xC8`                                                    |
| <span v-show="$clicks > 0" class='text-red'>アセンブリ言語</span> | <span :class="$clicks > 0 ? 'text-red' : 'text-transparent'">ネイティブコードと1対1対応<br>ニーモニックによって人の目でもわかりやすく</span> | <span v-show="$clicks > 0" class='text-red'>`mov eax, 1`</span> |
| 高級言語(C言語など)                                               | プログラマにとって扱いやすい                                                                                                                 | `int main() { return 0; }`                                      |

ネイティブコードは人間が理解するにはあまりにも厳しい。
...が何とか理解したい。

<v-click>

1対1の対応関係を表すために、個々のネイティブコードに機能を表す略語を付ける手法が考案された。<span class="text-red" v-text="'(ニーモニック)'"/>

また、これを使用する言語を<span class="text-red" v-text="'アセンブリ言語'"/>と呼ぶ。

</v-click>

---

# ネイティブコード・アセンブリ言語・高級言語の関係

- ネイティブコードとアセンブリ言語は1対1対応なので、相互に変換が可能。
- C言語などは1対1対応ではないので、このような変換は難しい。
  - ただし、コンパイルオプションを指定することでアセンブリ言語を出力することができる。
  - BCC32の場合は`-S`オプション

<div class="flex justify-center mt-20">
```mermaid {scale: 1.2}
graph LR
  A[アセンブリ言語] -->|アセンブル| B[ネイティブコード]
  B -->|逆アセンブル| A
```
</div>

---

# アセンブリを出力してみる

```sh
# 適当なC言語のプログラムをコンパイルしてアセンブリを出力
bcc32c -c -O1 -S hello.c
```

- `-c`オプション: コンパイルのみ(リンクはしない)
- `-O1`オプション: 最適化レベル1
- `-S`オプション: アセンブリを出力

<v-click>

こうすると`.s`や`.asm`といった拡張子のアセンブリが生成される。

</v-click>

---
layout: two-cols
---

# アセンブリ言語の基本

次のコードを題材に...

<div class="mr-5">

```c
// 2つの引数の加算結果を返す関数
int AddNum(int a, int b) {
  return a + b;
}

// AddNum関数を呼び出す関数
int Myfunc() {
return AddNum(123,456);
}
```

</div>

::right::

```asm {}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"
  .globl  _AddNum
  .align  16, 0x90      # @AddNum
_AddNum:
# BB#0:
  movl 8(%esp), %eax
  addl 4(%esp), %eax
  ret
  .def _Myfunc;
  .scl 2;
  .type 32;
  .endef
  .globl _Myfunc
  .align 16, 0x90      # @Myfunc
_Myfunc:
# BB#0:
  subl $8, %esp
  movl $456, 4(%esp)
  movl $123, (%esp)
  calll _AddNum
  addl $8, %esp
  ret
```

---
layout: two-cols
---

<div class="mr-5">

````md magic-move {lines: true}
```asm {*|11-13,22-27|1-8,14-19|6}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"
  .globl  _AddNum
  .align  16, 0x90      # @AddNum
_AddNum:
# BB#0:
  movl 8(%esp), %eax
  addl 4(%esp), %eax
  ret
  .def _Myfunc;
  .scl 2;
  .type 32;
  .endef
  .globl _Myfunc
  .align 16, 0x90      # @Myfunc
_Myfunc:
# BB#0:
  subl $8, %esp
  movl $456, 4(%esp)
  movl $123, (%esp)
  calll _AddNum
  addl $8, %esp
  ret
```
````

</div>

::right::

- アセンブリはネイティブコードと1対1対応と述べたが、次の要素で構成されている
  - <span :class="$clicks == 2 && 'opacity-50'" v-text="'ネイティブコードに変換される命令'"/>
  - <span :class="$clicks == 1 && 'opacity-50'" v-text="'アセンブラに対する命令(疑似命令)'"/>

---
layout: two-cols
---

<div class="mr-5">

````md magic-move {lines: true}
```asm {*|11,12,22-27|1-8,14-19}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"
  .globl  _AddNum
  .align  16, 0x90      # @AddNum
_AddNum:
# BB#0:
  movl 8(%esp), %eax
  addl 4(%esp), %eax
  ret
  .def _Myfunc;
  .scl 2;
  .type 32;
  .endef
  .globl _Myfunc
  .align 16, 0x90      # @Myfunc
_Myfunc:
# BB#0:
  subl $8, %esp
  movl $456, 4(%esp)
  movl $123, (%esp)
  calll _AddNum
  addl $8, %esp
  ret
```
````

</div>

::right::

- アセンブリはネイティブコードと1対1対応と述べたが、次の要素で構成されている
  - ネイティブコードに変換される命令
  - アセンブラに対する命令(疑似命令)
- 記法も(大きく異なるわけではないが)2種類ある
  - AT&T記法: GNUアセンブラで使われる
    - BCC32はこちら
  - Intel記法: Intelアセンブラで使われる

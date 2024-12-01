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
    - 実際にアセンブリのコードを見ながら
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

これを使用する言語を<span class="text-red" v-text="'アセンブリ言語'"/>と呼ぶ。

</v-click>

---

# ネイティブコード・アセンブリ言語・高級言語の関係

- ネイティブコードとアセンブリ言語は1対1対応なので、相互に変換が可能。
- C言語などは1対1対応ではないので、特に逆変換が難しい。
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

<div class="flex h-80 items-center" v-if="$clicks == 0">
  <div class="flex-col w-70">

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

  <div class="flex-col w-30 ml-5" v-if="$clicks == 0">
    コンパイル<light-icon icon="arrow-right" />
  <div class="text-[0.5rem]">

  - <span class="text-red">AT&T記法</span>: GNUアセンブラ
    - `%`、`$`がある
    - オペランド順序
    - コメント表記
  - Intel記法: Intelアセンブラ

  </div>
  </div>
</div>

<div v-if="$clicks > 0">

- <span :class="$clicks != 1 && $clicks != 2 && 'opacity-50'" >アセンブラに対する命令(疑似命令)</span>
  - <span :class="$clicks != 1 && $clicks != 2 && $clicks != 3 && 'opacity-50'" >セクションは大事らしい</span>
- <span :class="$clicks != 1 && $clicks != 4 && 'opacity-50'" v-text="'ネイティブコードに変換される命令'"/>

</div>

::right::

````md magic-move {lines: true}
```asm {*|*|1-8,14-19|6|11-13,22-27}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"  # 以降を_TEXTでexecute,readできる
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

---
layout: two-cols
clicks: 2
---

# アセンブリの構成要素

<div class="text-xs">

- それぞれの命令は<span class="text-red">オペコード オペランド</span>の構文で表現される
- まずコードはメモリにロードされ、実行時にCPUが内部のレジスタを駆使して演算する

</div>

<div v-if="$clicks==1" class="text-xs mr-2">
  <div>

  |オペコード|オペランド|機能|
  |--|---|---|
  |`movl`|A,B|AをBに格納する|
  |`addl`|A,B|B+AをBに格納する|
  |`subl`|A,B|B-AをBに格納する|
  |`calll`|L|アドレスLにある関数を呼ぶ|
  |`ret`|(なし)|処理を関数の呼び出し元に戻す|

  </div>
  <div class="text-xs text-right">

  ※末尾の`l`はlongでデータやアドレスが32bitであることを表す

  </div>
</div>

<div v-if="$clicks==2" class="text-[0.5em] mr-2">
  <div>

  |レジスタ名|呼称|役割|
  |--|---|---|
  |`eax`|アキュムレータ|演算に使用|
  |`ebx`|ベースレジスタ|アドレスを格納|
  |`ecx`|カウントレジスタ|ループ回数をカウント|
  |`edx`|データレジスタ|データを格納|
  |`esi`|ソースインデックス|データ転送元のアドレスを格納|
  |`edi`|ディスティネーションインデックス|データ転送先のアドレスを格納|
  |`ebp`|ベースポインタ|データ格納領域の起点のアドレスを格納|
  |`esp`|スタックポインタ|スタック最上位のデータのアドレスを格納|

  </div>
  <div class="text-xs text-right">

  ※他にも正負やオーバーフローを表すフラグレジスタやOS専用のものがある
  <br>
  ※`e`は32bitを表す、16bitは`e`がない、64bitは`r`がつく

  </div>
</div>

::right::

````md magic-move {lines: true}
```asm {11-13,22-27|11-13,22-27|11-12,22-24,26}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"  # 以降を_TEXTでexecute,readできる
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

---
layout: center
---

# それぞれの具体的な処理を見てみる<twemoji-backhand-index-pointing-right />

---
layout: two-cols
---

# `movl A,B`を題材に基礎編

<div class="text-sm">

- レジスタやメモリに値を格納する
  - 最もよく使われる
- 記法
  - カッコなし`$456`
    - 値がそのまま値として処理される
    - ここでは`456`という値
  - カッコ付き`(%esp)`
    - カッコ内がアドレス値として解釈されその値に対して処理する
    - ここでは`%esp`に格納されている値
  - カッコ前の数値付き`4(%esp)`
    - 上と似ているがカッコ前の数値を後続のアドレスに加算して処理する
    - ここでは`%esp+4`に格納されている値
    - <light-icon icon="arrow-right" />こんな感じになっているのは、次の関数呼び出しとも関連

</div>

<div v-if="$clicks==1" class="text-sm">

- `456`という値を

</div>

::right::

````md magic-move {lines: true}
```asm {11,23,24}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"  # 以降を_TEXTでexecute,readできる
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

---
layout: two-cols
---

# 関数呼び出し(呼出の仕組み)

<div  v-if="$clicks==0">

- 関数呼び出しを実現するにはスタックが利用される

![スタック](./stack.svg)

</div>
<div  v-if="$clicks==1">

- `calll`すると、自動的に次の命令がスタックに積まれる

![スタック1](./stack1.svg)

</div>

<div  v-if="$clicks==2">

- 呼び出された側で`ret`すると、`esp`レジスタが指す戻り先のアドレスを読み出すことで復帰する

![スタック1](./stack1.svg)

</div>

::right::

````md magic-move {lines: true}
```asm {9-13,20,25|20,25-26|13,26}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"  # 以降を_TEXTでexecute,readできる
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

---
layout: two-cols
---

# 関数呼び出し(引数の仕組み)

<div  v-if="$clicks==0">

- これもスタックを使う

![スタック](./stack2.svg)

</div>

<div  v-if="$clicks==1">

- 引数で使用する分のメモリを確保する
- 渡す引数を格納する

![スタック](./stack3.svg)

</div>

<div  v-if="$clicks==2">

- 呼び出された側では、スタックに積まれた値について演算
  - 演算はアキュムレータ(`eax`)で行う
  - BCC22では関数の戻り値はココに格納する決まり

![スタック](./stack4.svg)

</div>

<div  v-if="$clicks==3">

- 処理が終わったらスタックをクリーンアップする
  - 第五章

![スタック](./stack2.svg)

</div>

::right::

````md magic-move {lines: true}
```asm {9-13,20-26|22-24|9-12|26}
  .file   "hello.c"
  .def    _AddNum;
  .scl    2;
  .type   32;
  .endef
  .section _TEXT, "xr"  # 以降を_TEXTでexecute,readできる
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

---
layout: two-cols
---

# グローバル変数・ローカル変数の仕組み

- 以下を確認してみる
  - <span :class="$clicks == 2 && 'opacity-50'" >ローカル変数はスタック上のみで管理されていること</span>
  - <span :class="$clicks == 1 && 'opacity-50'" >グローバル変数は<light-icon icon="arrow-up" />とは別の管理がされていること</span>
<div class="mr-5">

```c
// グローバル変数の宣言
int x = 123;
int y = 456;

// グローバル変数とローカル変数を使う関数
int Myfunc() {
  int a;
  a = x + y;
  return a;
}
```

</div>

::right::

<div class="flex items-center justify-center h-full">

````md magic-move {lines: true}
```asm {1-2,4,6-8,12-18|6-8|14-18}
  .section _TEXT, "xr"  # 命令セクション
_Myfunc:
  pushl %ebp
  movl  %esp, %ebp
  pushl %eax
  movl  _x, %eax
  addl  _y, %eax
  movl  %eax, -4(%ebp)
  movl  -4(%ebp), %eax
  addl  $4, %esp
  popl  %ebp
  ret

  .section _DATA, "w"  # データセクション
_x:
  .long 123
_y:
  .long 456
```
````

</div>


---

# 繰り返し処理の仕組み

---

# 条件分岐の仕組み

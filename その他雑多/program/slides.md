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
  - アセンブリの基本的な構文を学ぶ
  - 実際にアセンブリのコードを見ながら、C言語の基本的な機能がどのように実現されているかを知る
    - 加減算
    - 変数
    - 関数呼び出し
    - ループ処理
    - 条件分岐
- 今回の目標
  - プログラムの生の動きを知ることで、問題解決のアプローチの幅を広げる
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

1対1の対応関係を表すために、個々のネイティブコードに機能を表す略語<span class="text-red" v-text="'(ニーモニック)'"/>を付ける手法が考案された。

これを使用する言語を<span class="text-red" v-text="'アセンブリ言語'"/>と呼ぶ。

</v-click>

---

# ネイティブコード・アセンブリ言語・高級言語の関係

- ネイティブコードとアセンブリ言語は1対1対応なので、相互に変換が可能。
- C言語などは1対1対応ではないので、特に逆変換が難しい。
  - コンパイルオプションを指定することでアセンブリ言語を出力することができる。
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

````md magic-move {lines: true}
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
````

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

以下に分類される

- <span :class="$clicks != 1 && $clicks != 2 && 'opacity-50'" >アセンブラに対する命令(疑似命令)</span>
  - <span :class="$clicks != 1 && $clicks != 2 && 'opacity-50'" >頭に`.`がついているモノ</span>
  - <span :class="$clicks != 1 && $clicks != 2 && $clicks != 3 && 'opacity-50'" >セクションは大事らしい</span>
- <span :class="$clicks != 1 && $clicks != 4 && 'opacity-50'">ネイティブコードに変換される命令</span><br><span v-if="$clicks == 4">主にこちらを見ていきます</span>

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
_AddNum:                # 2つの引数の加算結果を返す関数
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
_Myfunc:               # _AddNumを呼び出す
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
  |`movl`|A, B|AをBに格納する|
  |`addl`|A, B|B+AをBに格納する|
  |`subl`|A, B|B-AをBに格納する|
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
  |<span class="text-blue-500">`eax`</span>|<span class="text-blue-500">アキュムレータ</span>|<span class="text-blue-500">演算に使用</span>|
  |`ebx`|ベースレジスタ|アドレスを格納|
  |`ecx`|カウントレジスタ|ループ回数をカウント|
  |`edx`|データレジスタ|データを格納|
  |`esi`|ソースインデックス|データ転送元のアドレスを格納|
  |`edi`|ディスティネーションインデックス|データ転送先のアドレスを格納|
  |`ebp`|ベースポインタ|データ格納領域の起点のアドレスを格納|
  |<span class="text-blue-500">`esp`</span>|<span class="text-blue-500">スタックポインタ</span>|<span class="text-blue-500">スタック最上位のデータのアドレスを格納</span>|

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
_AddNum:                # 2つの引数の加算結果を返す関数
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
_Myfunc:               # _AddNumを呼び出す
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

# 具体的な処理を見てみる<twemoji-backhand-index-pointing-right />

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
    - ここでは`%esp+4`に格納されている値<br><light-icon icon="arrow-right" />こんな感じになっているのは、次の関数呼び出しとも関連

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
_AddNum:                # 2つの引数の加算結果を返す関数
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
_Myfunc:               # _AddNumを呼び出す
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

- 呼び出された側で`ret`すると、`esp`レジスタが指す戻り先のアドレスを読み出して復帰する

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
_AddNum:                # 2つの引数の加算結果を返す関数
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
_Myfunc:               # _AddNumを呼び出す
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

- スタック領域に引数で使用する分のメモリを確保する
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
_AddNum:                # 2つの引数の加算結果を返す関数
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
_Myfunc:               # _AddNumを呼び出す
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

- <span :class="$clicks == 2 && 'opacity-50'" >ローカル変数はスタック上のみで管理されている</span>
  - <span :class="$clicks == 2 && 'opacity-50'" >スタック領域にあるので、後の別処理で上書きされる</span>
- <span :class="$clicks == 1 && 'opacity-50'" >グローバル変数はデータセクションとして別途管理されている</span>

<div class="mr-5">

````md magic-move {at:1, lines: true}
```c {*|7|2-3}
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
````

</div>

::right::

<div class="flex items-center justify-center h-full">

````md magic-move {at:1, lines: true}
```asm {1-2,4,6-8,12-18|4,6-8|14-18}
  .section _TEXT, "xr"  # 命令セクション
_Myfunc:
  pushl %ebp
  movl  %esp, %ebp
  pushl %eax
  movl  _x, %eax
  addl  _y, %eax
  movl  %eax, -4(%ebp)  # -4(%ebp)がa
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
layout: two-cols
---

# 繰り返し処理`for`の仕組み

- 比較命令とジャンプ命令で実現している
  - C言語では`i < 10`で比較しているところが<br>`10 <= i`で比較していたりと微妙に異なる

<div class="mt-5 mr-5" v-if="$clicks == 0">

````md magic-move {lines: true}
```c
void MySub() {
  // 動作確認用に呼び出されるだけ
}

void MyFunc() {
  int i;
  for (i = 0; i < 10 ; i++) {
    Mysub();
  }
}
```
````

</div>

<div v-if="$clicks==1" class="text-xs mr-2">
  <div>

  |オペコード|オペランド|機能|
  |--|---|---|
  |<span class="text-blue-500">`cmpl`</span>|A, B|AとBを比較する|
  |<span class="text-blue-500">`jge`</span>|L|A<=BならLにジャンプ|
  |`jle`|L|A>=BならLにジャンプ|
  |<span class="text-blue-500">`jmp`</span>|L|Lにジャンプ|

  </div>
  <div class="text-right">

  ※`jle`は次出てくる

  </div>
</div>

::right::

<div class="flex items-center justify-center h-full">

````md magic-move {lines: true}
```asm {*|*}
                        # ebpにはespの値が格納されている
  movl  $0, -4(%ebp)    # ループカウンタi
LBB1_1:                 # ループ処理のラベル
  compl $10, -4(%ebp)   # iの大きさを比較して
  jge   LBB1_4          # 10を超えていたらループを抜ける
  calll _MySub
  movl  -4(%ebp), %eax  # iをeaxにいれて
  addl  $1, %eax        # 1加算して
  movl  %eax, -4(%ebp)  # ebpに戻す
  jmp   LBB_1
LBB1_4
```
````

</div>

---
layout: two-cols
---

# 条件分岐`if`の仕組み

- これも比較命令とジャンプ命令で実現している
  - C言語では`a > 100`で比較しているところが<br>`100 <= a`で比較していたりと微妙に異なる

<div class="mt-5 mr-5">

````md magic-move {lines: true}
```c
void MySubA() {
  // 動作確認用に呼び出されるだけ
}
void MySubB() {
  // 動作確認用に呼び出されるだけ
}

void MyFunc() {
  int a = 123;

  if (a > 100) {
    MysubA();
  } else {
    MysubB();
  }
}
```
````

</div>

::right::

<div class="flex items-center justify-center h-full">

````md magic-move {lines: true}
```asm {*}
                        # ebpにはespの値が格納されている
  movl  $123, -4(%ebp)  # aに123をいれる
  compl $100, -4(%ebp)  # 100と比較して
  jle   LBB2_2          # 100以下だったらLBB2_2へ
  calll _MySubA         # falseならこちら
  jmp   LBB2_3
LBB2_2:
  calll _MySubB
LBB2_3
```
````

</div>

---

# なぜ条件分岐の順番がC言語と異なるのか

- `for`
> C言語では`i < 10`で比較しているところが`10 <= i`で比較していたりと微妙に異なる
- `if`
> C言語では`a > 100`で比較しているところが`100 <= a`で比較していたりと微妙に異なる

`jge`や`jle`が、<span class="text-red">条件が真ならジャンプする</span>ことしかできないため

<div class="flex w-full">

<div class="w-1/2">

<span class="text-sm">`else`にジャンプするために`jle`で比較している<light-icon icon="arrow-right" /></span>
<br>
<span class="inline-block opacity-50 text-[0.6rem] text-right w-full">`calll _MySubA`と`calll _MySubB`を入れ替えるのはできない？</span>

</div>

<div class="w-1/2">

````md magic-move {lines: true}
```asm {*}
                        # ebpにはespの値が格納されている
  movl  $123, -4(%ebp)  # aに123をいれる
  compl $100, -4(%ebp)  # 100と比較して
  jle   LBB2_2          # 100以下だったらLBB2_2へ
  calll _MySubA         # falseならこちら
  jmp   LBB2_3
LBB2_2:
  calll _MySubB
LBB2_3
```
````

</div>

</div>

---

# まとめ

- ネイティブコードとアセンブリ言語は1対1対応
- アセンブリのコードを見ながらC言語との対応を学んだ
  - ネイティブコードの処理はごく基本的なもの
    - 基本的な操作
      - 値の格納
      - 加減算
      - 関数呼び出し
      - 比較
      - ジャンプ
    - スタックを活用
  - ローカル変数/グローバル変数の管理方法の違い

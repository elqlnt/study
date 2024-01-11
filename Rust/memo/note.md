# Rust

- mozillaが支援しているOSSのプログラミング言語
- C++の代わりとなる言語として開発された
- 処理速度が速い
  - メモリ空間を効率的に使えるように設計されている
  - C言語に並ぶ速度
- 並行処理が可能
  - マルチスレッドを可能にするための厳密なルールがある
- 安全性が高い
  - 所有権と行った概念により、メモリ管理が安全

## 記法

### 変数

- 変数は`let`で宣言
- 基本的に型は推論される
  - どうしてもされない場合は、明示的に追加できる
- 同じ変数名に複数回割当できる

```rust
fn main() {
    // x の型を推論
    let x = 13;
    println!("{}", x);

    // x の型を指定
    let x: f64 = 3.14159;
    println!("{}", x);

    // 宣言の後で初期化（あまり使われません）
    let x;
    x = 0;
    println!("{}", x);
}
```

- 変数の変更は重要な概念
- 可変と不変でキーワードを分ける

```rust
let mut x = 42;
let y = 44;
```

### 型

|型|例|
|:--:|:--:|
|bool|`true`|
|符号なし整数型|`u8, u32, u64, u128`|
|符号付き整数型|`i8, i32, i64, i128`|
|ポインタサイズ整数型|`usize, isize`<br>メモリ内のインデックスとサイズを返す|
|浮動小数点型|`f32, f64`|
|タプル型|スタック上の固定された値の組を渡す|
|配列型|コンパイル時に長さが決まるコレクション|
|スライス型|実行時に長さが決まるコレクション|
|`str`(string slice)|実行時に長さが決まるテキスト|

- 型変換は`as`を用いる

```rust
let a = 13u8;
let b = 7u32;
let c = a as u32 + b;
```

- 定数は`const`で宣言できる
- 変数とは異なり、明示的な型指定が必要
- 大文字のスネークケースを使用する

### 配列

- 配列のインデックスは`usize`型？

```rust
let nums: [i32; 3] = [1, 2, 3];
println!("{:?}", nums);
println!("{}", nums[1]);
```

### 関数

- 関数名にはスネークケースを使用する

``` rust
fn add(x: i32, y: i32) -> i32 {
    return x + y;
}
```

- 複数の値を返すには、値をタプルで返す

```rust
fn swap(x: i32, y: i32) -> (i32, i32) {
    return (y, x);
}

fn main() {
    // 戻り値をタプルで返す
    let result = swap(123, 321);
    println!("{} {}", result.0, result.1);

    // タプルを2つの変数に分解
    let (a, b) = swap(result.0, result.1);
    println!("{} {}", a, b);
}
```

- 関数に戻り値の方が指定されていない場合、`unit`と呼ばれるからのタプルを返す

```rust
fn make_nothing() -> () {
    return ();
}

// 戻り値は () と推論
fn make_nothing2() {
    // この関数は戻り値が指定されないため () を返す
}

fn main() {
    let a = make_nothing();
    let b = make_nothing2();

    // 空を表示するのは難しいので、
    // a と b のデバッグ文字列を表示
    println!("a の値: {:?}", a);
    println!("b の値: {:?}", b);
}
```

### if

- カッコがないだけで普通

```rust
if x < 42 {
    println!("42 より小さい");
} else if x == 42 {
    println!("42 に等しい");
} else {
    println!("42 より大きい");
}
```

- ループは`loop, while`など
- `break`で値を返すことができる

```rust
let mut x = 0;
let y = loop {
    x += 1;
    if x == 42 {
        break 6;
    }
}

while x != 42 {
    x += 1;
}
```

- その中でも`for`はかなり強化されているらしい
- イテレータを簡単に作成できる

```rust
for x in 0..5 {
    println!("{}", x);
}

for x in 0..=5 {
    println!("{}", x);
}
```

### match

- `switch`の上位互換として、`match`がある
- `switch`は文、`match`は式

```rust
match x {
    0 => {
        println!("found zero");
    }
    // 複数の値にマッチ
    1 | 2 => {
        println!("found 1 or 2!");
    }
    // 範囲にマッチ
    3..=9 => {
        println!("found a number 3 to 9 inclusively");
    }
    // マッチした数字を変数に束縛
    matched_num @ 10..=100 => {
        println!("found {} number between 10 to 100!", matched_num);
    }
    // どのパターンにもマッチしない場合のデフォルトマッチが必須
    _ => {
        println!("found something else!");
    }
}
```

- 関数から値を返す際は、`;`をつけなければそれが返される

```rust
fn example() -> i32 {
    let x = 42;
    // Rust の三項式
    let v = if x < 42 { -1 } else { 1 };
    println!("if より: {}", v);

    let food = "ハンバーガー";
    let result = match food {
        "ホットドッグ" => "ホットドッグです",
        // 単一の式で値を返す場合、中括弧は省略可能
        _ => "ホットドッグではありません",
    };
    println!("食品の識別: {}", result);

    let v = {
        // ブロックのスコープは関数のスコープから分離されている
        let a = 1;
        let b = 2;
        a + b
    };
    println!("ブロックより: {}", v);

    // Rust で関数の最後から値を返す慣用的な方法
    v + 4
}
```

### 構造体

```rust
struct SeaCreature {
    // String は構造体である。
    animal_type: String,
    name: String,
    arms: i32,
    legs: i32,
    weapon: String,
}
```

### メソッド

```rust
fn main() {
    // staticは::で呼び出す
    let s = String::from("Hello world!");
    // インスタンスメソッドは.で呼び出す
    let t = example.use()
}
```

### メモリ

- データメモリ
  - 固定長/スタティックなデータ
  - 読み取り専用
- スタックメモリ
  - 関数内で宣言された変数
  - 関数の呼び出し中はメモリの位置は変更されないためチューニングできる
- ヒープメモリ
  - プログラムの実行時に作られるデータ
  - 動的なデータが入る
- ダブルクォートで囲まれたテキスト`"Ferris"`は読み取り専用であるため、データメモリに入る
- `String::from`では構造体`String`を作成する
  - ヒープに変更可能なメモリを作り、テキストを入れる
  - 上記で作成した参照アドレスをヒープに保存し、それを`String`に保存する
- タプルのような構造体も利用できる

```rust
struct Location(i32, i32);

fn main() {
    // これもスタックに入れられる構造体です。
    let loc = Location(42, 32);
    println!("{}, {}", loc.0, loc.1);
}
```

- フィールドを持たない構造体も作れる
- あまり使わない

```rust
struct Marker;

fn main() {
    let _m = Marker;
}
```

### enum

- `match`と相性が良い

```rust
enum Species {
    Crab,
    Octopus,
    Fish,
    Clam
}
match ferris.species {
    Species::Crab => println!("{} is a crab",ferris.name),
    Species::Octopus => println!("{} is a octopus",ferris.name),
    Species::Fish => println!("{} is a fish",ferris.name),
    Species::Clam => println!("{} is a clam",ferris.name),
}
```

- enum内の値は複数の方でも良い
- 列挙型のメモリサイズはそれが持つ最大要素のサイズと等しい
- 要素の型以外に書く要素には数字地が着いており、どのタグであるかを示す
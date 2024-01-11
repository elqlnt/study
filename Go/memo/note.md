# Go

- シンプルで高速な処理が可能なプログラミング言語
  - 機能を最小限に抑えている(例外処理や継承、三項演算子がない)
- Webサービスの開発に適している
  - サーバーサイド
- Goでは、コードのパッケージを整理し、バージョン管理するために、モジュールという概念がある
  - 基本はすべてモジュールの単位？
  - コンパイル言語であるため、実行ファイルの生成時に依存関係を解消する必要があるから
- ゴルーチンやチャネルを用いた並行処理
- クロスコンパイル

## 記法

- パッケージ単位で構成される
  - プログラムはmainパッケージから開始される
  - 他のパッケージを使いたいときは`import`
  - その時は、元のパッケージで`export`されている必要がある

  ```go
  import package

  import (
    packageA
    packageB
  )
  ```

- 関数
  - 型情報を付与する
  - 一般的な言語と異なり、型情報は変数名の後ろに記述する
    - 後ろに書く[理由](https://go.dev/blog/declaration-syntax)
  - 関数の2つ以上の引数が同じ型である場合は、省略できる

  ```go
  funcion f(x int, y int){}
  funcion f(x, y int){}
  ```

  - 複数の戻り値を指定できる
  - 戻り値となる変数に名前をつけることができる
    - 記述が長い関数で使うと可読性が落ちる

  ```go
  func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
  }
  ```

- 変数
  - 変数は`var`で宣言する
  - 初期化子が与えられている場合は、型を省略できる
    - 更に`:=`で暗黙的な型宣言ができる

  ```go
  var i, j = 1, 2
  k := 3
  ```

  - 変数に初期値を与えずに宣言すると、その型のゼロ値が与えられる
  - 定数値は`const`を使う
    - 定数は`:=`を使って宣言できない
    - 数値の定数は、その状況によって必要な方を取得してくる(演算によって、intだったりfloat64だったりする)

  ```go
  const Pi = 3.14
  ```

- `for`、`if`、`switch`、`defer`
  - `for`はおおよそ他の言語と同じだが、初期化子と後処理ステートメントは省略できる
  - 条件式も省略すれば無限ループになる

  ```go
  for sum:=0; sum < 1000; sum++{
    sum += sum
  }

  sum := 0
  for sum < 1000 {
    sum += sum
  }
  ```

  - `if`もカッコはいらない
  - `if`ステートメントで宣言した値は`else`でも使える

  ```go
  if v := 5; x < 0 {
    return v
  } else {
    return v + 6
  }
  ```

  - `switch`は`break`は必要ない
  - `case`は定数である必要はないし、整数である必要もない
  - 条件のない`switch`は`true`

  ```go
  today := time.Now().Weekday()

  switch time.Saturday {
    case today + 0:
      fmt.Println("Today.")
    case today + 1:
      fmt.Println("Tomorrow.")
    case today + 2:
      fmt.Println("In two days.")
    default:
      fmt.Println("Too far away.")
  }

  t := time.Now()
  switch {
  case t.Hour() < 12:
    fmt.Println("Good morning!")
  case t.Hour() < 17:
    fmt.Println("Good afternoon.")
  default:
    fmt.Println("Good evening.")
  }
  ```

  - `defer`は、その文を呼び出し元の関数の終わりまで遅延させる
    - 評価自体はその場で行われる
    - `defer`が複数発行された場合、それらはスタックされる
      - last-in-first-out
  
  ```go
  func main() {
    fmt.Println("counting")

    for i := 0; i < 10; i++ {
      defer fmt.Println(i)
    }

    fmt.Println("done")
  }
  // counting
  // done
  // 9
  // 8
  // 7
  // 6
  // 5
  // 4
  // 3
  // 2
  // 1
  ```

## ポインタ

- Goはポインタを扱う
  - ゼロ値は`nil`
  - ただし、ポインタ演算はない

```go
var p *int
i := 42
p = &i
// 値を取り出す
fmt.Println(*p)
```

- 構造体へのアクセスはポインタを介して行うこともできる
- 構造体の一部のメンバだけを初期化して宣言することもできる

```go
v := Vertex{1, 2}
p := &v

  // (*p).X = 1e9 と同じ
p.X = 1e9
fmt.Println(v)

type Vertex struct {
  X, Y int
}
v2 = Vertex{X: 1}
```

## 配列・スライス

```go
var a [2]string
prime := [6]int{2, 3, 5, 7, 11, 13}
```

- 配列は固定長、スライスは可変長
- スライスは実体を持たない、常に配列への参照
- スライスを変更すると、元の配列も変わる

```go
var a []int = prime[1:4]
b := prime[4:]
```

- スライスは長さと容量を持つ
  - 容量は元の配列の長さ
  - 超えるとエラー
  - ゼロ値はnil
- `make`を使用して作成することもできる
  - これは動的サイズの配列を作る
  - 第二引数は長さ、第三引数は容量
  - 値はその型のゼロ値
- 2次元スライスもできる
- 要素を追加したい場合は`append`
  - 容量を超えたら、その分拡充される(割り当て直す)

  ```go
  a := []int{1, 2, 3}
  b := make([]int, 0, 5)
  ```

- `range`はスライスやマップを反復するために使う
  - 返り値はインデックスと場所の要素のコピー
  - 使わない場合は、`_`で捨てることができる
  - インデックスのみが必要な場合は2つめを省略できる

```go
var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}

for i, v := range pow {
  fmt.Printf("2**%d = %d\n", i, v)
}

for i, _ := range pow {
  fmt.Printf("2**%d = %d\n", i, v)
 }
```

## マップ

- キーと値を関連付ける
  - ゼロ値はnil
  - 値の型は省略できたりする

```go
type Vertex struct {
 Lat, Long float64
}
k := make(map[string]Vertex)

m := map[string]Vertex{
 "Bell Labs": Vertex{
  40.68433, -74.39967,
 },
 "Google": Vertex{
  37.42202, -122.08408,
 },
}

m["AAA"] = Vertex{3, 4}

// キーに要素が存在するか？しなくてもゼロ値が返る
v, ok := m["Answer"]
```

## 関数

- 関数も変数として扱える

```go
func compute(fn func(float64, float64) float64) float64 {
 return fn(3, 4)
}

func main() {
 hypot := func(x, y float64) float64 {
  return math.Sqrt(x*x + y*y)
 }
 fmt.Println(hypot(5, 12))

 fmt.Println(compute(hypot))
 fmt.Println(compute(math.Pow))
}
```

## メソッド

- Goにはクラスが無いが、型にメソッドを定義できる
- 以下の`(p Calc)`がレシーバーと呼ばれるもの
  - Calc型のメソッドとして表現することになる
- 値オブジェクトみたいな感じで使えるようになる？
- これは任意の型(float64)にも適用できる
- ポインタレシーバーを持つとき、アドレスに対してではなくても、`(&v)`に対するメソッドとして解釈される
  - 逆の場合も省略できる(`v.Add()`は`(*v).Add()`と解釈される)
- 一般に、値レシーバかポインタレシーバのどちらかで統一させる

```go
// 普通の関数
func Add(q Calc) int {
    return q.atai1 + q.atai2
}

// メソッド
func (p Calc) Add() int {
    return p.atai1 + p.atai2
}

// ポインタにすることで、レシーバーの値に影響させることができる
func (p *Calc) Add() int {
    return p.atai1 + p.atai2
}

// ポインタレシーバーであるとき、以下は(&v).Add()と解釈される
v.Add()

type Values struct {
    Atai1 int
    Atai2 int
    ans   int   // 先頭小文字の変数はカプセル化されている
}
```

## インターフェース

- メソッドのシグニチャの集まりで定義する
- インターフェースに対する実装は、明示的にされている必要はない
- インターフェースの値のメソッドを呼び出すと、基底の方の同じ名前のメソッドが呼び出される
- インターフェース自体の中にある具体的な値が`nil`の場合、一般的には`null`参照とかになるが、Goの場合は呼び出すことができる

```go
type I interface {
 M()
}

type T struct {
 S string
}

// タイプTがインターフェースIを実装していることを意味するが、明示的に宣言する必要はない
func (t T) M() {
 fmt.Println(t.S)
}

// 同じ名前で宣言すると基底の方が呼び出される
func (t F) M() {
 fmt.Println(t.S)
}

func main() {
 var i I

 i = T{"Hello"}
 i.M()

 i = F(math.Pi)
 i.M()

 // nilの場合でも呼び出せる
 // もちろんメソッドを定義してなければエラー
 var t *T
 i = t
 i.M()

 // インターフェースがその値を持っているか
  var i interface{} = "hello"

 s := i.(string)

 s, ok := i.(string) // helloを持つのでtrue

 f, ok := i.(float64) // 持つかどうかをチェックしているのでpanicにはならない

 f = i.(float64) // panic
}
```

- `Stringer`はよく使う、stringとして表現できる型
  - fmtパッケージにある
  - fmtパッケージでは変数を文字列で出力するためにある
- `Stringer()`が実装されていれば、`fmt.Println`内で自動的に`String()`が呼ばれる

```go
type IPAddr [4]byte

func main() {
 hosts := map[string]IPAddr{
  "loopback":  {127, 0, 0, 1},
  "googleDNS": {8, 8, 8, 8},
 }
 for name, ip := range hosts {
  fmt.Printf("%v: %v\n", name, ip)
 }
}

func (i IPAddr) String() string {
 return fmt.Sprintf("%v.%v.%v.%v", i[0], i[1], i[2], i[3])
}
```

### 参考

- [Goのinterfaceがわからない人へ](https://qiita.com/rtok/items/46eadbf7b0b7a1b0eb08)

## エラー

- インターフェースは用意されているので、自分で作る
- その型の`Error()`が実装されていれば、自動的に`Error()`が呼ばれる
  - `Stringr()`と同じ
  - 以下の例では、`ErrNegativeSqrt(x)`を呼んだとき
- fmtパッケージは、変数を文字列で出力する際にerrorインターフェースを確認する
  - そのため、`e`をそのまま出そうとすると、こいつは`ErrNegativeSqrt`なので、再評価されて、無限ループに陥る
  - [A Tour of Goの練習問題を解説するシリーズ(6/11) – Exercise: Errors](https://www.exmedia.jp/blog/a-tour-of-go%E3%81%AE%E7%B7%B4%E7%BF%92%E5%95%8F%E9%A1%8C%E3%82%92%E8%A7%A3%E8%AA%AC%E3%81%99%E3%82%8B%E3%82%B7%E3%83%AA%E3%83%BC%E3%82%BA6-11-exercise-errors/)

```go
type error interface {
    Error() string
}
```

```go
type ErrNegativeSqrt float64

func (e ErrNegativeSqrt) Error() string {
 return fmt.Sprintf("cannot Sqrt negative number: %f", e)
}

func Sqrt(x float64) (float64, error) {
 if x < 0 {
  return 0, ErrNegativeSqrt(x)
 }

 z := 1.0
 for i := 0; i < 10; i++ {
  z -= (z*z - x) / (2 * z)
 }
 return z, nil
}

func main() {
 fmt.Println(Sqrt(2))
 if _, err := Sqrt(-2); err != nil {
  fmt.Println(err)
 }
}
```

## Readers

- `io`パッケージはデータストリームを読むことを表現する
- `io.Reader`インターフェースは`Read`メソッドを持つ
- `Read`は、データを`b`へ格納し、その長さとエラーを返す
  - ストリームの終端だった場合は`io.EOF`を返す

```go
func (T) Read(b []byte) (n int, err error)
```

## Image

- `Image`は以下のインターフェースを定義している
- これらの実装を与えてやることで、`showImage`の動作が定義される

```go
type Image interface {
    ColorModel() color.Model
    Bounds() Rectangle
    At(x, y int) color.Color
}
```

## Go routine

- goroutineは、Goのランタイムに管理される軽量なスレッド
- すべてのGoプログラムは必ず1つ以上のgoroutineを持ち、バックグラウンドで動作する
- goroutine同士は独立しているため、実行の順序は保証されていない

```go
func say(s string) {
 for i := 0; i < 5; i++ {
  time.Sleep(100 * time.Millisecond)
  fmt.Println(s)
 }
}

// 出力順が毎回変わる
func main() {
 go say("world")
 say("hello")
}
```

- この実行順を担保するための仕組みがチャネル
- goroutine同士の値をやり取りする通路の役割と実行フローを制御する役割
- チャネルは`ch := make(chan int)`のように作成する
- チャネルがある場合、受信は別スレッドの送信を待つ
- channelはバッファとして使える`ch := make(chan int, 100)`
  - バッファが埋まると、チャンネルへの送信をブロックする
  - 空のときは受信をブロックする
- 通常は行わないが、送り手は、これ以上送信する値がないことを示す場合に`close`できる
- `select`はgoroutineで、複数ある`case`のいずれかが準備できるようになるまでブロックする
  - ここではチャンネルでの送信または受信作業を意味する
  - 複数のものが準備できている場合はランダムに実行される
  - `default`があって、どの`case`も準備できていなかったらそれが実行される

![channel](https://www.ariseanalytics.com/wp-content/uploads/2022/10/05144212/324e77e1-9b0a-4981-82e1-7517fb7f64f2-1.png)

```go
ch <- v    // 送信
v := <-ch  // 受信

func sum(s []int, c chan int) {
 sum := 0
 for _, v := range s {
  sum += v
 }
 c <- sum // send sum to c
}

func main() {
 s := []int{7, 2, 8, -9, 4, 0}

 c := make(chan int)
 go sum(s[:len(s)/2], c)
 go sum(s[len(s)/2:], c)
 x, y := <-c, <-c // receive from c

 fmt.Println(x, y, x+y)
}

// チャネルが閉じられるまで、チャネルから値を繰り返し受信する
for i := range c {}

// select
func fibonacci(c, quit chan int) {
 x, y := 0, 1
 for {
  select {
  case c <- x:
   // cに値が入った時に実行
   x, y = y, x+y
  case <-quit:
   // quitに値が入った時に実行
   fmt.Println("quit")
   return
  default:
   fmt.Println("******")
   time.Sleep(50 * time.Millisecond)
  }
 }
}

func main() {
 c := make(chan int)
 quit := make(chan int)
 go func() {
  for i := 0; i < 10; i++ {
   fmt.Println(<-c)
  }
  quit <- 0 //quitはcの受信を待つ
 }()
 fibonacci(c, quit)
}
```

- 2分木の問題のやつ

```go
package main

import (
 "golang.org/x/tour/tree"
 "fmt"
)

// Walk walks the tree t sending all values
// from the tree to the channel ch.
func Walk(t *tree.Tree, ch chan int) {
 if t == nil {
  return
 }
 
 Walk(t.Left, ch)
 ch <- t.Value
 Walk(t.Right, ch)
}

// Same determines whether the trees
// t1 and t2 contain the same values.
func Same(t1, t2 *tree.Tree) bool{
 ch1, ch2 := make(chan int, 10), make(chan int, 10)
 go Walk(t1, ch1)
 go Walk(t2, ch2)
 
 res := true
 
 for i := 0; i < cap(ch1); i++ {
  n1 := <-ch1
  n2 := <-ch2
  
  res = n1 == n2
   }
 
 return res
}

func main() {
 fmt.Println(Same(tree.New(1), tree.New(1)))
 fmt.Println(Same(tree.New(1), tree.New(2)))
}
```

- もっときれいなやつ

```go
func Walk(t *tree.Tree, ch chan int) {
    WalkRecursive(t, ch)
    close(ch)
}

func WalkRecursive(t *tree.Tree, ch chan int) {
    if t != nil {
        WalkRecursive(t.Left, ch)
        ch <- t.Value
        WalkRecursive(t.Right, ch)
    }
}

func Same(t1, t2 *tree.Tree) bool {
    ch1, ch2 := make(chan int), make(chan int)
    go Walk(t1, ch1)
    go Walk(t2, ch2)
    for {
        n1, ok1 := <- ch1
        n2, ok2 := <- ch2
        if ok1 != ok2 || n1 != n2 {
         return false
        }
        if !ok1 {
         break;
        }
    }
    return true
}
```

- goroutine間で通信の必要がない場合、一つのgoroutineだけあ変数にアクセスできるようにしたいときは`Lock`と`Unlock`を使う

```go
// SafeCounter is safe to use concurrently.
type SafeCounter struct {
 mu sync.Mutex
 v  map[string]int
}

// Inc increments the counter for the given key.
func (c *SafeCounter) Inc(key string) {
 c.mu.Lock()
 // Lock so only one goroutine at a time can access the map c.v.
 c.v[key]++
 c.mu.Unlock()
}

// Value returns the current value of the counter for the given key.
func (c *SafeCounter) Value(key string) int {
 c.mu.Lock()
 // Lock so only one goroutine at a time can access the map c.v.
 defer c.mu.Unlock()
 return c.v[key]
}

func main() {
 c := SafeCounter{v: make(map[string]int)}
 for i := 0; i < 1000; i++ {
  go c.Inc("somekey")
 }
```

### 参考

- [Goのinterfaceがわからない人へ](https://qiita.com/rtok/items/46eadbf7b0b7a1b0eb08)
- [【Go】このコードの意味が分かれば、ゴルーチンの基本は大丈夫](https://zenn.dev/farstep/articles/f712e05bd6ff9d)

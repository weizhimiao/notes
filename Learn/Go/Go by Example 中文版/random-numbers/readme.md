

Go 的 math/rand 包提供了伪随机数生成器（英）。

```go
package main
import "time"
import "fmt"
import "math/rand"
func main() {

    // 例如，rand.Intn 返回一个随机的整数 n，0 <= n <= 100。
    fmt.Print(rand.Intn(100), ",")
    fmt.Print(rand.Intn(100))
    fmt.Println()

    // rand.Float64 返回一个64位浮点数 f， 0.0 <= f <= 1.0。
    fmt.Println(rand.Float64())

    // 这个技巧可以用来生成其他范围的随机浮点数，例如 5.0 <= f <= 10.0
    fmt.Print((rand.Float64()*5)+5, ",")
    fmt.Print((rand.Float64() * 5) + 5)
    fmt.Println()

    // 默认情况下，给定的种子是确定的，每次都会产生相同的随机数数字序列。
    // 要产生变化的 序列，需要给定一个变化的种子。 
    // 需要注意的是，如果你出于加密目的，需要使用随机数的话，请使用 crypto/rand 包， 此方法不够安全。

    s1 := rand.NewSource(time.Now().UnixNano())
    r1 := rand.New(s1)

    // 调用上面返回的 rand.Source 的函数和调用 rand 包中函数 是相同的。
    fmt.Print(r1.Intn(100), ",")
    fmt.Print(r1.Intn(100))
    fmt.Println()

    // 如果使用相同的种子生成的随机数生成器，将会产生相同的随机 数序列。
    s2 := rand.NewSource(42)
    r2 := rand.New(s2)
    fmt.Print(r2.Intn(100), ",")
    fmt.Print(r2.Intn(100))
    fmt.Println()
    s3 := rand.NewSource(42)
    r3 := rand.New(s3)
    fmt.Print(r3.Intn(100), ",")
    fmt.Print(r3.Intn(100))
}
```

```sh
$ go run random-numbers.go
81,87
0.6645600532184904
7.123187485356329,8.434115364335547
0,28
5,87
5,87
```
参阅 [math/rand 包 文档](http://golang.org/pkg/math/rand/) ，提供了 Go 可以提供的其他随量的参考信息。


Slice 是 Go 中一个关键的数据类型，是一个比数组更 加强大的序列接口

- 创建&声明
- 初始化
> 与数组不同，slice 的类型仅由它所包含的元素决定（不需要 元素的个数）。要创建一个长度非零的空 slice，需要使用内建的方法 make。
```go
s := make([]string, 3)  // 这里我们创建了一 个长度为3的 string 类型 slice（初始化为零值）。
```
- 赋值&取值
> 和数组一样设置和得到值
```go
s[0] = "a"
s[1] = "b"
s[2] = "c"
fmt.Println("set:", s)
fmt.Println("get:", s[2])
```

- 相关常用函数
    - len() // 返回 slice 的长度
    - append()  // 返回一个包含了一个 或者多个新值的 slice
    - copy()    

- `slice[low:high]` 操作

```go
package main
import "fmt"
func main() {

    // 与数组不同，slice 的类型仅由它所包含的元素决定（不需要 元素的个数）。要创建一个长度非零的空 slice，需要使用内建的方法 make。这里我们创建了一 个长度为3的 string 类型 slice（初始化为零值）。
    s := make([]string, 3)
    fmt.Println("emp:", s)

    // 我们可以和数组一样设置和得到值
    s[0] = "a"
    s[1] = "b"
    s[2] = "c"
    fmt.Println("set:", s)
    fmt.Println("get:", s[2])

    // len 返回 slice 的长度
    fmt.Println("len:", len(s))

    // 除了基本操作外，slice 支持比数组更丰富的操作。 其中一个是内建的 append，它返回一个包含了一个 或者多个新值的 slice。注意由于 append 可能返回 新的 slice，我们需要接受其返回值。
    s = append(s, "d")
    s = append(s, "e", "f")
    fmt.Println("apd:", s)

    // Slice 也可以被 copy。这里我们创建一个空的和 s 有 相同长度的 slice c，并且将 s 复制给 c。
    c := make([]string, len(s))
    copy(c, s)
    fmt.Println("cpy:", c)

    // Slice 支持通过 slice[low:high] 语法进行“切片”操 作。例如，这里得到一个包含元素 s[2], s[3], s[4] 的 slice。
    l := s[2:5]
    fmt.Println("sl1:", l)

    // 这个 slice 从 s[0] 切片到 s[5]（不包含）。
    l = s[:5]
    fmt.Println("sl2:", l)

    // 这个 slice 从 s[2] （包含）开始切片。
    l = s[2:]
    fmt.Println("sl3:", l)

    // 我们可以在一行代码中声明并初始化一个 slice 变量。
    t := []string{"g", "h", "i"}
    fmt.Println("dcl:", t)

    // Slice 可以组成多维数据结构。内部的 slice 长度可以不 一致，这和多维数组不同。
    twoD := make([][]int, 3)
    for i := 0; i < 3; i++ {
        innerLen := i + 1
        twoD[i] = make([]int, innerLen)
        for j := 0; j < innerLen; j++ {
            twoD[i][j] = i + j
        }
    }
    fmt.Println("2d: ", twoD)
}
```

**Tips:**
注意，slice 和数组是不同的类型，但是它们通过 fmt.Println 打印 结果类似。

```sh
$ go run slices.go
emp: [  ]
set: [a b c]
get: c
len: 3
apd: [a b c d e f]
cpy: [a b c d e f]
sl1: [c d e]
sl2: [a b c d e]
sl3: [c d e f]
dcl: [g h i]
2d:  [[0] [1 2] [2 3 4]]
```

看看这个由 Go 团队撰写的 [一篇很棒的博文](http://blog.golang.org/2011/01/go-slices-usage-and-internals.html) ， 了解更多关于 Go 中 slice 的设计和实现细节。



for 是 Go 中唯一的循环结构。这里有 for 循环 的三个基本使用方式。

- 单个循环条件
- 经典的初始/条件/后续 for 循环
- 不带条件的 for 循环

```go
package main
import "fmt"
func main() {
    
    // 最基础的方式，单个循环条件。
    i := 1
    for i <= 3 {
        fmt.Println(i)
        i = i + 1
    }
    // 经典的初始/条件/后续 for 循环。
    for j := 7; j <= 9; j++ {
        fmt.Println(j)
    }
    
    // 不带条件的 for 循环将一直重复执行，直到在循环体内使用 了 break 或者 return 来跳出循环。
    for {
        fmt.Println("loop")
        break
    }

    // 你也可以使用 continue 来跳到下一个循环迭代
    for n := 0; n <= 5; n++ {
        if n%2 == 0 {
            continue
        }
        fmt.Println(n)
    }
}
```

```sh
$ go run for.go
1
2
3
7
8
9
loop
1
3
5
```

后续教程中当我们学习 `range` 语句，`channels`，以及其他 数据结构时，将会看到一些 `for` 的其它形式。

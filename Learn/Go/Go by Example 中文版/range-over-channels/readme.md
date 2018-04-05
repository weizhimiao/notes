
在前面的例子中，我们讲过 `for` 和 `range` 为基本的数据结构提供了迭代的功能。我们也可以使用这个语法 来遍历从通道中取得的值。

```go
package main
import "fmt"
func main() {
    
    // 我们将遍历在 queue 通道中的两个值。
    queue := make(chan string, 2)
    queue <- "one"
    queue <- "two"
    close(queue)
    
    // 这个 range 迭代从 queue 中得到的每个值。
    // 因为我们 在前面 close 了这个通道，这个迭代会在接收完 2 个值 之后结束。
    // 如果我们没有 close 它，我们将在这个循环中 继续阻塞执行，等待接收第三个值
    for elem := range queue {
        fmt.Println(elem)
    }
}
```

```sh
$ go run range-over-channels.go
one
two
```

这个例子也让我们看到，
- 一个非空的通道也是可以关闭的， 但是通道中剩下的值仍然可以被接收到。
- 使用 `range` 进行遍历的 chan 必须关闭，不然将会进入死循环

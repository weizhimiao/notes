

我们的第一个程序将打印传说中的 “hello world“ 消息。

```go
package main
import "fmt"
func main() {
    fmt.Println("hello world")
}
```
要运行这个程序，将代码放到 `hello-world.go` 中 然后执行 `go run` 。

```sh
$ go run hello-world.go
hello world
```

有时候我们想将程序编译成二进制文件。 可以通过 `go build` 来达到目的。

```sh
$ go build hello-world.go
$ ls
hello-world	hello-world.go
```

然后我们可以直接运行这个二进制文件。
```sh
$ ./hello-world
hello world
```
现在我们可以运行并编译基本的 Go 程序，让我们开始学习更多 关于这门语言的知识吧。

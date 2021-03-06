在学习一门语言的时候，了解一下通用，常规的代码组织结构，有益于写出符合易于维护的代码。

## 概览

- golang开发者一般将他所有的 Go 代码放在一个工作空间(**workspace**)
- 一个工作空间包含很多版本控制的代码仓库
- 每个代码仓库包含一个或多个包(**package**)
- 每个包由一个或者多个Go源文件组成，在一个目录下
- 一个包的路径决定了它的 导出路径(**import path**)

## 工作空间(***Workspace*)

一个工作空间目录里面有两个子目录:
- `src` 包含go的源代码
- `bin` 包含可执行文件

go命令行工具会将构建或者安装的二进制文件放在 `bin`目录下

`src`子目录下一般含有多个版本控制的仓库。

目录结构如以下：

```
bin/
    hello                          # command executable
    outyet                         # command executable
src/
    github.com/golang/example/
        .git/                      # Git repository metadata
	hello/
	    hello.go               # command source
	outyet/
	    main.go                # command source
	    main_test.go           # test source
	stringutil/
	    reverse.go             # package source
	    reverse_test.go        # test source
    golang.org/x/image/
        .git/                      # Git repository metadata
	bmp/
	    reader.go              # package source
	    writer.go              # package source
    ... (many more repositories and packages omitted) ...
```

用官方文档的一句话总结工作空间的作用就是

> A typical workspace contains many source repositories containing many packages and commands. Most Go programmers keep all their Go source code and dependencies in a single workspace

## GOPATH环境变量
`GOPATH` 环境变量是描述你的工作空间的目录所在位置的，默认是指向是home目录的go文件夹下，所以，在Unix系统中是`$HOME/go`，在Windows中是`C:\Users\YourName\go`，如果你想指定其他地方为工作空间，可以设置`GOPATH`环境变量，一般是加一个目录，而不是替换

## Import paths

导出路径是能唯一标识一个包的字符串，一个包的导出路径对应它在你的工作空间的位置或者远程仓库

标准库中的包，都是比较短的导出路径，比如 `fmt`，`net/http`

如果你的包托管在一些版本控制仓库中，比如在 `Github`中，那么包的导出路径会是这个样子: `github.com/iamMarkChu/strings`


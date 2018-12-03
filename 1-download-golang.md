golang的下载还是比较简单的，到 [golang官网下载页](https://golang.org/dl/),下载你所用操作系统所对应的安装包就可以了。

## 安装

### windows下安装

#### 使用.msi文件安装

1. 从 [golang官网下载页](https://golang.org/dl/) 下载.msi文件
2. 直接点开.msi文件，然后狂点下一步就行了，go的目录默认会在 `C:\Go`， 然后会把 `c:\Go\bin`放到 `PATH`环境变量中，重启你的`CMD`就能生效了。

#### 使用.zip文件安装

1. 从 [golang官网下载页](https://golang.org/dl/) 下载.zip文件
2. 解压后，放在你想放的目录下。
3. 设置环境变量 `GOROOT`为解压后的go文件夹的路径(第二步中)
4. 设置环境变量 `PATH`，加上 `GOROOT/bin`目录


### linux下安装

1. 从 [golang官网下载页](https://golang.org/dl/) 下载对应平台的.tar.gz文件
2. `tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz`
3. `export PATH=$PATH:/usr/local/go/bin`, 永久生效的话，需要修改 `.profile`文件，然后 `source $HOME/.profile.`

### macOs下安装

1. 从 [golang官网下载页](https://golang.org/dl/) 下载.dmg文件
2. 直接点开.dmg文件，然后狂点下一步就行了， go的目录默认会在 `/usr/local/go`，然后会把 `/usr/local/go/bin`放到 `PATH`环境变量中，重启你的命令行就能生效了。


___

## 验证安装是否成功

通过创建一个 `workspace`，然后build一个简单的程序来测试安装是否成功。

默认的工作空间是 `%USERPROFILE%\go`，所以我们在这个路径下新建 `src/hello`

``` go
package main

import "fmt"

func main() {
	fmt.Printf("hello, world\n")
}
```

然后使用 go的命令行工具构建一下,

```
C:\> cd %USERPROFILE%\go\src\hello
C:\Users\Gopher\go\src\hello> go build
```

然后会生成一个 hello.exe的可执行文件，执行一下

```
C:\Users\Gopher\go\src\hello> hello
hello, world
```

## 卸载

卸载只要删除对应的go目录就行了，比如 windows下，默认是 `C:\go`, macOs下，默认是 `usr/local/go`。




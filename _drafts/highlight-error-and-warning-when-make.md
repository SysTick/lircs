# make高亮显示警告和错误

对于在linux环境下面编程的你，一定对`make`并不陌生，当然也很可能遇到过这样的情况。当你在编程一个项目的时候，你的`make`输出的是青一色的白字，而不巧，你的项目又没有编译通过。那么这个时候你就会去关注`make`输出的信息，可是青一色的白字是不是很头大。好在已经有前辈给出了解决方案。

本文介绍的方法来自[github项目](https://github.com/chinaran/color-compile)，感谢作者。

> 克隆项目到本地

```bash
$ cd ~
$ git clone git@github.com:chinaran/color-compile.git
$ cd color-compile
```
[clone]()

> 编译/安装

```bash
$ cd color-compile
$ make
$ sudo make install #need root
```
> 配置

配置`~/.bashrc`
```bash
$ alias gcc="color_compile gcc"
$ alias g++="color_compile g++"
$ alias make="color_compile make"
$ alias mips-linux-gnu-gcc="color_compile mips-linux-gnu-gcc"
$ alias mips-linux-gnu-g++="color_compile mips-linux-gnu-g++"
```

> 总结


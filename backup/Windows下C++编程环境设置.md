## Mingw下载

从官网下载MingW 体验不好，不仅速度慢，而且不包含调试器gdb。可以从第三方下载网站找重新编译好的软件包。网址是：https://winlibs.com/
比如windows 64位系统可以使用的下载链接：https://github.com/brechtsanders/winlibs_mingw/releases/download/14.2.0posix-18.1.8-12.0.0-ucrt-r1/winlibs-x86_64-posix-seh-gcc-14.2.0-llvm-18.1.8-mingw-w64ucrt-12.0.0-r1.7z
## 配置

解压到任意文件夹，比如放到`c:/`目录下，路径为：`c:/mingW64`。将该目录下bin子目录加到系统级环境变量的PATH中，即可使用命令行编译c语言程序。

推荐使用Vscode来进行源代码编辑。VSC中要安装c/c++扩展支持，提供语法高亮和编译工具选择支持。推荐直接在vscode的terminal中进行编译、执行和调试，免去编译配置的步骤（可以参考：https://www.cnblogs.com/elmluo/p/15933484.html）。

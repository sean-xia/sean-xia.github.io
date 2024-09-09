### 问题描述

最近，帮小朋友解决了centos服务器上一个奇怪的环境变量无法生效的问题。症状是无论`bashrc`如何修改，`source`之后就是没有效果。

感觉到bashrc是依赖于所使用的shell程序的。而Linux操作系统的shell十分混乱，至少目前主流的有三种
* bash
* tcsh
* zsh

使用最多的就是bash, 这些程序的路径都是`/bin/`.
我猜测是不是shell默认程序被修改成了其他的程序呢？于是使用
```shell
echo $SHELL
```
查看了一下，果然是`tcsh`.

这样就基本破案了，罪魁祸首就是这个tcsh。简单地说，每个不同的shell所对应的初始化文件是不一样的，其中

* bash -> .bashrc
* tcsh -> .tcshrc

所以在tcsh这个shell中无法使用bashrc中定义的环境变量，别名等。

### 解决办法

只要把默认的shell程序从tcsh修改成bash就行了
命令行输入

```shell
chsh -s /bin/bash
```
同时为了使得命令行提示符里可以正常显示用户名，主机名以及当前路径等关键信息，需要在`~/.bashrc`中增加下面一句话
```shell
export PS1='\u@\h:\w\$ '
```
其中
* `\u`是指用户名（username），
* `\h`是指主机名（hostname）, 
* `\w`是指当前工作目录的完整路径，
* `\$`: 如果是普通用户则显示$，如果是root用户则显示#

编辑完`~/.bashrc`后保存退出， source一下
```shell
source ~/.bashrc
```
最后关闭此终端，重新登录一次即可生效。

另外，如果要查看别名是否生效，可以使用如下命令 ：
```shell
alias
```

最后，想搞清楚到底是哪个程序修改了默认的shell程序。我查了相关的安装软件的脚本，似乎都没有修改这个shell设置。只能怀疑是无疑修改的。或者原本这个操作系统默认的就是`tcsh`. Who Knows, Who Cares!


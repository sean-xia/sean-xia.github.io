## Winget简介

Windows下安装软件通常并不友好，要么安装一个**管家之类的全家桶，要么到各软件的官方网站去下载，确实很麻烦。但是Windows 10 (1809+) 之后可以使用Winget了。具体安装参考https://github.com/microsoft/winget-cli/releases。win11 已经内置winget了，不需要单独安装。

## 使用方法

在cmd或者power shell 中运行 `winget install [softwarename]` 即可。

例如，安装QQ和微信，
`winget install tencent.qq`

`winget install tencent.wechat`

如果这里大陆地区，可能会遇到源不可访问的问题，建议修改为中科大的源

修改 WinGet 软件源需要管理员权限，请以管理员身份运行终端。

替换 USTC 镜像：

`winget source remove winget`
`winget source add winget https://mirrors.ustc.edu.cn/winget-source`


>[!TIP]
> 如果不知道软件的全称，也没关系，可以使用 `winget search [keyword]` 来搜索，然后选择安装。
> 比如，不知道搜狗输入法如何安装，可以搜索
> `winget search sogou`
> 找到相应的名称进行安装。

## 小结
我尝试了工作中要用到的所有软件，基本上可以找到安装包，安装速度也很快。值得向所有windows用户推荐。
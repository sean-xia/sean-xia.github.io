最近找到了一款寨板 usb T4000 软件无线电接收机，很多年前的老物件了。拿出来擦一下灰，发现还是可以玩一玩的。记录如下。

## 1 SDR# 软件安装配置

转摘自  http://www.pckbd.com/rtl-sdr/
下载 SDR# 软件：

https://airspy.com/?ddownload=3130

下载 SDR# 软件不安装，解压后即可使用，需要注意 SDR# 是 x86 32-bit 应用程序，不是 64-bit。

但是对于 RTL-SDR，由于知识产权原因，SDR# 并没有集成支持 RTL-SDR 的驱动程序，使用 RTL-SDR 前需要先仅进行配置。

最简单的方式就是使用管理员权限执行 cmd.com，然后进入 SDR# 目录执行 install-rtlsdr.bat 自动安装驱动程序。注意需要从 Github 下载文件，需要提前确认是能顺利下载。成功执行 install-rtlsdr.bat 后，将 RTL-SDR 插在 USB 口，在 SDR# 目录下可以找到 zadig.com 文件以管理员权限运行，确保 zadig 的 Options->List All Devices 选项勾选，一定确保选择 Bulk-In, Interface (Interface 0) 安装WinUSB驱动程序。成功安装后，即可正常使用。

RTL-SDR 在 SDR# 中的推荐配置如下：

Sample Rate: 2.4 MSPS
RF Gain: 37.2 dB
Correct IQ: ON
Bandwidth: NFM/AM: 12500, WFM: 250000
Filter: Blackman-Harris 4
Order: 500

如执行 install-rtlsdr.bat 自动安装驱动程序失败，可以手动安装驱动程序。下载最新的 RTL-SDR 驱动：

http://github.com/rtlsdrblog/rtl-sdr-blog/releases/latest/download/Release.zip

解压后将 x86 目录中（需要注意 SDR# 是 x86 32-bit 应用程序，不是 64-bit）的 rtlsdr.dll 文件复制到 SDR# 目录。然后下载最新版的 libusb-1.0.dll binary 文件包：

https://github.com/libusb/libusb

解压后将 VS2015-Win32 目录中（需要注意 SDR# 是 x86 32-bit 应用程序，不是 64-bit）的 libusb-1.0.dll 复制到 SDR# 目录下覆盖原文件。

下载最新版的 zadig：

https://zadig.akeo.ie/

按上述方法安装 WinUSB 驱动即可正常使用。

上述软件配置好之后打包到一起，以免每次安装都需要重新配置。

## 2 软件使用
打开SDR# 之后，选择FM，然后调节右边频谱图中的中心频率即可。带宽和滤波方式在左边进行调节，还是很方便的。

这个软件对于学习数字信号处理和通信原理的同学还是很有用的，尤其是调制和解调的原理。当然也可以配合matlab来使用，可玩性更强。
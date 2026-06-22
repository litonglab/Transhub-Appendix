# Transhub安装指南2026版

💡PDF/Word版文档不方便复制多行命令，且图片较为模糊，可登录transhub查看**在线版本**

（[《Transhub竞赛指南》中"Transhub安装指南"部分](https://transhub.litonglab.com)），获取更好的阅读体验。



硬件环境：一台Linux主机（在本文中，Linux主机包括运行Linux系统的实体机、虚拟机或云服务器）

Linux版本要求：Ubuntu GNU/Linux 14\.04以上

****

**拥塞控制算法的运行示意图如下：**



![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZWFhNDdiYTdmZDAyZTdmYmIxMGZiY2ZmOTJkMmU2MzFfZjA4MTBjODkzYzVmYTlhZWYxNTZjNzNkODBhNjJiYmRfSUQ6NzQ3NDgyMjY2NTM1MjEwMTg4OV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)





本教程提供两种安装方式，两种方式**任选其一**：

- 第一种方法为使用Linux虚拟机/主机，安装相关依赖，下载transhub代码并编译，编译完成后即可运行实验。

- 第二种方法为使用已配置好的Docker镜像，镜像里已装好相关依赖和代码，**开箱即用**，可**直接**运行实验。

❗由于以上部分依赖仅有x86架构的包，因此使用**Mac M芯片**的同学需要注意，如果使用第一种方法自行安装虚拟机，需安装x86架构的Linux系统，使用Arm架构的虚拟机将无法安装所有依赖。建议Mac M芯片同学使用**Docker方法**。



---

# （一）安装transhub

## 方式一：使用Linux虚拟机/主机直接安装transhub

> **⭐Windows系统推荐使用此方式**
> 
> 

### 1\.1\. 安装Linux虚拟机（若直接使用Linux物理机可跳过此步）

- 下载VMware软件

参考教程：

[VMware Workstation Pro 17官网下载安装教程\_vmware17pro下载\-CSDN博客](https://blog.csdn.net/air__j/article/details/142798842)

官方下载链接：

[https://support\.broadcom\.com/group/ecx/productdownloads?subfamily=VMware%20Workstation%20Pro](https://support.broadcom.com/group/ecx/productdownloads?subfamily=VMware%20Workstation%20Pro)

- 下载Ubuntu 18\.04的镜像（Ubuntu20版本*可能*存在依赖无法安装的问题，建议使用**18**版本）

[Index of /ubuntu\-releases/18\.04/ \| 清华大学开源软件镜像站 \| Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/18.04/)



- 使用VMware创建Ubuntu 18\.04的虚拟机

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZDJhMTBlYTBmZjVlNjA0Y2ZiNTVhYzNiZTgyNmE3ZThfNGFjNDMxMWJlNTY0ZDc4NDU3YTQ2Mzg4YjlhZTMyNTBfSUQ6NzQ3NDY0MTcxNjg3MjY1ODk0Nl8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NmU2MjY1NWNhOGFjOTBlZjI4ZTUwOTQxMzYyMDE5ZTBfM2Y5ZTk1OGY1NGEwYjg2MGU4YTIzZTc5Njg2ZDBiYWNfSUQ6NzQ3NDY0MTcwOTQxOTUyODE5NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YTlmOWI5NzA1ZDdkZTk1Y2FmODE3YmVmNWJkMzk1YTRfMDE4OGU1NzZmMmZmNjExZjQzYzk0YjVhNTZlMjQ1MTJfSUQ6NzQ3NDY0MTcxMDEzNjYzOTQ5MV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NGIyOWUwNDc2ZjlhOWIxOWM3NDU0NzE0MDIyY2FkMjdfZDlhNzZkMjdmYWU0NTM4YjczNDhmNTY0ODc3M2U0Y2NfSUQ6NzQ3NDY0MTcwOTc4MDA1ODExNV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OWViOTMxYjgxM2MzODVkNzgxNjJlODJjMzA2NTVkMTFfMTc5Y2U0NTQ0NDEzZmFkZjc4ZjZkYjliODg1YjRjMjJfSUQ6NzQ3NDY0MTcxNDExMjc5MDUyOV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MjhjOTI3Njc1YjIxZWYyYzMzZDBiZDhkYmQwZTAwNTRfYWRkMmNmNmQ4NzU2YWE2NWM2NWUxMzc1NjIzNzBhY2ZfSUQ6NzQ3NDY0MTcxMzg4MjIzNDkwOF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=N2JlODAzN2NjYTc4ZTk3YjdkM2M1MGUxMTVmMGI0NGRfNWQ1NjI1OTVlMjVhZWZhY2NiNzg2YzMyZmZjZjJkZGZfSUQ6NzQ3NDY0MTcwNzk4MjQ1NDc4N18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NGZiOGYzZWQyNDQzZDRlNjY1OGM3ZWYwYmUwYjgyNjlfZjEyOGU1OTQwNjM1YmFlYjIyMTQ5NzhhZGY2NzA1MzNfSUQ6NzQ3NDY0MTcwNDM4NjQxMjU3Ml8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MjI1YTA3Njc3YmU2ZWQxODg2NzJlOTY1N2E0N2E4ZmFfNGViYjhlMDI0MDdhNGVhNjQ2MWYxMzFmMmExNmUwM2RfSUQ6NzQ3NDY0MTcwMzM5MjE4MjI3NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

- 将依赖包下载源站换为国内网站，避免因为网络问题导致依赖包下载失败

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NWM3MjBhM2JhYzEyYmQ4YWEyNzU2ZWJlMTY0OTc0ZDVfYzczN2VmMDUwZTNjYTkyNGI4MjBlZWVhZmQxYTRjY2FfSUQ6NzQ3NDY0MTcwMzMyNTA3MzQxMF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NTBjYWUwZmY1MDg0ZjExNmIxMWI2YTdlNjBlNzAzYzZfYjI4MDg2Y2JmNTQ2MjY3ZTU4YTYyY2RmZmM2MjkzYjFfSUQ6NzQ3NDY0MTcwNDgxODIyOTI3Nl8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=Y2IxMzljMGEzNzg1MzUxODg5ZmNhYmQ1NTYyYjg3MzlfN2Q5NDdmYTk3NTdmYjYzZDY3MTZhN2QzZGI4NjE1MzNfSUQ6NzQ3NDY0MTcwNTg0NTc1MTgyN18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=Zjc5MDIwZTg5ZTUzNDIyNWJmMTlmZjA1ZGQ4MzBmNGNfODU3OThjN2YzNzA2OWMyOGFiMWM4ODc4OTg3YmVlN2RfSUQ6NzQ3NDY0MTcwNDQ5OTQxMjk5Nl8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MGIxMTc5NjYzODVkNDkyOGQ0ZDU1M2YzOGVkYjNiZDJfZmE4YWEwZjAwNmJkMjIxZDhiNTdjOGY3ZTY5NTVhZjJfSUQ6NzQ3NDY0MTcwNTczMjU1NDc1NF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NzdiZjQ5ZjhlMGI5ZDg3YWMxZDJmN2QxNzAxNTg1ODRfMmIyZWQ0N2FkYTkzNjNmOThmMzgzZjE3YzE4NTdlOWNfSUQ6NzQ3NDgyMzYzMjgyMzQ2ODAzNV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NzFiMjdiMzUzMGI5YTM4OTdlYzhiMzY4MDg1YTJlMWNfMDg5NTEwNWJlODYyNzhkZWUyMTVjMDUwMzE2MDA4MmZfSUQ6NzQ3NDY0MTcwNDYzNzc0MzEyM18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NWNjYzgxMDQzZTNiNzM5ZjhkYjczODBjY2EzODFlNjJfNGQ0NzUwMzRiZTUwNWQ3NGZmOWNkNzg4NThiZmU4YjVfSUQ6NzQ3NDY0MTcwOTg1NzQ3MjUzMV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZjBhZjMyYzcyZTFiMDlkNjk3ZDExMWE1NWRlMzlmZmFfM2ZjNjJmMTA3ZDg3NDg1NmM1NTU2YTczY2I0Nzk4MmFfSUQ6NzQ3NDY0MTcxMjY0ODk2MjA1Ml8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=Yzg5YjJhZmNlZTZmNDNkZjkwMDJmNThjNWJmMjJkNDFfN2NjYjAzOTYxZjkyNjBkOTIzNmRhOGVmNzA4NGVkY2RfSUQ6NzQ3NDgyMzg3NTE4OTgzMzczMF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZTVmZjlkNDk1MzIzZDE1NTA3YTVjMTY5YjczYTBmMmZfODNlMTUwOGY3YjI4MDY4MzFmZWUwNzRlZDY1OGRjZDBfSUQ6NzQ3NDY0MTcwOTQwODQxOTg1OV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YzliMGNhOTNiZTEwM2EwNDEzYWE5Y2VjZDg4NjFjNjNfMzUzOTRkNmUzNzEzMjcwMGE5ZWY1NjJjYTQ2MmY1MzdfSUQ6NzQ3NDgyMzk0ODg3MDQzNDgxN18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



### 1\.2\. 安装Mahimahi

- 在其终端中运行如下代码，安装依赖项：

```Bash
sudo apt-get install build-essential git debhelper autotools-dev dh-autoreconf iptables protobuf-compiler libprotobuf-dev pkg-config libssl-dev dnsmasq-base ssl-cert libxcb-present-dev libcairo2-dev libpango1.0-dev iproute2 apache2-dev apache2-bin iptables dnsmasq-base gnuplot iproute2 apache2-api-20120211 libwww-perl
```

（这些依赖项在[mahimahi / debian / control](https://github.com/keithw/mahimahi/blob/master/debian/control#L5)中列出，另外还有一些用于比赛的依赖项）

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YjM2MzdjMDVjZTEzODE0MTA0YzkwZTBkNmMyY2Q0N2JfYjU4ZWFkNWI0MzM2ZmM5OWJmZTk2ZmRjYjY2OWVlZTZfSUQ6NzQ3NDY0MTcxNDczNzc0MTg0M18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NTA2YjdmMzg1ZjEzZjMxZjhiODBlMDZlOWZlYjk1NzdfZGU1ZDRjMzhjMjNiNDUzZmRlNDk4MzY5NjBiOWM3YjJfSUQ6NzQ3NDY0MTcxNDE1MjI5MjM1M18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZTY3ODI5ZjYwYzZlNmZlZjE3NjdiODRiOWMwOGFmOTdfZTY1YzRkMDcxMTlmOTQxNTdkYTY1OWM4MmFjMTVlMGZfSUQ6NzQ3NDY0MTcxMjkzMDAyOTU2OV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MGQyZTYyOWQ2M2NkNWZhYmJhMzU1MWExOWU4ZTFhMTNfYzQ5MTQ3MGNlMzUwMjc3M2U0ZWRlNzZmOWFiMGQ1ODBfSUQ6NzQ3NDgyNDA4MzcyMjQ1Mjk5NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



- 下载mahimahi源代码

```Bash
git clone https://github.com/ravinet/mahimahi 
```

（Mahimahi工具提供了我们模拟的蜂窝网络和测量工具）

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YTUxOTFmMGIyODU3OTc3YWQzNWVkNDFhMWYzMTA1MTBfZDdlNWU0OGEwMzhiZGVjOTNiMjViMWRlMWUwYjE3NTdfSUQ6NzQ3NDY0MTcyMDU1MDk2NTI1MF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



- 编译并安装mahimahi

```Bash
cd mahimahi

# （用make工具编译mahimahi）
./autogen.sh && ./configure && make

# 安装
sudo make install
sudo sysctl -w net.ipv4.ip_forward=1 
# 进入mahimahi
mm-delay 20
# 退出mahimahi
exit
```

（若要检查是否安装成功，可运行`mm_delay 20`，若出现delay 20ms字样，说明安装成功）

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OTVkZjY2MTEwODg1ZGY3NjQwMGJhODFlNDc1NzMxYzNfZWM3Y2NkYzlkNzY0M2I4NjMyNWMyYmZmNWEyZDlkYmZfSUQ6NzQ3NDY0MTY5NjY5OTcxMTQ4OV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OGYwMDIzZDgzYzViNTY0ODY2MTdkNDYzZTc3NjM1YjFfNzQ4YzkzMWU5MmQyNDdjNDFmOGY4MjczYjk3MGIyZmNfSUQ6NzQ3NDY0MTY5NjUzODU0MjA4M18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OTA1OGY3NjQzYjhjNDZjOGZhMmFhMjk1Njg0ZjFlYTlfYjY3MjM2NmVhMDczMzkyZmMzYzg2YWRhMDdhOWI0NTNfSUQ6NzQ3NDY0MTcwMDA4NzA4NzEwNl8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZjFhZGVmYWU1MDBiODBjOTNhMDk3MjA0YjRmNDAzMjFfMmZhZmRhMmRmMDc5MDJlMmM4YWNhMTg4Mjk4YWM3NjFfSUQ6NzQ3NDY0MTcwMDI0MjA5NjEzMV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



### 1\.3\. 编译Transhub代码

```Bash
#退出mahimahi目录，回到用户目录
cd ..
#下载transhub代码
git clone https://git.ruc.edu.cn/akth/cc-training 
cd cc-training
#按常规方式编译代码
./autogen.sh && ./configure && make 
```

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YTg5Yzg3OWQwZjY2MjQ3NWQwMDg5NDcwYWYxODBmZWJfZmQzZmE2NDVhNTY3YWJhN2JmYzRhZmZkZDZmNmZkMTJfSUQ6NzQ3NDY0MTcwODQ4OTkzMjgwNF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NzgyMTUyMGZmYjdkNWJiYzE0YTJmNWRmZjhlM2ZmMThfNGEwYTBkZGFlNTgxNWUyODU3MjBmNDAyN2Q2NWYyNTNfSUQ6NzQ3NDY0MTcxODU2MDQ1NjcwNV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NGUzZmYxNzRkNWI2YWZlYjIxNmFhMTBiZDA3OGRmZmVfZjNjNTQ4MWYzYTFlMzNlYTY5YWM3ZjdjNjY5MzUzMWNfSUQ6NzQ3NDY0MTcyMjAyMDYyNjQzM18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NjMwOTBiMjRhMTFhNjdkOTAzODViZDhlNDA0MTEzNzlfOTJlZjQyOGNlMTMzYjYyN2NlNDAyNGE4MTE5OWNkYTBfSUQ6NzQ3NDY0MTcyNjA3OTA5MDY5Ml8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OGU1OGU0ZGM4N2JkYjlmNWVlZjEwOWRhMWIzY2NkYjZfNTg5NDI3ZmQwZmZkOGFmYjNjODUzNDI4NTQ0MGUxMDJfSUQ6NzQ3NDY0MTcyMzQ3ODYyMjIxMF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MzI1MTk2M2I1NmFlOGIxNjY1Y2Y1Y2QzMjZiMThmNmVfYjliODAxMDM2NzBmYmZkMjE5NTA3M2JkYzQ4Yzc3ODlfSUQ6NzQ3NDY0MTcyNTg2MDg3MjE5M18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



## 方式二：使用已安装好Transhub的Docker镜像

> **⭐MacOS系统推荐使用此方式**
> 
> 2\.1部分仅限Mac，Linux/Windows平台参照对应教程安装好Docker后，后续方法（2\.2\-2\.4）通用。
> 
> 

### 2\.1\. 安装Docker

Linux/Windows上如何安装使用Docker请自行查询相关教程，此处以Mac安装Docker为例。

Mac上可安装Docker Desktop或者Orbstack，这里以Orbstack为例。

> OrbStack 是一款专为 MacOS 设计的轻量级容器和虚拟机管理工具，旨在为开发者提供快速、高效的容器化开发和测试环境。它支持 Docker 容器和 Linux 虚拟机，特别针对 Apple Silicon（M1/M2 等 ARM 芯片）进行了优化，能够无缝运行 x86 和 ARM 架构的容器。
> 
> 

访问[https://orbstack\.dev/download](https://orbstack.dev/download) 下载并安装。安装好后，打开Orbstack完成初始化。



### 2\.2\. 下载并导入Transhub镜像

访问以下链接下载已配置好的transhub镜像：

- 夸克网盘：链接：[https://pan\.quark\.cn/s/da8e2b2dfdd8](https://pan.quark.cn/s/da8e2b2dfdd8)  提取码：ae6w

- 百度网盘：链接: [https://pan\.baidu\.com/s/10ltC9\-XBsS0XKMpb7JBK0w?pwd=rt9x](https://pan.baidu.com/s/10ltC9-XBsS0XKMpb7JBK0w?pwd=rt9x) 提取码: rt9x

在**镜像所在目录**运行终端，执行以下命令导入transhub镜像

```Bash
docker load -i transhub.tar
```

导入成功后，可以在Orbstack看到该镜像：

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ODE0ZjZjNzYxOGUyYzMyNmEwNmEyOGIyMGE4YWEzZGFfODBkODcwZTNhOGI0MWQzY2Q3ZGViNzBlNWQxNzliZWZfSUQ6NzQ3NDY0MTcyMTM3MzE3OTkyM18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



### 2\.3\. 创建并运行Transhub容器

此步骤**仅需执行一次**，使用以下命令创建并运行transhub容器：

```Bash
sudo docker run --platform linux/amd64 --privileged -itd --name transhub transhub:v2.0
```

❗注意，在m芯片mac上，需要显式指定平台为 `linux/amd64`，强制运行 x86 架构的镜像

❗注意，如需要使用`-v`命令将主机上的目录挂载到容器目录，请勿覆盖容器内的 `/home/none_root/transhub` 目录。因为该目录下已包含配置好的代码文件，如映射后，将被主机目录覆盖。即如需使用` -v ~/Downloads/transhub:/home/none_root/transhub`，`:`后不得接`/home/none_root/transhub`

运行成功后，可以在Orbstack中看到其已处于运行状态：

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NDE4MDYzZGJlNDFjMTg5YTNkYjU0MGIzYzUxZmUxYWFfOGU3ZjQ3MTUzYzRlOGQ5NTAwOTE3YjE5ZDEzMjk0ZDBfSUQ6NzQ3NDY0MTY5ODU3Mjg5NDIwOV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



### 2\.4\. 进入Transhub容器

- 首先，确保容器已经启动并正在运行。在执行完2\.3步后，容器已经处于运行状态。后续若需再次使用容器，则无需再重复执行2\.3步骤，可使用以下方法来启动容器。

> ***`docker run`***命令通常用于第一次启动一个新的容器。当你执行 ***`docker run`*** 时，Docker会执行两个步骤：首先，它会从指定的镜像创建一个新的容器（相当于执行了 ***`docker create`*** 命令），然后它会启动这个容器，使其变成一个运行中的容器（这一步相当于执行了 ***`docker start`***` `命令）。因此，***`docker run`*** 是一个组合命令，它不仅创建容器，还会立即启动容器。如果在系统上找不到指定的镜像，***`docker run`*** 甚至会尝试从Docker Hub拉取镜像。
> 相比之下，***`docker start`*** 命令用于启动一个已经存在的容器。如果你之前已经创建了一个容器（无论是通过 ***`docker create`*** 创建的，还是之前用 ***`docker run`*** 创建并启动过的），你可以使用 ***`docker start`*** 来重新启动这个容器。这意味着，使用 ***`docker start`*** 时，你必须知道要启动的容器的ID或名称。
> 
> 

可以运行以下命令查看容器状态：

```Bash
docker ps
```

如果容器正在运行，你会看到类似以下的输出：

```Bash
CONTAINER ID   IMAGE           COMMAND       CREATED       STATUS       PORTS     NAMES
eecfe24288b1   transhub:v2.0   "/bin/bash"   5 minutes ago Up 5 minutes          transhub
```

如果容器没有运行，可以使用以下命令启动它：

```Bash
docker start transhub
```

- 使用 `docker exec` 命令进入容器的 Shell，后续即可在终端中**操作该容器**

```Bash
docker exec -it transhub /bin/bash
```

- 接下来可进入容器的目录`/home/none_root/transhub`，可以看到已安装好的mahimahi和transhub文件：

```Bash
cd home/none_root/transhub/
ls
```

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NmU4NGNjYWZlNTI3ZWY1NjQwYTkzYjUwYjdlOTZmNjFfZDdlZTQ1ODc1Mjc2MTY0ZDBjM2ZiOGMyMzVhZWEwMDZfSUQ6NzQ3NDY0MTczMjA5MzcyMjYyOF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



---

# （二）运行实验测试

运行`run-contest`开始测试后，程序将模拟VerizonLTE连接大约两分钟，请耐心等待，运行完成时会生成日志。

💡`run-contest`工具负责将测试文件通过模拟Verizon downlink生成日志，并使用mahimahi仿真，提供传输过程中的性能信息，并显示queueing delay和throughput随时间变化的折线图。

### 2\.1\. 通过方式一安装的测试过程

- 运行`run-contest`开始实验

```Bash
sudo sysctl -w net.ipv4.ip_forward=1 #（必须启用Linux的IP转发才能使mahimahi工作）
cd datagrump #（前提已经在cc-training目录下）
./run-contest [scheme_name] #（scheme_name就是你给自己文件命名的名称，第一次使用时可以将[scheme_name] 替换为controller.cc）
```

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MWE1MDlmNGNmZTE2MjQ2ZDUwZWY3YmFmOWNmYjRlODhfNGUyMWQ1YTg3MzA3MDczZDZjM2RiYWEzMjg1NjY5MjBfSUQ6NzQ3NDY0MTcyNjA1Mzk1NzYzNV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MTM5MmI1MzZhN2Y2NGNmYWNlMWUzNTMyMjRlZWY5YzhfZjVkZTQ4Zjg5ZDg5ZTBlMjFmZDg5ZmRmYjMwMjM1YmZfSUQ6NzQ3NDY0MTcyNzU1MTIwOTQ3NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZWNlMDljNzU5ZTY1NzMxODYzZmQwZWNjMzNiYTYyOGVfNTFlMWI2NjdlY2ZkODQ3NTU0OGY3Yzk0OGM2Y2ZkMTRfSUQ6NzQ3NDgyNTU1MDY2MzU5ODA4M18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YTQ0ZjViOTE4MWU5MDc2M2Y2MjJmZDg0ZDY5M2MzYjdfNDI2Mzc3Yjg5ZDZlMTdjNzk0MTA0ZTEwM2Y5YjdmYzFfSUQ6NzQ3NDY0MTcyNjA3OTEwNzA3Nl8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MTc2M2Y3OTc2MGFiYzZhOTNkN2ZkYjdiMGJlM2RkMDBfNTc0YzMxYzRkZjI0OThhMWU0YWQ2Yzg1ZDBkNDU0NTlfSUQ6NzQ3NDY0MTcyNzI5OTYzMzE1NF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

- 使用如下命令获取实验结果

```Bash
mm-throughput-graph  500  ./contest_uplink_log > a.svg #（分析日志，输出吞吐等信息,得到svg图）

# 得到以下结果
Average capacity:平均容量
Average throughput:平均吞吐量
95(th) percentile per-packet queueing delay:95%排队延迟
95(th) percentile signal delay:95%信号延迟
```

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NTk3ZDhkNDUxZWUyZWFlMDU3MjRkNGRjNDFhNjlhZWNfOTM5Yjc0MGYyOWRjMTRlZjY3MDQxYWMwMWZjOTQ3N2NfSUQ6NzQ3NDY0MTcyMzc1MTM4MzA0MV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZGEwZWUzZGNjM2I0MWQ5ZmNmNmFjMzNlMjQ2YmVjNjBfMGZkN2VhOTcxZTBmZDc4NDg2MDBjMDgwNjkyOWY4MzJfSUQ6NzQ3NDgyNTc1NDI2MzY1MDMwN18xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZTg1MDlmNTQwMTJkZmVkZGU0MzU0YTdmMTZhMjA0ZDlfNTU5Mzg2NjVmNGM5YjhkNGE3YzQxNjNkZDIwODI5ZGNfSUQ6NzQ3NDY0MTczMDU4ODg1MjIyNl8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



### 2\.2\. 通过方式二安装的测试过程

❗注意，在容器中运行时，运行`run-contest`需要在非root用户下执行，而开启linux的IP转发以及编译源代码需要在root用户下。使用`su none_root`切换为非root用户，使用`exit`切换回root用户。在使用过程中请注意在两种用户间灵活切换。

- 运行`run-contest`开始实验

```Bash
sysctl -w net.ipv4.ip_forward=1 #（必须启用Linux的IP转发才能使mahimahi工作，此操作需在root用户下执行）
cd datagrump #（前提已经在cc-training目录下）
su none_root #（切换为非root用户。若是想再切换回root，只需要输入exit然后按下回车即可）
./run-contest [scheme_name] #（scheme_name就是你给自己文件命名的名称，第一次使用时可以将[scheme_name] 替换为controller.cc）
```

执行命令时，若如下方提示`please run as non-root`，请使用命令`su none_root`切换到non\_root用户。

```Bash
root@12be595786c5:/home/none_root/transhub/cc-training/datagrump# ./run-contest  controller.cc
Listening on :::9090
Died on std::runtime_error: mm-delay: please run as non-root
 done.
```

由非root用户切换回root用户示意图：

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OGYyZDA4ZjBkZWNmYmUyYjFmNDU0YTM2OTM4MDVhYWFfNGI0NDI3ZTY0YjgzNmFmMjliNGYxNmMyM2Q4ODc1M2ZfSUQ6NzQ3NDY0MTczMTYwMDYxMzM5NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



- 使用如下命令获取实验结果

```Bash
mm-throughput-graph  500  ./contest_uplink_log > a.svg #（分析日志，输出吞吐等信息,得到svg图）

# 得到以下结果
Average capacity:平均容量
Average throughput:平均吞吐量
95(th) percentile per-packet queueing delay:95%排队延迟
95(th) percentile signal delay:95%信号延迟
```

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZDlmNjE4NDI2Mzg3YzUzNmZiZWYxOWM4NWZkNGEyOTJfZjMwNGYwYjhiOGQzY2UyYmZmMzI1ZDQ1ODI1ODEyMDZfSUQ6NzQ3NDY0MTczMjA5MzY3MzQ3Nl8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

Mac可通过以下方式找到容器内文件：

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NjYyYzI5NTdmN2M3MjZlMWE3MWQ0NDQxNDJhNDYwMDhfODFjNzMxMWU0MjFkYzA2YTI3NDVhM2I1MDg1M2UxZDRfSUQ6NzQ3NDY0MTcyOTE0NTIwODgzNF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YWQ5ODQ0MzdlY2NlNjlmNTdlN2M3ZjVmOGRmNTNhNDlfNWYyNGY1MDY3MTUyOGIzMzcyZjg4NzAyMmNkYjc0MzFfSUQ6NzQ3NDY0MTczMjM0MTEyMTA1Ml8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



🎉**Congratulations！至此，你已成功安装transhub，接下来请按照后续任务书要求，完成相应任务。** 



---

# （三）系统拥塞控制算法配置（\*可选）

本节内容介绍了如何查看并修改系统拥塞控制算法，属于**拓展阅读**部分。

Linux系统中可选的拥塞控制算法包括`reno`、`cubic`、`bbr`等。本节以配置`bbr`算法为例：

❗配置不同的拥塞控制算法会对传输结果产生不同的影响，可做相关实验验证（此处所指**实验并非**本transhub中的`run-contest`实验，`run-contest`的拥塞控制算法为`controller.cc`,与系统拥塞控制算法无关。如需验证系统拥塞控制算法，可使用`iperf`等工具来做相关实验）。

### 3\.1 通过方式一安装的操作过程

💡在Linux主机上启用BBR算法

```Bash
# 查看系统支持的拥塞控制算法
sudo sysctl net.ipv4.tcp_available_congestion_control
# 输出结果：表明当前系统支持reno cubic算法
# net.ipv4.tcp_available_congestion_control = reno cubic

# 查看系统当前使用的拥塞控制算法
sudo sysctl net.ipv4.tcp_congestion_control
# 输出结果：表明当前系统使用cubic算法
# net.ipv4.tcp_congestion_control = cubic

# 切换到BBR
sudo sysctl net.core.default_qdisc=fq
sudo sysctl net.ipv4.tcp_congestion_control=bbr
# 查看是否切换成功
sudo sysctl net.ipv4.tcp_congestion_control

# 切换回CUBIC
sudo sysctl net.core.default_qdisc=pfifo
sudo sysctl net.ipv4.tcp_congestion_control=cubic
# 查看是否切换成功
sudo sysctl net.ipv4.tcp_congestion_control
```



![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MDc5OGI2NzM4MzMwMTI1NWZiNzQ4MTcyMDdmODg5NjFfMWZjOTU3N2EzMWIyMzI3Nzg2MzI5YTg4ODg0ZWQ4ODdfSUQ6NzQ3NDY0MTczMDI1MjQ4ODcwOF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZWM1ZThiMDE3NDUwNTk1NGIyMmJjMmMxNmRiOGRlMWZfYThiZWY4YjRlOWRiYzU4NzAwNTFkOTJlZmI1ZTM5YmNfSUQ6NzQ3NDY0MTcyODU2NjI4MDE5NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MWQxOTQ1NzMzMTk4OGJkYWFhMzQ1MGQ2ZTZiNDJmODlfMGQ5NTA5NWYyOGUwYmY3NzdhZmIyMTdjODUzZWRhNTBfSUQ6NzQ3NDY0MTczNjIxNjkyMDA2NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZmRkMGFkZDg2NjI0MjEzZjMwNTg4OTA4YmRiMDAxMzNfYzBmNjAxZGIyMjExNjFlZGVjNGMwMmE4MzY4ODA0MTNfSUQ6NzQ3NDY0MTczMTA2MjE4NTk4NV8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



### 3\.2 通过方式二安装的操作过程

💡在Docker容器中启用BBR算法

**附相关知识点：Docker容器共享主机内核**：

- Docker容器共享宿主机的内核，因此容器内的网络配置（如拥塞控制算法）受宿主机内核限制。

- 如果宿主机内核不支持BBR，容器内也无法使用BBR。

> [Docker](https://zhida.zhihu.com/search?content_id=461284401&content_type=Answer&match_order=1&q=Docker&zhida_source=entity)在[macOS](https://zhida.zhihu.com/search?content_id=461284401&content_type=Answer&match_order=1&q=macOS&zhida_source=entity)上和Windows上跑[Linux](https://zhida.zhihu.com/search?content_id=461284401&content_type=Answer&match_order=1&q=Linux&zhida_source=entity) docker都是先套了个虚拟机，虚拟机里跑Linux提供[kernel](https://zhida.zhihu.com/search?content_id=461284401&content_type=Answer&match_order=1&q=kernel&zhida_source=entity)，再在里面跑docker。目前虚拟机在Windows上是[Hyper\-V](https://zhida.zhihu.com/search?content_id=461284401&content_type=Answer&match_order=1&q=Hyper-V&zhida_source=entity)或者WSL，macOS上有两套方案。
> 
> 

**拥塞控制算法**属于**内核算法**，所以在Docker容器能够使用的拥塞控制算法受**宿主机内核**确定。bbr算法是较新的算法，并非在所有内核都支持。

使用命令`sysctl net.ipv4.tcp_available_congestion_control`查看当前支持的拥塞控制算法：

```Bash
# 查看系统支持的拥塞控制算法
sysctl net.ipv4.tcp_available_congestion_control
# 输出结果：表明当前系统支持reno cubic算法
# net.ipv4.tcp_available_congestion_control = reno cubic
```

- 如是Linux宿主机，可按照3\.1节方法开启宿主机bbr算法，在容器中也将变更为bbr算法。

- Mac若是使用Orbstack的容器，可尝试使用reno或cubic算法。目前暂时没找到打开bbr的方法，因为容器内开启bbr算法需要**宿主机内核**支持。而在Orbstack中，该内核实际上是由Orbstack提供的**定制化的内置Linux内核**，用户无法修改。

- Windows Docker若是使用WSL后端，理论上可尝试在WSL中修改。本教程未在Windows Docker环境下进行测试，欢迎感兴趣的同学尝试后帮助补充此部分内容。

在Docker中切换拥塞控制算法的命令如下：

```Bash
# 查看系统支持的拥塞控制算法
sysctl net.ipv4.tcp_available_congestion_control
# 输出结果：表明当前系统支持reno cubic算法
# net.ipv4.tcp_available_congestion_control = reno cubic

# 查看系统当前使用的拥塞控制算法
sysctl net.ipv4.tcp_congestion_control
# 输出结果：表明当前系统使用cubic算法
# net.ipv4.tcp_congestion_control = cubic

#===========若内核支持BBR，使用以下命令切换到BBR以及切回CUBIC
# 切换到BBR
sysctl net.core.default_qdisc=fq
sysctl net.ipv4.tcp_congestion_control=bbr
# 查看是否切换成功
sysctl net.ipv4.tcp_congestion_control

# 切换回CUBIC
sudo sysctl net.core.default_qdisc=pfifo
sudo sysctl net.ipv4.tcp_congestion_control=cubic
# 查看是否切换成功
sudo sysctl net.ipv4.tcp_congestion_control

#===========若内核不支持BBR，例如使用Orbstack，使用以下命令切换到RENO以及切回CUBIC
# 切换到RENO
sysctl net.ipv4.tcp_congestion_control=reno

# 切换到CUBIC
sysctl net.ipv4.tcp_congestion_control=cubic
```

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MjhlZDgyZjBjMTA4YTNiZjE5ZjZkMjllOTQyZjljMDJfZjUyMzY3OWE1MTI3MmRhNTZlZWI0MmZlNjJiYjQ4MjhfSUQ6NzQ3NDY0MTczNDE2OTg4Njc0OF8xNzgyMTQ3MDE1OjE3ODIyMzM0MTVfVjM)



---

本文档更新时间：2026年03月01日 星期日 15:00




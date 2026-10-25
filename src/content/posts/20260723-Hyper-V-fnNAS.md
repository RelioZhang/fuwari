---
title: 'Hyper-V安装飞牛OS教程-NAS入门指南'
published: 2026-07-23
description: '有些朋友想尝试一下飞牛OS，但是又不想重新组装一套NAS机器，那么可以先试试用Hyper-V虚拟机在先有的Windows电脑上安装飞牛OS体验一下再决定要不要组装一套新机器。'
image: 'https://im.124365.xyz/file/20260723/1784789899740_fnos.webp'
tags: [Docker, fnNAS, Docker Compose]
category: Docker
draft: false
---


### 下载飞牛OS镜像[​](#下载飞牛os镜像 "下载飞牛OS镜像的直接链接")

点击下方的卡片进入飞牛OS官方网站

### 🌐 飞牛OS官方网站

fnnas.com - 系统镜像下载

### 在Windows中启用Hyper-V功能[​](#在windows中启用hyper-v功能 "在Windows中启用Hyper-V功能的直接链接")

打开 控制面板，点击进入 “程序和功能”。

![](https://fnnas.wiki/assets/images/image-1-790e2760cc64cb7b1dd5a2fb72a835cc.png)

在左侧菜单中，点击 “启用或关闭 Windows 功能”。

![](https://fnnas.wiki/assets/images/image-2-04acda845dd1c03556090b46742c5896.png)

在右侧列表中找到并勾选 “Hyper-V” 复选框。

![](https://fnnas.wiki/assets/images/image-3-3d669df5959d8bdef46e0a444474b71c.png)

点击“确定”。Windows 将会安装所需文件。

### 配置Hyper-V虚拟网络[​](#配置hyper-v虚拟网络 "配置Hyper-V虚拟网络的直接链接")

在开始菜刀打开 “Hyper-V 管理器”

![](https://fnnas.wiki/assets/images/image-4-848e85124106c9fe280bc8215093271a.png)

在右侧的“操作”面板中，点击 “虚拟交换机管理器”。

![](https://fnnas.wiki/assets/images/image-5-664875c13ebabbc16e59d2eacf0f99a8.png)

选择 “新建虚拟网络交换机”。在右侧选择 “外部” 作为交换机类型，然后点击 “创建虚拟交换机”。

![](https://fnnas.wiki/assets/images/image-6-022fb70a66b06f86d552cddb183eb7e7.png)

命名：给你的虚拟交换机起一个易于识别的名称，这里我写成了 FNNAS，在“外部网络”部分，选择你电脑当前用来上网的 物理网卡，这里我是笔记本电脑，有两个网卡，一个有线，一个无线，带wireless的就是无线网卡，目前我通过无线连接的，所以选择无线网卡。

勾选 “允许管理操作系统共享此网络适配器” 选项。这能让电脑（宿主机）和虚拟机同时通过这块网卡上网。 ![](https://fnnas.wiki/assets/images/image-7-92c30ac13ad0fadfe5bb37d34e295fd0.png)

点击 “应用”，系统可能会有短暂的网络中断，等待配置完成。

### 创建虚拟机[​](#创建虚拟机 "创建虚拟机的直接链接")

在“Hyper-V 管理器”的右侧“操作”面板中，点击 “新建” -> “虚拟机”，启动新建虚拟机向导。 ![](https://fnnas.wiki/assets/images/image-8-f673a5bbdf7036ece8dcb3a1d7300895.png)

为虚拟机命名（如：FNNAS），这里可以自定义虚拟机的存储位置，默认的位置在C盘，如果C盘空间不足，可以自定义到其他磁盘。注意这里如果长期使用则存储位置要放在起码有64GB剩余空间的磁盘上。

![](https://fnnas.wiki/assets/images/image-9-8b5f8d1f2c35543d317c52d248f55c89.png)

指定代数： 必须选择 “第一代”

![](https://fnnas.wiki/assets/images/image-10-eab8dbe51268a3247d1fa86e134e77a7.png)

分配内存：设置分配给虚拟机的内存大小。不要勾选“为此虚拟机使用动态内存”

![](https://fnnas.wiki/assets/images/image-11-ef047a4c3d3c3b749dac126cc1b89924.png)

配置网络：在“连接”下拉菜单中，选择之前创建的那个外部虚拟交换机，这里选择FNNAS，如果没有的话回到前面配置虚拟网络连接的时候看看是不是忘了点应用了。

连接虚拟硬盘：

*   选择“创建虚拟硬盘”。
*   设置系统盘的大小，视频建议系统盘 至少为 64 GB。

![](https://fnnas.wiki/assets/images/image-12-27973593fb90e2754226fd85e5d25331.png)

安装选项：

*   选择 “从可启动的映像文件安装操作系统”。
*   点击“浏览”，找到并选择下载的飞牛OS的 `.iso` 镜像文件。

![](https://fnnas.wiki/assets/images/image-13-1ff22ef540406124862651151190cca8.png)

点击 “完成” 创建虚拟机，这一步会在你选择的路径下创建两个文件夹，分别存放系统数据和磁盘数据。

### 安装飞牛系统[​](#安装飞牛系统 "安装飞牛系统的直接链接")

在“Hyper-V 管理器”的虚拟机列表中，右键点击刚刚创建的 FNNAS 虚拟机，选择 “连接”，在弹出的虚拟机连接窗口中，点击 “启动” 按钮。

![](https://fnnas.wiki/assets/images/image-14-65364a66d5c3d8b1750bdcd0b0e7c627.png)

虚拟机将从ISO文件启动，进入安装界面后，按 回车键 选择 “安装到虚拟磁盘”。

![](https://fnnas.wiki/assets/images/image-15-856d3fdb500d52f00b17b90b5e24d796.png)

按照安装向导的提示，连续点击 “下一步” 和 “确定”。等待安装进度条走完。安装成功后，界面会显示系统获取到的 IP地址，记住这个地址，之后在局域网内就可以通过这个地址访问到飞牛OS了。点击 “保存”，然后点击 “确定”，虚拟机会自动重启。 ![](https://fnnas.wiki/assets/images/image-16-dd2e43aea400fd0c73def2057c4f4b76.png)

### 虚拟机配置[​](#虚拟机配置 "虚拟机配置的直接链接")

在虚拟机重启后，首先在Hyper-V管理器中将其 “强制关闭”。

![](https://fnnas.wiki/assets/images/image-17-3a26f5dcca5119ee8db294097a6f2127.png)

右键点击虚拟机，选择 “设置”。添加数据硬盘（用于存储数据），在左侧选择“SCSI控制器”，在右侧选择“硬盘驱动器”，然后点击 “添加”，在“虚拟硬盘”部分，点击 “新建”，启动新建虚拟硬盘向导。

![](https://fnnas.wiki/assets/images/image-19-8cb8e37bafca7bfccd2980f7b57e4654.png)

选择磁盘格式为（VHDX），选择磁盘类型为 “固定大小”，命名并选择存储位置。根据你的需求设置数据盘的大小。点击“完成”，稍等片刻，系统会自动创建硬盘，完成之后会自动返回到设置界面，点

注意

*   命名的时候不要删掉vhdx的后缀，否则会创建失败
*   创建完成后会回到设置界面，一定要点击**应用**保存。 ![](https://fnnas.wiki/assets/images/image-21-c2cf94da8a298aa29d4661976d7e1100.png)
    

![](https://fnnas.wiki/assets/images/image-20-7f1a88ad50e9c3c0afd1d8fcb39374df.png)

#### 移除安装介质：[​](#移除安装介质 "移除安装介质：的直接链接")

在虚拟机设置的左侧，选择 “DVD 驱动器”。在右侧选择 “无”，以弹出安装镜像，防止下次开机时再次进入安装程序。

![](https://fnnas.wiki/assets/images/image-22-033064e228cff96d4cabd8a23582c191.png)

### 配置自动启动：[​](#配置自动启动 "配置自动启动：的直接链接")

在设置的左侧最下方选择“自动启动操作”。建议选择 “始终自动启动此虚拟机”，并可以设置一个 “启动延迟”（如30秒），以防止宿主机启动时负载过高。 6. 完成所有设置后，点击 “应用” 和 “确定” 保存。

![](https://fnnas.wiki/assets/images/image-23-8efae80d3c6bfc9154927c6143e254c7.png)

### 飞牛OS网页端初始化[​](#飞牛os网页端初始化 "飞牛OS网页端初始化的直接链接")

启动 虚拟机。2. 等待虚拟机控制台界面加载完成，并显示出 IP地址。 ![](https://fnnas.wiki/assets/images/image-24-a9ecb056f7a9acbc90a52d0d6f8ada76.png)

在电脑上打开一个网页浏览器，在地址栏输入该IP地址并访问。 ![](https://fnnas.wiki/assets/images/image-25-bc061131da6ee34ce7313f8d6f3c4f41.png)
 开始配置：

*   点击“开始”。
*   设置 设备名称、超级管理员账号 和 密码。
*   创建存储空间： 根据界面右侧的向导提示，创建存储池和存储空间。由于是虚拟机，不同模式效果一样

![](https://fnnas.wiki/assets/images/image-26-d2ac4395a5f15caef3fcfb199f5950f5.png)
 绑定飞牛账号： 下一步，绑定你的飞牛账号。如果没有，需要先在官网(fnnas.com)注册一个。至此，飞牛OS系统已完全配置好。
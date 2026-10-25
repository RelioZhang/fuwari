---
title: 'ZeroOmega 配置，规则列表网址可自动更新'
published: 2026-07-20
description: ''
image: ''
tags: [fnNAS, 绿联NAS, 浏览器扩展]
category: Docker
draft: false
---

[ZeroOmega](https://github.com/zero-peak/ZeroOmega "zero-peak/ZeroOmega") 是 [SwitchyOmega](https://github.com/FelisCatus/SwitchyOmega "FelisCatus/SwitchyOmega") 的一个更新分支，其界面和使用方式与 SwitchyOmega 相同。原插件 SwitchyOmega 不兼容 manifest V3，故不再使用。

浏览器插件 ZeroOmega 的配置备份，支持三种情景模式，规则列表网址可自动更新。

| 情景模式 | 类型 | 说明 |
| --- | --- | --- |
| _GFWed_ | 固定模式 | 该模式强制浏览器通过特定途径进行网络访问。 |
| _白名单_ | 自动切换模式 | 列表网址为中国网址。  
该模式避免通过特定途径访问相应网址。  
适用于访问网址以国外为主、国内为辅时。 |
| _黑名单_ | 自动切换模式 | 列表网址为国外网址。  
该模式允许通过特定途径访问相应网址。  
适用于访问网址以国内为主、国外为辅时。 |

使用方法
----

### 安装 ZeroOmega

适用于基于 Chromium 的浏览器的 ZeroOmega 插件，可通过以下任一方式安装：

*   [Chrome Web Store](https://chromewebstore.google.com/detail/proxy-switchyomega-3-zero/pfnededegaaopdmhkdmcofjmoldfiped "Proxy SwitchyOmega 3 (ZeroOmega) - Chrome Web Store")
    
*   [Chrome扩展 - Crx搜搜](https://www.crxsoso.com/webstore/detail/pfnededegaaopdmhkdmcofjmoldfiped "Proxy SwitchyOmega 3 (ZeroOmega) | Chrome扩展 - Crx搜搜")
    
*   [Github Releases](https://github.com/zero-peak/ZeroOmega/releases "Releases · zero-peak/ZeroOmega")
    

### 导入备份

打开 ZeroOmega 选项，

![](https://i-blog.csdnimg.cn/direct/8fce700ccaed458aad3f3380b2facfa9.png#pic_center)

① 点击 “导入/导出”；

② “在线恢复”，输入以下链接后，点击 “恢复”。

```
`https://raw.githubusercontent.com/chugit/SwitchyOmegaBackup/main/OmegaOptions.bak` 

*   1


```

或

```
`https://gitee.com/chugit2024/SwitchyOmegaBackup/raw/main/OmegaOptions.bak` 

*   1


```

③（备选）若在线恢复不成功，可从 [github](https://github.com/chugit/SwitchyOmegaBackup/blob/main/OmegaOptions.bak) 或 [gitee](https://gitee.com/chugit2024/SwitchyOmegaBackup/raw/main/OmegaOptions.bak) 下载备份文件 OmegaOptions.bak，然后点击 “从备份文件恢复” 加载该文件。

### 修改 _GFWed_ 参数

插件配置恢复后，首先应根据代理软件实际，修改情景模式 _GFWed_ 的参数。

![](https://i-blog.csdnimg.cn/direct/9bf6b7b8afcc404d956d68b43003a149.png#pic_center)

根据所使用软件的参数和说明书，对 _GFWed_ 情景模式进行修改，选择并设定与软件对应的 “ 协议 ”、“服务器” 和 “端口”。

此外，可在 “地址列表” 中指定该情景模式需要绕过的IP（即不通过该途径访问的网址）。本备份文件中的不通过特定途径访问的地址（见上图）均为本地地址。

点击侧边栏的 “应用选项”，保存插件配置。

### 选择 _白名单_ 或 _黑名单_ 科学上网

完成上述配置后，即可选择基于规则的情景模式 _白名单_ 或 _黑名单_ 进行上网。

情景模式 _白名单_ 和 _黑名单_ 的参数默认设置如下，一般不需要修改。

![](https://i-blog.csdnimg.cn/direct/822c72fdc35f4c7e8d3d37ea9993e619.png#pic_center)
  
![](https://i-blog.csdnimg.cn/direct/e9e97d6ceb8f4d25af1d71f1be491066.png#pic_center)

*   _白名单_ 的规则列表网址为中国网址，可避免通过特定途径访问这些网址，适合访问网址以国外为主、国内为辅时使用。
    
*   _黑名单_ 的规则列表网址为国外网址，要求通过特定途径访问这些网址，适合访问网址以国内为主、国外为辅时使用。
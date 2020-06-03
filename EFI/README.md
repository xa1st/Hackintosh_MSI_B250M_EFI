微星B250M-E OpenCore EFI

### 当前OC版本
0.5.8

### 重要说明 

<font color="red">更新至0.5.6之后，CONFIG文件大改，请务必保存旧的CONFIG文件，默认设置启动项的方法为 呼出启动菜单(win+r),选择对应项, 按 ctrl+enter, 即可设置为默认启动项</font>

没有3码，需要自己去填

### 机器配置

1. CPU: I5-6500 
2. 内存：金士顿 DDR4 2400 8g 普条 x 2
3. 显卡：HD530(集显)
4. 主板：[微星B250M-E](https://cn.msi.com/Motherboard/B250M-E, "官网链接")
5. 声卡：ALC887(实际上探测为 Realtek ALC888B (0x0887) )，仿冒ID为40
6. 硬盘: 雷克沙512M SSD M.2 2280(需升级最新版本BIOS才可识别), 西数1T硬盘
7. 键盘: 达尔优DK100
8. 鼠标: DELL MS 116 (19块一个)
9. 网卡：板载 RTL8111H / TP-LINK TL-WN725N V2 

### 实现功能

1. 10.15.2 除了快捷键都应该算是OK了
2. SSD已内置，网卡也已内置
3. 4K硬解也已OK
4. 声卡仿冒成功，基本完美识别，可以识别前后也可以识别显示器的HDMI
5. 原生电源管理(节能5项)
6. USB电源管理
7. 加入VirtualSMC的CPU温度传感器，istatus显示正常 (2019-11-25)

### 系统补丁
1. lilu.kext   1.4.7
2. VirtualSMC.kext  1.1.4
3. WhateverGreen.kext 1.3.7
4. AppleALC.kext   1.4.7
5. RealtekRTL8111.kext  2.2.2
6. USBPorts.kext  自己生成
7. USBPower.kext  自己生成

### DSDT
1. SSDT-no-EC.aml   禁用ECO
2. SSDT-PLUG-_PR.CPU0.aml  原生电源管理

### 需要自己动手的
1. 因为原生不支持nvram所以需要工具生成，下载完EFI之后还需要用 LogoutHook来生成nvram，不然无法修改启动项，方法请阅读:[https://blog.xjn819.com/?p=543](https://blog.xjn819.com/?p=543) 3.1 这一节，就2句命令，直接照作即可。
2. 暂时没有了

### 非常重要
1. 本EFI已经在BIOS关闭了Fast Boot / CFG Lock / VT-d / CSM，请配合食用，
  （若BIOS里没有CFG LOCK，请升级一下[https://cn.msi.com/Motherboard/support/B250M-E](https://cn.msi.com/Motherboard/support/B250M-E)
**   !!! 刷BIOS有风险，万万不可断电

2. 如果不想升级BIOS，可以阅读[https://blog.xjn819.com/?p=543](https://blog.xjn819.com/?p=543)此文中第2部分CONFIG.PLIST中红字部分即可解决

### 遗留问题

1. HD530的睡眠叫不醒问题！！这个暂时无法解决
2. 一系列的快捷键神马的，我自己用不到就没有加，请自行添加

### 其它说明 

1. 本EFI只适用微星B250M-E，同型号的B250M-F / B250M PRO (包括VHD所有) / B250M NANO 都需要单独仿冒声卡，其它没有什么问题
2. 因为是6代U，所以仿冒的机型为 IMAC17,1，如果修改该值，请配合修改 仿冒的显卡和声卡ID
3. 因为在config.plist中设置了交换command和alt,所以呼出OC菜单为 win+r
4. 其它想好再说

### 鸣谢
1. [远景论坛](https://bbs.pcbeta.com, '国内黑苹果基地')
2. [黑果小兵](https://blog.daliansky.net)
3. [XJN](https://blog.xjn819.com)
4. [宪武](https://github.com/daliansky/OC-little)
5. [OPENCORE](https://github.com/acidanthera/OpenCorePkg)
6. [独行秀才](https://shuiyunxc.gitee.io/2020/02/21/instructions/index/)
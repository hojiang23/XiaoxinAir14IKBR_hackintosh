项目在github随缘更新
https://github.com/Jiang2479/XiaoxinAir14IKBR_hackintosh/
-----------------------------------------------------------------------------------------------------
配置
[CPU] Intel i5-8250U [GPU] UHD620+Nvidia mx150（已屏蔽） [声卡] ALC236 [无线网卡] BCM94352Z （DW1560）
-----------------------------------------------------------------------------------------------------
Opencore说明
1. 支持11.0 Big Sur，完美度99%
2. 变频正常，机型设置为mbp15.2
3. 触摸板正常
4. 睡眠正常
5. DW1560蓝牙+Wi-Fi正常
6. Opencore版本：0.6.0
-----------------------------------------------------------------------------------------------------
注意事项
1. 请自行解锁CFG Lock，设置DVMT 64M，教程链接附在后面
**若未解锁CFG Lock，请勾选Kernel/Quirks/AppleCpuPmCfgLock及AppleXcpmCfgLock
2. USB已定制，但最好请自行定制
3. 机型设置为Macbook Pro 15.2，请自行添加smbios信息
-----------------------------------------------------------------------------------------------------
配制提示
1. i5-8250u为Kaby Lake平台
2. SSDT-PLUG.aml
  第一颗cpu位置为SB.PR00
       SSDT-EC-USBX.aml
  EC Pathing：_SB.PCI0.LPCB
  EC Name：EC0
       SSDT-PNLF.aml
  GPU ACPI pathing：\_SB.PCI0.GFX0
       SSDT-GPI0/XOSI.aml
  SBRG、GPEN均需==0
3. DVMT修改
 SaSetup
 区域（area）：0x2
 偏移（offset）：0xDF
 更改：01 to 02
4. CFG LOCK
 CpuSetup
 区域（area）：0x3
 偏移（offset）：0x3C
 更改 01 to 00
5. Wi-Fi DW1560
 设备：PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)
 pci14e4,43b1
 Big Sur下已移除4360驱动，直接使用AirportBrcmFix.kext会造成Wi-Fi无法使用
 解决办法：OC引导请在config中去除AirportBrcmFix.kext/Contents/PlugIns/AirPortBrcm4360_Injector.kext，切记请勿直接删除文件。
6. 触控板失效，参考其他教程重新驱动成功
-----------------------------------------------------------------------------------------------------
参考内容
1.《Dortania's OpenCore Install Guide》opencore安装指南，最好用
https://dortania.github.io/OpenCore-Install-Guide/
2.《Getting started with ACPI》ACPI指南
https://dortania.github.io/Getting-Started-With-ACPI/
3.《使用OpenCore引导黑苹果》
https://blog.xjn819.com/?p=543
4.《lietxia/XiaoXinAir14IML_2019_hackintosh》参考触摸板驱动方法
https://github.com/lietxia/XiaoXinAir14IML_2019_hackintosh
5.《lietxia/XiaoXinAir14IML_2019_hackintosh》DVMT修改及CFG Lock解锁
https://github.com/lietxia/XiaoXinAir14IML_2019_hackintosh/wiki/DVMT
6.《99%完美！小新Air14 OC0.5.5分享 DW1820A驱动新方法 各种疑难杂症解决办法》参考部分ssdt
http://bbs.pcbeta.com/viewthread-1842644-1-1.html
7.《Intel Coffee Lake平台完美黑苹果系统安装教程（Opencore+Catalina15.4》
https://www.bilibili.com/video/BV1hA411t7dr
-----------------------------------------------------------------------------------------------------

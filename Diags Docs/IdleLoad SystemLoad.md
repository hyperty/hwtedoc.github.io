---
author:
  name: Anna Ning
  email: Anna.Ning@quantacn.com
date: 2020-2-12
title: IdleLoad & SystemLoad
---

![docDingDong300](Smokey/img/docDingDong300.png)

# IdleLoad

* What’s the IdleLoad test?
* About the smokey test of IdleLoad\(J214\)

* SystemLoad
    * What’s the SystemLoad test?
    * About the smokey test of SystemLoad\(J214\)
* IdleLoad & SystemLoad
    * The difference between IdleLoad and SystemLoad

## What’s the IdleLoad test?

将DUT启动起来后，通过Starfire读取不同时段的key值，监控负载相关sensors的空闲状态性能。

## About the smokey test of IdleLoad\(J214\)

* run smokey
* 准备活动
* BootDiagsOS
* WifiPoweroff
* Starfire
* ShutdownDiagsOS
* 收尾工作
* 打印debug信息

### run smokey

* smokey IdleLoad \-\-clean \-\-run
* smokey IdleLoad\_EG \-\-clean \-\-run
* smokey IdleLoad\_IG \-\-clean \-\-run
* Smokey <span style="color:#FDCDC4">\-\-clean</span> \-\-run IdleLoad <span style="color:#B4FFCC">\-\-testargs</span> '"Starfire Idle",SpecPath="nandfs:\\\\AppleInternal\\\\Diags\\\\Logs\\\\Smokey\\\\IdleLoad\\\\FactorySpecific\.lua'"

![](Smokey/img/IdleLoad_SystemLoad0.png)

### 准备活动

* RamlogInit
* DumpNVRAM
* DumpNandDebugCounters

![](Smokey/img/IdleLoad_SystemLoad1.png)

![](Smokey/img/IdleLoad_SystemLoad2.png)

![](Smokey/img/IdleLoad_SystemLoad3.png)

![](Smokey/img/IdleLoad_SystemLoad4.png)

### BootDiagsOS

* 查询x86端状态

* smc write FAC1 1

* boot diagsos

* DumpPCIe

* rm \-f /mnt/shell\.log

  ![IdleLoad_SystemLoad4](./Smokey/img/IdleLoad_SystemLoad4.png)

![IdleLoad_SystemLoad5](./Smokey/img/IdleLoad_SystemLoad5.png)

### WifiPoweroff

* smc write MPWF 0

![](Smokey/img/IdleLoad_SystemLoad6.png)

### Starfire

![](Smokey/img/IdleLoad_SystemLoad8.png)

![](Smokey/img/IdleLoad_SystemLoad9.png)

![](Smokey/img/IdleLoad_SystemLoad10.png)

![](Smokey/img/IdleLoad_SystemLoad11.png)

![](Smokey/img/IdleLoad_SystemLoad12.png)

![](Smokey/img/IdleLoad_SystemLoad13.jpg)

### ShutdownDiagsOS

![](Smokey/img/IdleLoad_SystemLoad14.png)

![](Smokey/img/IdleLoad_SystemLoad15.png)

![](Smokey/img/IdleLoad_SystemLoad16.png)

### 收尾工作

* DumpNVRAM
* SaveNVRAM
* DumpNVRAM

### 打印debug信息

* consolerouter \-t

![](Smokey/img/IdleLoad_SystemLoad18.png)

![](Smokey/img/IdleLoad_SystemLoad19.png)

# SystemLoad

  * What’s the SystemLoad test?
* About the smokey test of SystemLoad
    * run smokey
    * 准备活动\+BootDiagsOS\+WifiPoweroff
    * EnableBacklightControl
    * TurnBacklightOn
    * Starfire
    * ShutdownDiagsOS\+ 收尾工作\+打印debug信息

## What’s the SystemLoad test?

将DUT启动起来后，开启Backlight。通过fio模拟机器运行读取不同时段的key值，监控负载相关sensors的性能状态。

## About the smokey test of SystemLoad

### EnableBacklightControl

* i2c \-\-devwrite 10 0x09 0x67 0x02

### TurnBacklightOn

* i2c \-\-devwrite 10 0x09 0x68 0xFF 0xFF

![](Smokey/img/IdleLoad_SystemLoad20.png)

![](Smokey/img/IdleLoad_SystemLoad21.png)

### Starfire

![](Smokey/img/IdleLoad_SystemLoad22.png)

![](Smokey/img/IdleLoad_SystemLoad23.png)

https://fio\.readthedocs\.io/en/latest/fio\_doc\.html\#i\-o\-type

![](Smokey/img/IdleLoad_SystemLoad24.png)

![](Smokey/img/IdleLoad_SystemLoad25.png)

# Difference
## 机器状态

Idle:no stressors

System:使用fio模拟机器运行\(通过对memory\,cpu\,storage施加 stressor\)


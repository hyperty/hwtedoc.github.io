---
author: Nancy
date: 2019-9-5
title: Diags Learning
---

# Astro (Runin测试软件) 介绍

* Astro是一个取代Earthbound的Runin测试软件, 下面是关于其基本介绍：
  * Sequence: 很简单，可以理解为一个预设好的测试项目的合集, 比如测试所有测试项的“burnin” sequence或是单独某些测试项的testflow集合。
  * 如果机器正在跑Runin测试\,那么跑Runin测试所用的测试工具Astro会在MacOS下以Flint窗口的形式显示其运行状态。如下图：
    * 蓝色窗口表示Astro正在跑测试
    * 绿色窗口表示Astro已经跑完而且测试结果是Pass
    * 红色窗口表示Astro跑完了 而且测试结果有Fail item
  * 在gOS串口下輸入`astro status sequence` \(Ex: astro status burnin\)
    * 在gOS串口輸入的話會有時間戳記
    * 在MacOS底下透過eos\-ssh輸入的話沒有時間戳記

![](Diags_learning/img/0905Nancy0.png)

![](Diags_learning/img/0905Nancy1.png)

![](Diags_learning/img/0905Nancy2.png)

* _Astro会不会运行是根据gOS boot\-args的设定决定的,_  <span style="color:#0433FF">gOS boot\-args astro=sequence</span>  _\(例如: astro=burnin 代表astro跑burnin这个sequence\)_
  * <span style="color:#0433FF">OSDToolbox bootargs \-a astro=sequence</span>  (直接设定gOS boot\-args里的astro的值, 若在gOS下则可直接输入指令，若在macOS端则需先打开terminal输入eos-ssh进到gOS下)
  * <span style="color:#0433FF">OSDToolbox bootargs \-r astro</span>  (清掉astro sequence设定, 此指令在停止astro测试时使用，测试停掉后会显示如下的黄色Flint)
    * Astro被停止
    * 如果gOS boot\-args astro沒有设定任何sequence,则会出现如下的黑色Flint\.
* 如何停止Astro？
* \- <span style="color:#0433FF">eos\-ssh</span>
* \- <span style="color:#0433FF">OSDToolbox bootargs \-r astro</span>  _\(清掉gOS boot\-args astro的值\)_
* \- <span style="color:#0433FF">killall \-9 Astro</span>  _\(A记得要大写\)_

![](Diags_learning/img/0905Nancy3.jpg)

![](Diags_learning/img/0905Nancy4.jpg)

![](Diags_learning/img/0905Nancy5.jpg)

* 另外一种停止Astro的方法是：
  * 连接Potassium,强制按住机器Power键，直到连接31337port窗口吐出Log，然后松开power键，然后按住Enter键，使得机器进入Recovery mode
  * _当机器处于Recovery mode时, `printenv`查看机器当前的环境和参数设置_
  * `setenv boot\-args="xxx"` (Remove astro=burnin\)
  * `printenv`

![](Diags_learning/img/0905Nancy6.png)

1\. 如何得到Goku Crash Log, Terminal Log, Goku Log, System\.log

\- 以Display 4123:”Solid Image \- Grey 64 Grey128\(30HZ\)”为例

\- /AppleInternal/Diagnostics/Resources/96/J132\_xvT\_PTF\.json

\- 打开Terminal，打开Goku，执行/AppleInternal/Diagnostics/GOKU/MacOS/Goku

\- 将执行的PTF档案拉至Goku\.app

\- Terminal Log:

\- Goku Log:   /AppleInternal/Diagnostics/GOKU/Logs/2019\-08\-31\_GoKu\.log

![](Diags_learning/img/0905Nancy7.png)

![](Diags_learning/img/0905Nancy8.png)

![](Diags_learning/img/0905Nancy9.png)

\- System Log:/Volumes/MaxDisk/private/var/log/system\.log

\- Crash Log:

/Volumes/MaxDisk/Library/Logs/DiagnosticReports/Goku\_2019\-08\-31\-061404\_Mac\.crash

2\. 相关文件路径

\- 查看root的版本：/AppleInternal/Diagnostics/root\.plist

\- Plugin 路径：/AppleInternal/Diagnostics/OS/Plugin

\- Frameworks 路径：/AppleInternal/Library/Frameworks/

\- PTF\.json 脚本路径：/AppleInternal/Diagnostics/Resources/\*\[project code\]/

\*\[project code\]: 103 \-> PWW\, 96 \-> PGS

![](Diags_learning/img/0905Nancy10.png)

Smokey Sequence介绍

1\. What’s the Smokey

iEFI environment test sequence, iEFI instruction set, Lua scripts…

Location at nandfs:\\AppleInternal\\Diags\\Logs\\Smokey\\…

![](Diags_learning/img/0905Nancy11.png)

Smokey Sequence介绍

2\. Smokey Sequence Structure

In the test dir: \(a\) Main\.lua, \(b\) Main\.plist and \(c\) PlatformSpecific\.lua

\(a\) Main\.lua 执行Smokey测试需要加载的头文件

\(b\) Main\.plist 档案是函数执行的顺序，在iEFI root，Lua Scripts  可以查找相应的函数

\(c\) PlatformSpecific\.lua 一般定义跟测试相关的上下限的设定

![](Diags_learning/img/0905Nancy12.png)

Smokey Sequence介绍

3\. how to run smokey

Smokey \+ DiagsOS

<span style="color:#0433FF">smokey</span>  _\-\-clean_  _\-\-run_  <span style="color:#0433FF">IdleLoad</span>  _\-\-testargs_  <span style="color:#0433FF">'"Starfire Idle"\,SpecPath="nandfs:\\AppleInternal\\Diags\\Logs\\Smokey\\IdleLoad\\FactorySpecific\.lua"'</span>

_\-\-args_ 'keep\_alive=true'

_\-\-clean:_  _Smokey\.log and PDCA\.plist should be clean before running_

_Note: You can use "zerofile" or remove files in gOS_

_\-\-testargs_  _:_  _Current test Arguments_

_\-\-args_  _:_  _Global test Arguments_

4\. smokey sequence

Smokey \+ DiagsOS

Take TDiags_learning/imgPU as an example：

A series of stress tests that collect performance data\.

_TDiags_learning/imgPU stress 温度检测:_  <span style="color:#0433FF">smokey \-\-clean \-\-run TDiags_learning/imgPU \-\-args 'keep\_alive=true'</span>

Smokey Sequence介绍

![](Diags_learning/img/0905Nancy13.png)

![](Diags_learning/img/0905Nancy14.png)

![](Diags_learning/img/0905Nancy15.png)

![](Diags_learning/img/0905Nancy16.png)

![](Diags_learning/img/0905Nancy17.png)

Smokey Sequence介绍

_https://www\.icloud\.com/numbers/0ZcmOdktcWrnn\_SghARYsggnw\#Diags\-Smokey\-Sequence\-Nancy_

![](Diags_learning/img/0905Nancy18.png)

Smokey Sequence介绍

TDiags_learning/imgPU:  Main\.plist

![](Diags_learning/img/0905Nancy19.png)

![](Diags_learning/img/0905Nancy20.png)

Smokey Sequence介绍

Visual Stadio Code : 打开Smokey资料夹

![](Diags_learning/img/0905Nancy21.png)

Smokey Sequence介绍

__进入__ IG \(Internal Graphic\)

<span style="color:#0433FF">sudo nvram GfxMode=I</span>

reboot

进入EG \(External Graphic\)

<span style="color:#0433FF">sudo nvram GfxMode=E</span>

reboot

重启之后查看 about this Mac \->Overview Graphics

![](Diags_learning/img/0905Nancy22.jpg)

Boot Spartacus Issue

使用Runin 跑过测试的机器，有时MacEFI启动不起来

iEFI env:

DIAG: boot\.efi  startup\.nsh  spartacus\.efi

<span style="color:#0433FF">x86 boot \-\-bootstate diagsos</span>  _在boot diagsos时，DUT屏幕上面出现_  <span style="color:#FF2600">黑色的禁止符号</span>  _，经分析可能的原因是：_

\- DIAG下没有boot\.efi binary

从MacDisk  /AppleInternal/Diagnostics/boot\.efi binary复制至DIAG的根目录下

\- DIAG下startup\.nsh 里面的脚本被修改，不是启动spartacus的指令

从MacDisk  /AppleInternal/Diagnostics/startup\_spartacus\.nsh 复制至DIAG的根目录下重命名为startup\.nsh

1\. 移动文件

<span style="color:#0433FF">mv</span>  <span style="color:#0433FF">原始文件 目标文件</span>

2\. 复制文件

<span style="color:#0433FF">cp 原始文件 目标文件</span>

3\. 列出当前目录下的所有文件

<span style="color:#0433FF">ls</span>

4\. 显示当前目录的路径

<span style="color:#0433FF">pwd</span>

5\. 查看档案内容

<span style="color:#0433FF">cat 目标文件</span>

6\. 查看档案内容（文件过大时）

<span style="color:#0433FF">head \-n rowNum 目标文件</span>

<span style="color:#0433FF">tail \-n rowNum 目标文件</span>

7\.查找文件

<span style="color:#0433FF">find \./路径 \-name \*FLOW\.txt</span>

8\. 进入某个目录

<span style="color:#0433FF">cd 目标文件</span>

9\. 删除文件

<span style="color:#0433FF">rm \-f</span> 强制删除

<span style="color:#0433FF">rm \-i</span> 删除前确认

<span style="color:#0433FF">rm \-r</span> 删除目录以及子目录文件

10\. 将Macos文件copy到gos下：

<span style="color:#0433FF">eos\-scp macos文件/路径 eos:/gos文件/路径</span>

11\. 将gos文件copy到macos下：

<span style="color:#0433FF">eos\-scp eos:/gos文件/路径 macos文件/路径</span>

12\. root安装与卸载

安装macos root: <span style="color:#0433FF">darwinup install root文件</span>

安装gos root： <span style="color:#0433FF">eos\-darwinup install root文件</span>

卸载root： <span style="color:#0433FF">darwinup uninstall root文件</span> \(gos同理）

查看root: <span style="color:#0433FF">darwinup list</span> \(gos root需进入gos下查看）

13\. Transfer files to/from MacEFI or DiagsOS

<span style="color:#0433FF">x86 xfer \<source> \<destination></span>

<span style="color:#0433FF">x86 xfer nandfs:\\AppleInternal\\Diags\\logfile hd2:\\logfile</span>

<span style="color:#0433FF">x86 xfer /tmp/file\.txt nandfs:\\AppleInternal\\Diags\\tmp\\file\.txt</span>

Display 2494\, 换之前屏幕下方有出现白线的问题：

![](Diags_learning/img/0905Nancy23.png)

以TDiags_learning/imgPU 温度检测 P2 ~ 40w为例

启动 iEFI env 执行Smokey TDiags_learning/imgPU测试

修改/root/amddiags\.sh,使其stress之后达到期望值 P2 ~ 40w  GP0R ~ 40w

Diagsos env: /root/amddiags\.sh

iEFI env:

<span style="color:#0433FF">x86 boot \-\-bootstate diagsos</span>

<span style="color:#0433FF">x86 xfer /root/amddiags.sh nandfs:\amddiags.sh</span>

<span style="color:#0433FF">smokey \-\-clean \-\-run TDiags_learning/imgPU \-\-args 'keep\_alive=true'</span>

_新开一个Terminal窗口，输入_  <span style="color:#0433FF">/Users/nancy/Diags/usbfs\-2\.4\.254 \-f \./Desktop</span>

iEFI env:

<span style="color:#0433FF">usbfs \-m</span>

<span style="color:#0433FF">cp \-r nandfs:\\AppleInternal\\Diags\\Logs\\Smokey\\TDiags_learning/imgPU usbfs:</span>

<span style="color:#0433FF">x86 xfer nandfs:\\amddiags\.sh /root/amddiags\.sh</span>

![](Diags_learning/img/0905Nancy24.png)

![](Diags_learning/img/0905Nancy25.png)

tGraph 温度检测工具，可以实时侦测数据，方便测试。

![](Diags_learning/img/0905Nancy26.png)

![](Diags_learning/img/0905Nancy27.png" width=222px />

![](Diags_learning/img/0905Nancy28.png)

![](Diags_learning/img/0905Nancy29.png)

![](Diags_learning/img/0905Nancy30.png)


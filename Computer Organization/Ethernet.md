---
author: 
    name: Whiteny Ren
    email: Whitney.Ren@quantacn.com
date: 2019-1-14
title: Ethernet 
---
# Ethernet Brief introduction

一、**Ethernet**发展历史

> 1973年， Xerox公司提出以太网技术并实现之，最初以太网数率只有2.94Mbps
>
> 1980年， Digital Equipment Corporation
> ，Intel，Xerox，三家联合推出10Mbps DIX以太网标准
>
> 1995年，IEEE正式通过了802.3u快速以太网标准
>
> 1998年，IEEE802.3z千兆以太网标准正式发布
>
> 1999年，发布IEEE802.3ab标准，即1000BASE-T标准
>
> 2002年7月18日，IEEE通过了802.3ae，即10Gbit/s以太网，又称为万兆以太网，它包括了10GBASE-R,10GBASE-W,10GBASE-LX4三种物理接口标准。

2004年3月，IEEE批准铜缆10G以太网标准802.3ak，新标准将作为10GBASE-CX4实施，提供双轴电缆上的10Gbps的速率。

<center>
    <img src="img/Ethernet0.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图1. Ethernet 发展历史
    </div>
</center>

二、简述**Ethernet**

以太网(Ethernet)是一种计算机局域网技术。

以太网的标准拓扑结构为总线型拓扑，但目前的快速以太网(100BASE-T、1000BASE-T标准)为了减少冲突，将能提高的网络速度和使用效率最大化，使用集线器来进行网络连接和组织。如此一来，以太网的拓扑结构就成了星型；但在逻辑上，以太网仍然使用总线型拓扑和CSMA/CD(即载波多重访问/碰撞侦测)的总线技术。

以太网实现了网络上无线电系统多个节点发送信息的想法，每个节点必须取得电缆或者信道才能传送信息，有时也叫作以太。每个节点有全球唯一的48位地址也就是制造商分配给网卡的MAC地址，以保证以太网上所有节点能相互鉴别。由于以太网十分普遍，许多制造商把以太网卡直接集成进计算机主板。

三、以太网的传输介质

以太网的连接介质有同轴电缆、双绞线、光纤等有线介质。

\[一\] 同轴电缆

早期的以太网一般是一根同轴电缆连接多台终端，因此通过这种连接方式形成的网络叫做共享介质网络。IEEE802.3中使用两种同轴电缆，分别为10BASE5（又名粗缆）和10BASE2（又名细缆），并且都保持10Mbps的传输速率。

<center>
    <img src="img/同轴电缆.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图2. 同轴电缆
    </div>
</center>

1）粗缆

连接粗缆时必须安装收发器，且可以在不影响其他设备使用的情况下增设收发器，收发器和PC端的NIC（Network
Interface
Card，网卡）之间通过收发器电缆连接。

<center>
    <img src="img/粗缆.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图3. 粗缆
    </div>
</center>

2）细缆
与粗缆不同的是，10BASE2通过BNC（又称T型连接器）与设备连接，但是新增线路时需要切断电缆。

<center>
    <img src="img/细缆.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图4. 细缆
    </div>
</center>

\[二\] 双绞线

双绞线电缆（简称双绞线）是将成对的导线封装在绝缘外套中而成的传输介质，具有比一般导线更强的抗噪性。双绞线有很多种类型。因为其便宜，短距离传输快的优点，已经成为目前以太网（10BASE-T、100BASE-TX、1000BASE-T）中最常用的布线材料。

1）双绞线的绕对组合

通常两根铜线组成一个绕对，四个绕对（两个发送数据，另外两个发送指令，以实现全双工通信）用套管包成一条双绞线。双绞线两端可以连接交换机、集线器（现在很少人用了，相当于交换机的前身）等通信设备。

2）双绞线的分类

双绞线分为屏蔽双绞线（Shielded Twisted
Pair，STP）和非屏蔽双绞线（Unshielded Twisted
Pair，UTP）两种。UTP的内部有一个个绕对，而STP在套层和绕对之间添加了一个绝缘的屏蔽层，可以防止电磁的干扰，如图：

<center>
    <img src="img/双绞线.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图5. 双绞线
    </div>
</center>
虽然STP比UTP的抗干扰性更强，但布线复杂和昂贵的价格是它的主要缺点。

双绞线的标准

| **Category** |        **是否屏蔽**        |   **最大传输速度**   | **最大** **频宽** |
| :----------: | :------------------------: | :------------------: | :---------------: |
| **CAT - 3**  |         **非屏蔽**         |       10 Mbps        |       16MHz       |
| **CAT - 4**  |         **非屏蔽**         |       16 Mbps        |       20MHZ       |
| **CAT - 5**  |         **非屏蔽**         |       100 Mbps       |      100MHz       |
| **CAT - 5e** |         **非屏蔽**         |  1000 Mbps / 1 Gbps  |      125MHz       |
| **CAT - 6**  | **屏蔽** **或** **非屏蔽** |  1000 Mbps / 1 Gbps  |      250MHz       |
| **CAT - 6A** |          **屏蔽**          | 10000 Mbps / 10 Gbps |      500MHz       |
| **CAT - 7**  |          **屏蔽**          | 10000 Mbps / 10 Gbps |      600MHz       |
| **CAT - 8**  |          **屏蔽**          |        40Gbps        |      2000MHz      |

\[三\] 光纤

光纤的主要应用场景为：实现同轴电缆和双绞线无法实现的远距离连接；防止噪声等外界的干扰；为了高速传输。

光纤的分类

1）多模光纤

多模光纤的纤芯直径较大，易于制作，可以同时传播多种波长的光（通过折射）。一般实现100Mbps左右的通讯可以采用多模光纤。但是因为模间色散程度较大，所以多模光纤的传输距离一般只有几公里。

<center>
    <img src="img/多模光纤.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图6. 多模光纤
    </div>
</center>

2）单模光纤

单模光纤的纤芯一般为数微米，对制造工艺的要求较高。由于其中模间的色散很小（材料色散和波导色散），所以适用于远距离的高速通讯。

<center>
    <img src="img/单模光纤.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图7. 单模光纤
    </div>
</center>

四、**CSMA/CD**共享介质以太网

带冲突检测的载波侦听多路访问(CSMA/CD)技术规定了多台电脑共享一个通道的方法。这项技术最早出现在1960年代由夏威夷大学开发的ALOHAnet，它使用无线电波为载体。这个方法要比令牌环网或者主控制网简单。当某台电脑要发送信息时，在以下行动与状态之间进行转化：

<center>
    <img src="img/CSMACD.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图8. CSMA/CD
    </div>
</center>

五、传输信道**-**差分信道

差分传输是一种信号传输的技术，区别于传统的一根信号线一根地线的做法，差分传输在这两根线上都传输信号，这两个信号的振幅相同，相位相反。在这两根线上的传输的信号就是差分信号。信号接收端比较这两个电压的差值来判断发送端发送的逻辑状态。在电路板上，差分走线必须是等长、等宽、紧密靠近、且在同一层面的两根线。

<center>
    <img src="img/差分信号.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图9. 差分信号
    </div>
</center>

六、以太网类型

各类以太网的差别仅在速率和配线。因此，同样的网络协议栈软件可以在大多数以太网上執行。

以下的章节简要综述了不同的正式以太网类型。除了这些正式的标准以外，许多厂商因为一些特殊的原因，例如为了支持更长距离的光纤传输，而制定了一些专用的标准。

很多以太网卡和交换设备都支持多速率，设备之间透過自动协商设置最佳的连接速度和双工方式。如果协商失败，多速率设备就会探测另一方使用的速率但是默认为半双工方式。10/100以太网端口支持10BASE-T和100BASE-TX。10/100/1000支持10BASE-T、100BASE-TX和1000BASE-T。

|  速度   |    常用名称    | 非正式的IEEE标准名称 | 正式的IEEE标准名称 | 线缆类型 | 最大传输距离 |
| :-----: | :------------: | :------------------: | :----------------: | :------: | :----------: |
| 10Mbps  |     以太网     |       10BASE-T       |       802.3        |  双绞线  |     100m     |
| 100Mbps |   快速以太网   |      100BASE-T       |       802.3u       |  双绞线  |     100m     |
|  1Gbps  |  吉比特以太网  |     1000BASE-LX      |       802.3z       |   光纤   |    5000m     |
|  1Gbps  |  吉比特以太网  |      1000BASE-T      |      802.3ab       |  双绞线  |     100m     |
| 10Gbps  | 10吉比特以太网 |      10GBASE-T       |      802.3an       |  双绞线  |     100m     |

七、分类发展

标准以太网

|   **标准规格**   |     **线缆类型**     | **最大网段长度** |
| :--------------: | :------------------: | :--------------: |
|  **10Base - 5**  |      粗同轴电缆      |       500m       |
|  **10Base - 2**  |      细同轴电缆      |       185m       |
|  **10Base - T**  |        双绞线        |       100m       |
|  **10Base - F**  |         光纤         |      2000m       |
| **100Base - T**  |     非屏蔽双绞线     |       100m       |
| **100Base - TX** |     非屏蔽双绞线     |       220m       |
| **1000Base - T** | 双绞线(非屏蔽或屏蔽) |       100m       |


\[1\] 10Mbps 以太网

10Mbps以太网即[标准以太网，根据IEEE 802.3 的规定，10M 以太网目前广泛使用的线缆有：10Base -T双绞线、10Base5粗同轴电缆以及10Base2 细同轴电缆。

10Base-T使用3类双绞线、4类双绞线、5类双绞线的4根线（两对双绞线）100米。10BASE－T的连接主要以集线器HUB作为枢纽(HUB将在第5节中介绍)，工作站通过网卡的RJ45插座与RJ45接头相连，另一端HUB的端口都可供RJ45的接头插入，装拆非常方便。

\[2\] 100Mbps以太网(快速以太网)

快速以太网（FastEthernet）为IEEE在1995年发表的网路标准，能提供达100Mbps的传输速度。

• 100BASE-T------ 下面三个100 Mbit/s双绞线标准通称，最远100米。

◦100BASE-TX\--类似于星型结构的10BASE-T。使用2对电缆，但是需要5类电缆以达到100Mbit/s。

◦ 100BASE-T4 \--使用3类电缆，使用所有4对线，半双工。由于5类线普及，已废弃。

◦ 100BASE-T2 \--无产品。使用3类电缆。支持全双工使用2对线，功能等效100BASE-TX，但支持旧电缆。

•
100BASE-FX\-- 使用多模光纤，最远支持400米，半双工连接(保证冲突检测），2km全双工。

\[3\]1Gbps以太网(千兆以太网)

|                         **连接标准**                         |             **介质**             |        **最大可传输距离**         |
| :----------------------------------------------------------: | :------------------------------: | :-------------------------------: |
|                       **1000Base-CX**                        |           双轴屏蔽铜缆           |                25m                |
|                       **1000Base-KX**                        |             背板铜缆             |                1m                 |
| [**1000BASE-SX**](https://zh.wikipedia.org/wiki/1000BASE-SX) |             多模光纤             | 220m-550m(由光纤的直径和带宽决定) |
| [**1000BASE-LX**](https://zh.wikipedia.org/wiki/1000BASE-LX) |        多模光纤  单模光纤        |             550m  5km             |
| [**1000BASE-LX10**](https://zh.wikipedia.org/wiki/1000BASE-LX10) | 单模光纤(使用波长为1310nm的激光) |               10km                |
|                       **1000Base-EX**                        | 单模光纤(使用波长为1310nm的激光) |             超过40km              |
| [**1000BASE-ZX**](https://zh.wikipedia.org/wiki/1000BASE-ZX) | 单模光纤(使用波长为1550nm的激光) |             超过70km              |
|                        **1000Base-T**                        | 双绞线（CAT-5/CAT-5e/CAT-6/CAT-7 |               100m                |
|                       **1000Base-TX**                        |      双绞线（CAT-6/CAT-7）       |               100m                |

\[4\] 10Gbps以太网(万兆以太网)

新的万兆以太网标准包含7种不同类型，分別适用于局域网、城域网和广域网。目前使用附加标准[IEEE
802.3ae，将来会合并进IEEE802.3标准。

|                       **连接标准**                       |           **介质**           |   **最大可传输距离**   |
| :------------------------------------------------------: | :--------------------------: | :--------------------: |
|                     **10GBASE-CX4**                      |             光纤             |          15m           |
|                      **10GBASE-SR**                      |             光纤             |          400m          |
|                     **10GBASE-LX4**                      |      多模光纤  单模光纤      | 300m(多摸)  10km(单摸) |
|                      **10GBASE-LR**                      |             光纤             |          10km          |
|                      **10GBASE-ER**                      |             光纤             |          40km          |
| [**10GBASE-T**](https://zh.wikipedia.org/wiki/10GBASE-T) | 双绞线（CAT-6/CAT-6A/CAT-7） |          100m          |
|                     **10GBASE-KX4**                      |           PCB背板            |           1m           |

\[5\] 100Gbps以太网

新的40G/100G以太网标准在2010年中制定完成，包含若干种不同的节制类型。目前使用附加标准IEEE802.3ba。

|          **连接标准**           |  **介质**  | **最大可传输距离** |
| :-----------------------------: | :--------: | :----------------: |
|         **40GBASE-KR4**         |  PCB背板   |         1m         |
| **40GBASE-CR4 / 100GBASE-CR10** | 短距离铜缆 |         7m         |
| **40GBASE-SR4 / 100GBASE-SR10** |  多模光纤  |      超过100m      |
| **40GBASE-LR4 / 100GBASE-LR10** |  单模光纤  |      超过10km      |
|        **100GBASE-ER4**         |  单模光纤  |      超过40km      |

八、相关测试

|      **Category**      | Test ID |                      Test Name                       | SOC Env |     Intel env     |
| :--------------------: | :-----: | :--------------------------------------------------: | :-----: | :---------------: |
| **EthernetController** |  2438   |               Mac Address Verify Test                |   EFI   | MacEFI(spartacus) |
|        **PCIe**        |  8186   |               Reset Errors Test [EFI]                |   EFI   | MacEFI(spartacus) |
|        **PCIe**        |  8008   |                Link Speed Test [EFI]                 |   EFI   | MacEFI(spartacus) |
|        **PCIe**        |  8016   |                Link Width Test [EFI]                 |   EFI   | MacEFI(spartacus) |
|        **PCIe**        |  8070   |                Error Rate Test [EFI]                 |   EFI   | MacEFI(spartacus) |
|        **PCIe**        |  8106   | Standard Register Test (Device Identification) [EFI] |   EFI   | MacEFI(spartacus) |

J185 SMT QT Ethernet test

<center>
    <img src="img/EthernetTest.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图10. J185 SMT QT Ethernet test
    </div>
</center>

Ethernet 吞吐量 (Throughput)的测试

J185 EthernetDOE

<center>
    <img src="img/EthernetDOE.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图11. J185 EthernetDOE
    </div>
</center>

J160 Ethernet Controller Loop back throughout test

<center>
    <img src="img/Ethernetloopbackthroughput.png" width=500px //>
    <br>
    <div style="color:orange; solid:#d9d9d9; display:inline-block; color:#999; font-size:14px">
        图12. J160 Ethernet Controller Loop back throughout test
    </div>
</center>
# 		                                           SMA-BRB 应用指导书 





<img>![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/LOGO.bmp)

**版本V1.0** 

**版权©2019** 







##                                                                                                                                                                                                                            	     关于本手册

本手册介绍了SMA-BRB 产品参数，包含以下章节

| 章     | **标题**           | **内容**                           |
| :----- | :----------------- | :--------------------------------- |
| 第一章 | 产品简介           | 概述SMA-BRB的特点和功能应用        |
| 第二章 | 功能描述           | 描述模块功能及具体说明             |
| 第三章 | 电气特性           | 介绍模块的电气性能基本参数         |
| 第四章 | 模块类型及管脚定义 | 提供模块类型、管脚定义功能说明     |
| 第五章 | PCB设计            | 提供了模块布局及PCB layout注意事项 |
| 第六章 | 封装信息           | 提供模块封装尺寸图                 |
| 第七章 | 参考设计           | 提供模块外部电路的参考设计         |







## 一、  产品简介						

SMA-BRB 是深圳酷宅科技有限公司(简称：酷宅科技)开发的智能门铃模块，主要包含本地按键功能、通过家庭网关接入网络与云端数据交互功能、局域网内通信功能、OTA功能，基于上述功能，用户可以实现本地切换门铃音乐、APP远程接收门铃及报警触发记录、设置模式、配置参数和查询状态等功能。  

主要应用领域：智能家居

   **产品特性**

- 支持无线802.11 b/g/n 标准
- Wi-Fi @2.4 GHz，支持WPA/WPA2安全模式
- 802.11b 模式下+20.5dBm的最大输出功率
- UMA认证标准
- 支持定时器操作
- 支持对 433MHZ 载波门磁键值的学习
- 支持 Wi-Fi 远程控制 
- 支持兼容配对模式 / 快速配对模式
- 支持OTA升级



## 二、功能描述

### 2.1 模块功能

SMA-BRB内置我司IoT协议，可动态、实时的参与与云端服务器、移动终端APP的三方数据交互。本应用中，Wi-Fi模块作为Station连接路由，通过Internet实现设备端事件上报和云服务器下发数据解析。

按键用于控制设备进入配置模式，与APP终端配合加入网络。Wi-Fi状态灯表征设备当前的网络状态，状态详解见2.2节。

以下功能是搭配酷宅门铃方案所实现功能：

#### 2.1.1 本地按键控制

1. 配网按键

   长按：长按配网按键大于5S进入配网模式。

   双击：双击配网按键进入RF433学习状态，默认添加为门铃按钮（不使用APP添加），不能超出16个。

   注：如果设备已存有要学习的门铃或报警器键值，将会学习失败，设备不会再保存新学习的门铃或报警器键值。但蜂鸣器仍然会响两声。

2. 切换门铃声按键：在非报警时段短按为切换门铃音乐功能，报警时段短按为关闭报警声功能。 

![image-20191105185134766](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191105185134766.png)

​		注：2.1.    短按按键触发逻辑为抬起触发。

​				2.2.    按键短按：按下时长t1大于75ms、小于3S且抬起时长t2大于75ms。

​					a)    OTA模式下，按键无效；

​					b)   配网模式下，按键有效；

​				2.3.	按键操作频率不高于3次/S，否则可能无效。

#### 2.1.2 门铃音乐

1. 门铃音乐有两种：

   a) 叮咚一声

   b) 叮咚两声 

2. 可短按切换铃声按键进行铃声切换。

3. 不论有无网络，已配对门铃都能正常操作，即离线情况下按下按钮门铃会响，门铃按钮在布防撤防模式下都正常使用。

4. 3秒内多次触发门铃按钮只响一次。

#### 2.1.3 报警提示声 

1. 报警提示声优先级高于门铃，即报警声响起时，门铃触发不响只上报记录。
2. 报警提示声使用叮咚一声，采用连续周期400ms高频触发的方式制作报警声，持续报警直到用户短按铃声切换按键或设置撤防模式。
3. 长按铃声切换按键只停止播放当前的报警声，若之后报警器又触发，报警声再次播放。
4. 配网时，若门铃或报警器触发，设备将播放门铃音乐或报警声。
5. 在布防状态下，报警声响起时，接收到的门铃和报警器触发信号记录都要上传至云端和局域网。
6. 报警声响起时(报警器A触发的)，若报警器A重复触发，不上报；若此时报警器B触发，触发的第1次上报，重复触发不上报，报警器C以此类推，避免重复多次上报增加服务器负担。

#### 2.1.4 布防撤防状态设置

用户可以在APP上设置报警器布防撤防状态：

1. 开启布防状态后，若报警器触发，门铃设备应发出报警声并上报记录至云端与局域网；

2. 开启撤防状态后，若报警器触发，门铃设备应上报记录至云端与局域网，但不发出报警声；

注意事项：门铃音乐播放及其记录上报不受布防撤防状态影响。

#### 2.1.5 学习门铃按钮或报警器功能

1. 通过app选择门铃或报警器，并下发学习指令使设备进入学习模式。

2. 学习模式的退出条件：

   a) 学习1分钟超时

   b) app下发学习退出指令

   c) 学习成功

3. 可以重复学习相同的门铃或报警器。

注意事项：仅支持最多16个门铃或报警器的学习，若已满16个，设备将不会进入学习模式。

#### 2.1.6 延时布防

         软件支持延时设置布防和单次定时设置布防、撤防功能 。

- 延时布防:	对布防的延时设置，可设置0-300s，0表示无延时，其它数值为延时时长。
- 单次定时设置布防，撤防功能：可以设置在某一天的某个时间点进行布防，撤防等操作。


### 2.2 Wi-Fi状态灯闪烁方式说明

            设备端Wi-Fi状态灯的闪烁方式表征设备当前的网络工作状态，具体状态包括以下七种：

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/LED%E7%81%AF%E9%97%AA%E7%83%81%E8%AF%B4%E6%98%8E.bmp)

​	                                                设备状态与Wi-Fi状态灯闪烁方式关系示意图



Wi-Fi状态灯的闪烁特征以2秒为一个周期，如图所示，低电平灯亮，高电平灯灭。各状态详解：

A. 	Normal : 设备正常工作，与云服务器连接正常。此时可以通过APP操控设备。在其它任何模式下，都无法通过 APP操控设备。

B.	NO Wifi：设备无法连接到无线路由器。

C.	No Server：设备已经连接上无线路由器，但是无法连接到服务器（就是通常理解下的“无法上网”）。

D.	Unregistered：表示设备还没有被绑定到任何账户下。一般的，设备需要与易微联账号绑定才可与服务器通信。在易微联APP“添加设备”可完成绑定操作。

E.	Upgrade：表示设备正在固件升级。

F.	Setting G1：表示设备正处于兼容配对模式。配置模式用于设备获取移动终端APP提供的加入服务网络比要信息，包括路由器ssid、password和服务器ip、端口号等。

G.	Setting G2：表示设备正处于快速配对模式。配置模式用于设备获取移动终端APP提供的加入服务网络的必要信息，包括路由器ssid、password和服务器ip、端口号等。两种配置，设备获取相关信息的方式不同，详见下节所述。





### 2.3 Wi-Fi模块的基本工作流程

#### 2.3.1 配置

设备模块在未加入局域网时就是一个“信息孤岛”，设备端操作配合易微联APP设置，使设备获取加入服务网络的必要信息，包括路由器ssid、password和服务器ip、端口号等。模块内置两种配置方式：

1. 兼容配对模式：移动终端作为station加入该AP组成局域网实现数据交互。快速配对模式（G状态，详情见2.2 Wi-Fi状态灯闪烁方式说明）下长按配置按键5S，设备进入兼容配对模式。点击易微联APP添加设备（iOS移动终端需在“设置”菜单内手动连接ssid：ITEAD-10000XXXX， password12345678的热Android终端无需此操作），输入家庭路由器的ssid和password，完成设备的上线准备工作。
2. 快速配对模式：此方式Wi-Fi模块处于混杂模式（Wi-Fi Promiscuous），通过空快速配对模式：此方式Wi-Fi模块处于混杂模式（Wi-Fi Promiscuous），通过空空抓包的形式获取移动终端发出的包含ssid和password等信息的加密报文。上节所述A~D任意一个状态内长按配置按键5S，设备进入快速配对模式。点击易微联APP添加设备，输入家庭路由器的ssid和password，完成设备的上线配置工作。

#### 2.3.2 上线

设备模块从上电到连接服务器，需经历以下流程：

1. 加入所配置路由器，连接Internet。
2. 连接服务器。
3. 注册设备，绑定至易微联账户。
4. 获取设备应用参数，保持在线 。

​	以上各个步骤，当连接/获取失败时，均有相应的退避策略和重连接机制，确保设备稳定、实时在线。

#### 2.3.3 OTA升级

模块设备连接升级服务器，下载更新至最新版本固件，实现设备的在线升级。





























## 三、电气特性

####      3.1 额定参数

    条件：VDD=3.3V±10%，GND=0V；室温25°C下测试。

|     型号     |                           类型                           |
| :----------: | :------------------------------------------------------: |
|     型号     |                         PSF-BRB                          |
|   硬件接口   |                        UART，GPIO                        |
|   工作电压   |                        2.7V~3.6V                         |
| GPIO驱动能力 |                        Max：12mA                         |
|   工作电流   | 平均电流：≈80mA，<br>最大工作电流：210mA<br>待机: <200uA |
|   工作温度   |                          0℃~45℃                          |
|   存储环境   |          温度：-10℃~75℃，相对湿度：20%RH~80%RH           |
| 无线网络类型 |                      STA/AP/STA+AP                       |
|   安全机制   |                   WEP/WPA-PSK/WPA2-PSK                   |
|   加密类型   |                  WEP64/WEP128/TKIP/AES                   |
|   固件升级   |                       OTA 远程升级                       |



####      3.2 Wi-Fi 参数  

​	条件：VDD=3.3V±10%，GND=0V；室温 25°C 下测试。 

|    类型    | 参数                                                         |
| :--------: | ------------------------------------------------------------ |
|  无线标准  | IEEE 802.11b/g/n                                             |
|  频率范围  | 2.412GHz-2.484GHz                                            |
|  发射功率  | 802.11b: 20±2dBm (@11Mbps)<br>802.11g: 17±2dBm (@54Mbps)<br>802.11n: 14±2dBm (@HT20,MCS7) |
| 接收灵敏度 | 802.11b: -91 dBm (@11Mbps ,CCK)<br>802.11g: -75 dBm (@54Mbps, OFDM)<br>802.11n: -72 dBm (MCS7) |
|  天线类型  | PSF-BRB：陶瓷贴片天线                                        |







#### 3.3 WIFI射频指标

条件：VDD=3.3V±10%，GND=0V；室温25°C下测试。

| 描述                               | 最小值 | 典型值 | 最大值 | 单位 |
| :--------------------------------- | :----: | :----: | :----: | :--: |
| 输入频率                           |  2412  |   -    |  2484  | MHz  |
| 输出阻抗                           |   -    |   50   |   -    |  Ω   |
| 输入反射                           |   -    |   -    |  -10   |  dB  |
| 72.2Mbps 下， PA 的输出峰值功率    |  15.5  |  16.5  |  17.5  | dbm  |
| 802.11b 模式下， PA 的输出峰值功率 |  19.5  |  20.5  |  21.5  | dbm  |



#### 	3.4 灵敏度

| 描述                          | 最小值 | 典型值 | 最大值 | 单位mA |
| ----------------------------- | ------ | :----: | ------ | :----: |
| CCK 1Mbps                     |        |  -98   |        |  dBm   |
| CCK 11Mbps                    |        |  -91   |        |  dBm   |
| 6Mbps(1/2BPSK)                |        |  -93   |        |  dBm   |
| 54Mbps(3/4 64-QAM)            |        |  -75   |        |  dBm   |
| HT20，MCS7（65Mbps，72.2Mbps) |        |  -72   |        |  dBm   |



#### 	3.5 邻频抑制

| 描述         | 最小值 | 典型值 | 最大值 | 单位mA |
| ------------ | ------ | :----: | ------ | :----: |
| OFDM，6Mbps  |        |   37   |        |   dB   |
| OFDM，54Mbps |        |   21   |        |   dB   |
| HT20，MCS0   |        |   37   |        |   dB   |
| HT20，MCS7   |        |   20   |        |   dB   |

 注：

        1. 72.2Mbps是在802.11n模式下，MCS=7，GI=200uS时测得。

        2. 802.11b模式下最高可达+21.5dBm的输出功率。







## 四、模块类型及管脚定义

####      4.1 脚位排列顺序

SMA-BRB模块提供配对按键，铃声切换按键，Wi-Fi指示灯接口，软件UART串口，UART串口，铃声控制io口。

<img src="https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/SMA%E6%A8%A1%E5%9D%97%E9%A1%B6%E5%B1%82%E8%84%9A%E4%BD%8D%E5%9B%BE.bmp" alt="图片描述" style="zoom:80%;" />

                                                       	      模块引脚顶视图



<img src="https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/SMA%E6%A8%A1%E5%9D%97%E4%BD%8E%E5%B1%82%E8%84%9A%E4%BD%8D%E5%9B%BE.bmp" alt="图片描述" style="zoom:80%;" />

                                                              模块引脚低视图





####    4.2 管脚定义

    													**管脚定义及功能说明表**

| 管脚 | 名称   | 功能                                                         |
| ---- | ------ | ------------------------------------------------------------ |
| 1    | 3V3    | 电源                                                         |
| 2    | TX     | 模块UART-TX,与EFM8BB10F通信                                  |
| 3    | RX     | 模块UART-TX,与EFM8BB10F通信                                  |
| 4    | GPIO15 | 注：芯片配置脚，需要下拉（1~4.7K）电阻到地                   |
| 5    | GPIO4  | 软串口RX，工厂模式用。                                       |
| 6    | GPIO5  | 软串口TX，工厂模式用。                                       |
| 7    | GPIO12 | 通用GPIO，控制铃声2                                          |
| 8    | GPIO2  | NC                                                           |
| 9    | TOUT   | ADC端口、NC                                                  |
| 10   | GPIO0  | 1、配网按键引脚，低电平有效<br/>2、双击配网按键进入RF433学习状态，默认添加为门铃设备（不使用APP添加），最多学习16个。 |
| 11   | E-D2   | GPIO9,控制铃声1                                              |
| 12   | E-D3   | GPIO10,切换铃声按键输出入，低有效。                          |
| 13   | GPIO14 | NC                                                           |
| 14   | GPIO13 | Wi-Fi状态指示灯，接LED灯串联限流电阻到3V3                    |
| 15   | GPIO16 | NC                                                           |
| 16   | GND    | GND                                                          |



## 五、PCB设计

 **PCB layout 与模块布局注意事项：**

1. 在PCB layout时注意模块摆放位置，特别是模块的天线部分，尽可能远离干扰源：磁性元件(如马达、电感、变压器等)、高频信号器件（如晶振、高频时钟信号等）。

2. 模块摆放位置的PCB上下层尽可能不要走线，做覆铜包地处理，模块天线到模块最近引脚部分的PCB尽可能做挖空处理。

3. 模块PCB天线区域及外扩 15 mm 区域需净空（严禁铺铜、⾛线、摆放元件）

4. 模块的电源（VCC）引脚电容和模块其他引脚电容、电阻尽可能靠近模块引脚摆放，走线路径要短。





## 六、封装信息	

             封装尺寸图：

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/SMA%E6%A8%A1%E5%9D%97%E5%B0%81%E8%A3%85%E5%B0%BA%E5%AF%B8%E5%9B%BE.bmp)









## 七、参考设计

本章节是酷宅门铃方案的参考说明，该方案使用EFM8和AC8DD12。

### 7.1参考原理图

![](https://github.com/junlin-chen/img/raw/master/%E5%8F%82%E8%80%835.png)



<img src="https://github.com/junlin-chen/img/raw/master/%E5%8F%82%E8%80%834.png" style="zoom:80%;" />

### 7.2 编码说明

SMA-BRB支持学习PT2260、PT2264、EV1527等系列固定码门磁感应设备的键值，不支持滚动码。其编码方式如下所示：

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/%E7%BC%96%E7%A0%81%E8%AF%B4%E6%98%8E%E5%9B%BE.bmp)

                                                           SMA-RBR编码单帧数据示意图



包括同步码和24bit数据码。其中：

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/%E7%BC%96%E7%A0%81%E6%B5%81%E7%A8%8B%E5%9B%BE1.bmp)



                                                          SMA-BRB遥控编码方式解析示意图



**注**：不支持其他编码方式的遥控器。

### 7.3 协议说明

- SMA-BRB与MCU之间采用串口通信，波特率为19200。

                                UART-TX(pin22) ---->EFM8BB10F8G_RX(pin17)

                                UART-RX(pin21) <---  EFM8BB10F8G_TX(pin18)

- 指令格式如下所示：

  起始码（0xAA固定）+指令类型码（必选）+数据码（可选）+终止码（0x55）每条指令都有相应的应答，详细协议见附录(7.5)：RF万能收发模块串口协议_v1.0。协议中Tsyn表示遥控器波形中的同步码长（单位us），Tlow表示数据码段中的一个周期中“4LCK”段的实际脉冲时间，Thigh表示数据码段中的一个周期中“12LCK”段的实际脉冲时（单位us）。

  如图8.4  所示脉冲翻译成二进制表示 “00000010 10111011 11101000”即 24bit Data为0x02,0xBB,0xE8 。Tsyn、Tlow、Thigh、24bit Data 为学习到的门磁设备的键值属性，点击APP对应的学习过的按钮

  

上述属性值会下发至MCU解析发送。用户可根据协议开发外部MCU。

### 7.4 发声控制

发声芯片支持两种发声方式：单次触发以及报警声。

单次触发：可以由GPIO9和GPIO12触发：

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191105194855191.png" alt="image-20191105194855191" style="zoom: 67%;" />

报警声：GPIO9 400ms周期性触发

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191105194925329.png" alt="image-20191105194925329" style="zoom: 67%;" />

### 7.5 附录 

####          7.5.1 RF万能收发模块串口协议  

**简介**

​		RF万能收发模块串口协议适用于模块与MCU之间。后者可以实现RF键

值的接收、发送、学习。 串口参数：19200，8位数据，1位停止，无校验。

####          7.5.2 协议

           指令长度可变，每一条指令都有相应的返回值，具体如下。

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/RF%20%E5%8D%8F%E8%AE%AE%E6%B5%81%E7%A8%8B%E5%9B%BE.bmp)                      

| Start       |
| ----------- |
| 0xAA:起始位 |

| Action         |
| -------------- |
| 0xA0:返回动作  |
| 0xA1:学习动作> |
| 0xA2:超时退出  |
| 0XA3：学习成功 |

| Tysn                                                   |
| ------------------------------------------------------ |
| uint16类型，表示同步码时间，单位us,MSB序（先发送高位） |

| Tlow                                                    |
| ------------------------------------------------------- |
| uint16类型，表示低电平时间，单位us，MSB序（先发送高位） |

| Thigh                                                   |
| ------------------------------------------------------- |
| uint16类型，表示高电平时间，单位us，MSB序（先发送高位） |

| 24bit Data  |
| ----------- |
| 24bit的键值 |

| End         |
| ----------- |
| 0x1B:结束符 |

















#  

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/%E7%89%88%E6%9D%83%E8%AF%B4%E6%98%8E.bmp )

# 		                                           PSA-BHA 应用指导书 



<img>![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/LOGO.bmp)

**版本V1.0** 

**版权©2019** 





## Overview

     

        PSA-BHA-GL 模块是由酷宅设计开发的一款低成本高集成度的通用智能温湿度 WiFi 开关模块， 以用于快 速

开发基于智能温湿度控制的开关插座、 加湿器、 除湿器等产品。 PSA-BHA-GL 模块能实现 wifi 的搜索连 接， 网

络服务器的通讯， 与外部 MCU 协作， 手机 app 的控制等基本功能， 所有型号支持不同地区的服务器 及各种手

机端控制。 模块核心处理器为 ESP8266， 它在较小尺寸封装中集成了业界领先的 Tensilica L106 超低功耗 32 位 

微型 MCU， 带有 16 位精简模式， 主频支持 80 MHz 和 160 MHz， 支持 RTOS， 集成 Wi-Fi MAC/ 

BB/RF/PA/LNA， 板载天线。 该模块支持标准的 IEEE802.11 b/g/n 协议， 完整的 TCP/IP 协议栈。 ESP8266 是高

性能无线 SOC， 以最低成本提供最大实用性， 为 WiFi 功能嵌入其他系统提供无限可能。           

  

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA%20%E6%A8%A1%E5%9D%97%E8%8A%AF%E7%89%87%E6%A1%86%E6%9E%B6%E5%9B%BE.bmp)





## Functions 

        ESP8266 是一个完整且自成体系的WiFi 网络解决方案， 能够独立运行， 也可以作为slave 搭载于其他Host 

运行。 ESP8266 在搭载应用并作为设备中唯一的应用处理器时， 能够直接从外接 闪存中启动。 内置的高速缓冲

存储器有利于提高系统性能， 并减少内存需求。 另外一种情况是， 无线上网接入承担WiFi 适配器的任务时， 可

以将其添加到任何基于微控制器的设计 中， 连接简单易行， 只需通过SPI/SDIO 接口或I2C/UART 口即可。 

ESP8266 强大的片上处理和存储能力， 使其可通过GPIO 口集成传感器及其他应用的特定设备， 实现了 最低前期

的开发和运行中最少地占用系统资源。 ESP8266 高度片内集成， 包括天线开关balun、 电源管理转换器， 因此仅

需极少的外部电路， 且包括前 端模块在内的整个解决方案在设计时将所占PCB空间降到最低。 装有ESP8266 的系

统表现出来的领先特征有： 节能VoIP 在睡眠/唤醒模式之间的快速切换、 配合低功率 操作的自适应无线电偏置、 

前端信号的处理功能、 故障排除和无线电系统共存特性为消除蜂窝/蓝牙 /DDR/LVDS/LCD干扰。    





## Features 



- WIFI @2.4 GHz， 支持WPA/WPA2 安全模式    

- 超小尺寸模组20.32mm*22.86mm    

- 内置10 bit 高精度ADC    

- 内置TCP/IP 协议栈    

- 内置TR 开关、 balun、 LNA、 功率放大器和匹配网络    

- 内置PLL、 稳压器和电源管理组件    

- 802.11b 模式下+ 20 dBm 的输出功率    

- 支持天线分集    

- 深度睡眠保持电流为10uA， 关断电流小于5uA    

- 内置低功率32 位CPU： 可以兼作应用处理器    

- SDIO 2.0、 SPI、 UART    

- STBC、 1x1 MIMO、 2x1 MIMO    

- A-MPDU 、 A-MSDU 的聚合和0.4 s的保护间隔    

- 2ms之内唤醒、 连接并传递数据包    

- 待机状态消耗功率小于1.0mW (DTIM3)    

- 工作温度范围-40 ~ 125℃    

- 支持温湿度在线显示    

- 支持设定温湿度区间自动控制    

- 支持多种温湿度传感器（DHT11、 AM2301、 DS18B20） 

  

     

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA%E6%A8%A1%E5%9D%97%E5%BC%95%E8%84%9A%20%E5%8A%9F%E8%83%BD%E5%9B%BE.bmp)

                                                                                    



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA%E6%A8%A1%E5%9D%97%E5%AE%9E%E7%89%A9%E5%9B%BE.bmp)

                                                                                     





| Pin Index | Pin Name | Description                                                  |
| --------- | -------- | ------------------------------------------------------------ |
| 1         | Sensor   | 传感器数据引脚， 支持DHT11/AM2301/DS18B20三种传感器          |
| 2         | NC       | 开关控制引脚。 可连接继电器等器件。 高电平： 开 低电平： 关  |
| 3         | SLED     | 状态指示LED：<br>1、 常亮， 正常工作状态；<br>2、 亮 200ms 灭 1800ms 一直重复该动作， 表示无法连接到 WiFi热点；<br>3、 亮 200ms 灭 200ms 亮 200ms 灭 1400ms 重复该动作， 表 示无法连接到服器；   4、 亮 1000ms 灭 1000ms 重复该动作， 表示该设备连接到服 务器但是没有被正确注册到服务器及用户账户下； 亮1000ms， 灭200ms, 亮200ms,灭200ms, 亮200ms,灭200ms，<br>5、 一直重复该动作， 表示已进入SSID配置模式； |
| 4         | NC       | -不使用-                                                     |
| 5         | KEY      | 按键引脚。 内部10k上拉， 低有效。 单击按键， 开关状态切换。 默认高电平， 当按下5s后模块会进入配置模式， 配置模式下单 击按键会自动退出配置模式。 |
| 6         | VCC      | 模块3.3V电源引脚                                             |
| 7         | NC       | -不使用-                                                     |
| 8         | NC       | -不使用-                                                     |
| 9         | GND      | 模块地电源引脚                                               |
| 10        | RESET    | 复位引脚， 内部10K上拉， 低有效                              |

                                                                              



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA%E6%A8%A1%E5%9D%97%E5%B0%81%E8%A3%85%E5%B0%BA%E5%AF%B8%E5%9B%BE.bmp)

                                                                                 







------





 

   



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/%E7%89%88%E6%9D%83%E8%AF%B4%E6%98%8E.bmp )
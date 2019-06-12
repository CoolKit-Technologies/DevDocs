# 		                                           PSA-BTA 应用指导书 



<img>![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/LOGO.bmp)

**版本V1.0** 

**版权©2019** 





## Overview

     

          PSA-xTA 系列是一款高集成度的通用串口转 WiFi 透传模块，可以用于快速开发基于 WiFi 的数据传输产品。 

PSA-xTA 系列 模块能实现 wifi 的搜索连接，网络服务器的通讯，串口转 WiFi 透传等基本功能。       

  





## Functions 

         

- 支持通过手机 app 快速配置 SSID 及连接密码    
- 支持自动连接服务器，注册及更新状态信息    
- 支持通过手机 app 与模块进行数据透传    







## Features 



- 体积小，更容易安装入壳体空间 

- 外接天线及陶瓷天线可选    

- 高集成度，无需代码开发即可实现完整功能    

     

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA%E6%A8%A1%E5%9D%97%E5%BC%95%E8%84%9A%20%E5%8A%9F%E8%83%BD%E5%9B%BE.bmp)

                                                                                    



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA%E6%A8%A1%E5%9D%97%E5%AE%9E%E7%89%A9%E5%9B%BE.bmp)

                                                                                     





| Pin Index | Pin Name | Description                                                  |
| --------- | -------- | ------------------------------------------------------------ |
| 1         | NC       | -不使用-                                                     |
| 2         | NC       | -不使用-                                                     |
| 3         | NET      | 网络状态指示引脚，可接 LED，低有效。状态时序见图 1           |
| 4         | NC       | -不使用-                                                     |
| 5         | E-FW     | 模块配置引脚。内部 10k 上拉，低有效。 默认高电平，当拉低超过 100ms 后模块会进入配置模式，配置模式下收到低脉 冲会自动退出配置模式。 做按键输入时，低有效，按键按会进入或者退出配置模式。 |
| 6         | VCC      | 模块电源引脚                                                 |
| 7         | RX       | 串口输入、波特率 9600，1 位起始位，8 位数据位，1 位停止位，无校验位 |
| 8         | TX       | 串口输出、波特率 9600、 1 位起始位，8 位数据位，1 位停止位，无校验位 |
| 9         | GND      | 模块电源引脚                                                 |
| 10        | RESET    | 复位引脚，内部 10K 上拉，低有效                              |

 

 

    

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA-BTA%20%E5%BC%95%E8%84%9A%E7%8A%B6%E6%80%81%E6%97%B6%E5%BA%8F%E5%9B%BE.bmp)                                                                             



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/PSA%E6%A8%A1%E5%9D%97%E5%B0%81%E8%A3%85%E5%B0%BA%E5%AF%B8%E5%9B%BE.bmp)

                                                                                 







------





 

   



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/%E7%89%88%E6%9D%83%E8%AF%B4%E6%98%8E.bmp )
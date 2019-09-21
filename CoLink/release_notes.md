# Colink 0.13.0

    source:master/7a8b5afbe4c4ff62e07cc7e3d681442b3ef6ea52

    - 通用：
      - 修复重新配网后设备上线不显示版本号bug
      - 修复tcp发送失败不重连bug
      - 新增设备被删除通知
      - 更新库
      - 更新example代码

# Colink 0.12.0

    source:master/5bd6458203b21a73e0015d34ee622497a30c08e2

  - 通用：
    - 新增软件定时器API：colink_user_timer.h
    - 新增底层超时：连接超时，服务器响应超时...
    - 修改DNS解析为非阻塞
    - 将tcp收发改为串行关系
    - 内部优化（协议升级，框架优化）

  - 网关设备：
    - 新增网关设备本地操作API
      - colinkGatewayDelAllSubDev
      - colinkGatewayAddSubDev
      - colinkGatewayGetSubDevNum
      - colinkGatewayGetSubDevList
    - 新增网关设备批量上报子设备状态API
      - colinkGatewayReportSubDevState
    
  - 文档：
    - 更新《CoLink API 参考手册》
  

# Colink 0.10.0

    source:master/c78c7cc20ae6278f1fcfb0c432c71de19d14bf84
    
  - 库：
    - 分离网关类设备库和cJSON库：libcolinkgw.a,libcolinkcJSON.a;
    
  - 普通设备：
    - 更改结构体ColinkSubDevice成员uuid为uiid;
    - 获取设备状态API：colinkGetDevStatus增加未注册状态：DEVICE_UNREGISTERED;
    - 增加获取UTC时间API：colinkSendUTCRequest、colinkSendUTCRequestCb;
    - 底层协议优化;
    - 增加设备未注册状态的通知;
    - 增加反初始化colink API：colinkDeInit;
    - colink_sysadapter.h：变量命名更改（需要对应.c文件进行相应更改）;

  - 网关设备：
    - 支持8字节子设备mac;
    - 在colinkSubDevSendRes和colinkSubDevRecvReqCb上增加req_sequence参数;
    - 增加网关设备子设备列表操作API：colinkGatewayAddSubDev、colinkGatewayGetSubDevNum和colinkGatewayGetSubDevList;
    - 增加子设备上下线请求回调：colinkOnlineSubDevResultCb、colinkOfflineSubDevResultCb;

  - 文档：
    - 新增《基于CoLink接入酷宅云平台操作指南》;
    - 新增《OTA固件升级说明》;
    - 新增《CoLink配网说明》;
    - 新增《CoLink定时器使用说明》;
    - 新增《colink状态机》;
    - 更新《CoLink API 参考手册 v0.10》;
    - 更新《CoLink 快速指导 v0.10》;
    - 更新《CoLink 单通道开关开发示例 v0.10》;

# CoLink 0.9.0

    source:master/58b976a318beae1e51b79cfb43359e949c1f3779

  - 新增网关类设备API；
  - 新增配网数据API；
  - 更新cJSON库至1.7.7版本；
  - 新增colinkSscanf、colinkStrtod和colinkTolower适配接口；
  - ColinkDev结构体新增distor_port和dev_type字段；
  - 调整ColinkEvent所有回调接口名称，参见《CoLink API 文档变更说明》；
  - 调整接口名称colinkUpgradeResponse改为colinkUpgradeRes；
  - 修复内存泄漏问题；
  - 更新light_8266示例：支持SSL身份认证、演示OTA接口使用方法；
  - 新增devicehub_8266示例：演示网关类设备接口使用方法；
  - 更新lib目录下的库文件；

# CoLink 0.8.1

    source:master/c96c87b552fb3aec69d03f970bf1abd9cd6137e8

  - 修复使用非加密时连不上服务器问题；

# CoLink 0.8.0

  - 新增SSL功能，需要在原来的网络适配接口去适配实现SSL加密功能；
  - ColinkDev结构体新增ssl_enable字段；
  - 调整连接服务器的重连策略和心跳机制；
  - 新增OTA升级通知接口；
  - 新增获取colink版本接口；
  - 新增和调整colink接口的错误返回值；
  - 新增获取网络状态的适配接口；

# CoLink 0.7.0

  - 实现colink框架和与云平台交互的基本功能；
  - 提供colink系统适配接口；
  - 提供colink网络层适配接口；
  - 提供获取设备离线上线功能；

# 硬件
维特智能WTRTK（开发程序的时候可以买一个别的便宜的GPS用，数据的都是一样）,STM32f10c8t6![[1745628937562.jpg]]
# 实现逻辑
## GPS模块通过串口与单片机进行通信
GPS可以通过TTL主动输出，传感器回传数据兼容**NMEA－183**。
NMEA是?**National Marine Electronics Association**的缩写，是美国国家海洋电子协会的简称，现在是GPS导航设备统一的标准协议。![[NMEA0183.xls]]
其中**RMC（Recommended Minimum Specific GNSS Data**是我们大创中需要用到的通信协议
## 单片机开发解析数据
是现在的主要内容与任务。
初步计划利用UART串口进行通讯。
### 进行串口的配置
利用程序设置好UART串口的状态 ，要考虑进行后续的CAN口通讯
### 数据的解析
因为GPS模块传送的二进制数据包，所以不能直接解析，需要根据二进制的字母编码进行解析数据，得到我们需要的经纬度数据
### 资料
野火的GPS模块教程 https://doc.embedfire.com/module/module_tutorial/zh/latest/Module_Manual/port_class/gps.html
知乎的一个教程： https://zhuanlan.zhihu.com/p/594438920
### 代码托管

## 通过CAN口和WiFi进行远程的数据传输
现在没有了解，之后再涉及
## 数据接受后的地图绘制
初步想法是先将二进制数据转化成十进制的经纬度，之后通过python的数据处理和图形绘制库进行地图的绘制。如果前期的数据正常这个步骤会非常简单。
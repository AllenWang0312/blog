# 常见协议类型特点
## UDP 
用户数据报协议（UDP，User Datagram Protocol） 传输层协议
* 是无连接的，即发送数据之前不需要建立连接。
* 尽最大努力交付，即不保证可靠交付
* 传输效率高，适用于对高速传输和实时性有较高的通信或广播通信。
* 支持一对一，一对多，多对一和多对多的交互通信。

## TCP/IP 
传输控制协议（TCP，Transmission Control Protocol） 传输层协议
* TCP面向连接（如打电话要先拨号建立连接）。
* 提供可靠的服务，
* 通过TCP连接传送的数据，无差错，不丢失，不重复，且按序到达。传输效率相对较低。
* 连接只能是点到点、一对一的

## MQTT  
消息队列 遥测 传输（MQTT Message Queuing Telemetry Transport） 应用层协议
* 工作在 TCP/IP协议族
* 基于客户端-服务器的消息发布/订阅传输协议。
* MQTT协议是轻量、简单、开放和易于实现的机器与机器（M2M）通信和物联网（IoT）。其在，通过卫星链路通信传感器、偶尔拨号的医疗设备、智能家居、及一些小型化设备中已广泛使用。
* MQTT协议的优势是可以支持所有平台，它几乎可以把所有的联网物品和互联网连接起来。

##CoAP 
约束应用协议（CoAP The Constrained Application Protocol）应用层协议
* 工作在 UDP协议族
* 基于REST架构。
* CoAP是二进制格式的，HTTP是文本格式的，CoAP比HTTP更加紧凑。
轻量化，COAP最小长度仅仅4B，一个HTTP的头都几十个B
* 支持可靠传输，数据重传，块传输。
* 确保数据可靠到达支持IP多播, 即可以同时向多个设备发送请求。
* 非长连接通信，适用于低功耗物联网场景。

## LWM2M 
轻量级机器到机器 （Lightweight Machine-To-Machine）应用层协议
* 协议的消息传递是通过 CoAP 协议来达成的。
* 协议基于REST架构。
* 协议定义了一个紧凑高效又不乏扩展性的数据模型
* 协议最主要的实体包括LwM2M Server和LwM2M Client。
* LwM2M Serve作为服务器，部署在M2M服务供应商处或网络服务供应商处。
LwM2M Client作为客户端，部署在各个LwM2M设备上。


HTTP
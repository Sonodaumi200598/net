# 第 6 章 Linux 网络基础

## 6.1 Linux 网络接口管理

聚合路由器和聚合服务器建议以 Linux 系统作为实验基础平台。需要掌握的网络管理工具包括 `ip addr`、`ip link`、`ip route`、`ip rule`、NetworkManager 和 systemd-networkd。

主要操作包括查看网卡状态、配置 IP 地址、启用或关闭接口、设置默认路由、管理多网卡优先级和监测链路变化。

## 6.2 策略路由

策略路由是多链路聚合系统中的基础关键技术。它用于确保不同链路的数据能够从指定网卡、指定源 IP 和指定路由表发出。

```text
发往链路 A 的数据绑定源 IP A，并走路由表 A。
发往链路 B 的数据绑定源 IP B，并走路由表 B。
发往链路 C 的数据绑定源 IP C，并走路由表 C。
```

相关技术包括多路由表、`ip rule`、按源 IP 路由、按 `fwmark` 路由、按接口路由和默认路由隔离。

## 6.3 Socket 基础

聚合传输程序通常通过 Socket 完成数据收发。需要掌握 UDP socket、TCP socket、bind、sendto、recvfrom、SO_BINDTODEVICE、SO_SNDBUF、SO_RCVBUF 和非阻塞 I/O 等技术。

典型设计中，聚合路由器为不同链路建立独立 socket 或绑定不同源地址，聚合服务器则通过一个或多个监听 socket 接收来自多条链路的数据。

## 6.4 网络队列与缓冲区

网络队列和缓冲区直接影响实时视频传输质量。基础技术层需要理解发送缓冲区、接收缓冲区、网卡队列、qdisc、队列积压、bufferbloat，以及丢包与排队延迟之间的关系。

对于实时视频，过大的缓冲可能降低丢包但增加时延，过小的缓冲可能降低时延但增加丢包，需要结合上层策略合理配置。

## 6.5 抓包与诊断

基础诊断工具包括 tcpdump、Wireshark、ss、netstat、iftop、nload、iperf3、ping 和 traceroute。这些工具用于分析链路连通性、吞吐量、RTT、丢包、乱序和协议封装正确性。


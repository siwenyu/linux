# 每天一个linux命令
### 1.ping命令

ping命令是因特网包探索器。

ping命令的一般格式为：
ping[-dfnqrRv][-c发送次数][-i间隔秒数][-I(大写i)网络界面][-l(小写L)前置载入][-p范本样式][-s数据包大小][-t存活数值][主机名或IP地址]
#### 参数
 	【-c】指定要被发送(或接收)的回送信号请求的数目，由Count变量指出。如果没有指定，mac下一直发送，知道手动停止（command+c）
	【-wtimeout】这个选项仅和-c选项一起才能起作用。它使ping命令以最长的超时时间去等待应答(发送最后一个信息包后)。默认超时时间为4000ms(4s)
	【-d】使用Socket的SO_DEBUG功能。
	【-D】这个选项引起ICMPECHO_REPLY信息包向标准输出的十六进制转储。
	【-f】指定flood-ping选项。-f标志“倾倒”或输出信息包，在它们回来时或每秒100次，选择较快一个。每一次发送ECHO_REQUEST，都打印一个句号，而每接收到一个ECHO_REPLY信号，就打印一个退格。这就提供了一种对多少信息包被丢弃的信息的快速显示。仅仅root用户可以使用这个选项。
	注：这在网络上将非常困难，必须小心使用。Floodping命令仅仅root用户可以使用。-f标志与-iWait标志不兼容.
	【-n】只输出数值。
	【-r】忽略路由表，直接将数据包送到远端主机上。通常是查看本机的网络接口是否有问题。
	【-R】记录路由过程。-R标志包括ECHO_REQUEST信息包中的RECORD_ROUTE选项，并且显示返回信息包上的路由缓冲。
	【-v】详细显示指令的执行过程。
	【-iwait】在每个信息包发送之间等待被Wait变量指定的时间(秒数)。缺省值是在每个信息包发送之间等待1秒。这个选项与-f标志不兼容。
	【-Ia.b.c.d】指定被a.b.c.d标明的接口将被用于向外的IPv4多点广播。-I标志是大写的i。
	【-lPreload】在进入正常行为模式(每秒1个)前尽快发送Preload变量指定数量的信息包。-l标志是小写的L。
	【-L】对多点广播ping命令禁用本地回送。
	【-pPattern】指定用多达16个“填充”字节去填充你发送的信息包。这有利于诊断网络上依赖数据的问题。例如“-pff”全部用1填充信息包。
	【-q】不显示任何传送封包的信息，只显示最后的结果。
	【-spacketsize】指定发送的数据字节数，预设值是56，加上8字节的ICMP头，一共是64ICMP数据字节。
	【-Shostname/IPaddr】将IP地址用作发出的ping信息包中的源地址。在具有不止一个IP地址的主机上，可以使用-S标志来强制源地址为除了软件包在其上发送的接口的IP地址外的任何地址。如果IP地址不是以下机器接口地址之一，则返回错误并且不进行任何发送。
	【-ttll】设置存活数值TTL的大小。
	【-ointerface】指出interface将被用于向外的IPv6多点广播。接口以“en0”，“tr0”等的形式指定。

#### 示例

##### ping ip

```
$ ping 220.181.38.110

```
ping不通的情况：

```
$ ping 220.181.38.110 
PING 220.181.38.110 (220.181.38.110): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
^C
--- 220.181.38.110 ping statistics ---
4 packets transmitted, 0 packets received, 100.0% packet loss
```
ping通的情况：

```
$ ping 172.20.130.239
PING 172.20.130.239 (172.20.130.239): 56 data bytes
64 bytes from 172.20.130.239: icmp_seq=0 ttl=64 time=0.130 ms
64 bytes from 172.20.130.239: icmp_seq=1 ttl=64 time=0.065 ms
64 bytes from 172.20.130.239: icmp_seq=2 ttl=64 time=0.088 ms
64 bytes from 172.20.130.239: icmp_seq=3 ttl=64 time=0.081 ms
64 bytes from 172.20.130.239: icmp_seq=4 ttl=64 time=0.083 ms
^C
--- 172.20.130.239 ping statistics ---
5 packets transmitted, 5 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.065/0.089/0.130/0.022 ms
```
##### ping域名

```
$ ping www.baidu.com

```
ping通的情况：

```
$ ping www.baidu.com
PING www.a.shifen.com (220.181.111.188): 56 data bytes
64 bytes from 220.181.111.188: icmp_seq=0 ttl=56 time=1.807 ms
64 bytes from 220.181.111.188: icmp_seq=1 ttl=56 time=1.833 ms
64 bytes from 220.181.111.188: icmp_seq=2 ttl=56 time=2.906 ms
64 bytes from 220.181.111.188: icmp_seq=3 ttl=56 time=2.768 ms
^C
--- www.a.shifen.com ping statistics ---
4 packets transmitted, 4 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 1.807/2.329/2.906/0.511 ms
```

ping不通的情况

```
$ ping www.baidu123412341234.com
ping: cannot resolve www.baidu123412341234.com: Unknown host
```



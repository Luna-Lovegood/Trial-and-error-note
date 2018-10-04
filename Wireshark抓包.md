# linux下Wireshark抓取其他设备的包
### 1.首先查看无线网卡的型号，查看自己电脑的无线网卡是否支持Monitor(监听)模式
输入如下命令行：

`lspci | grep -i net`

下面第二行就是我的电脑无线网卡的型号：

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
05:00.0 Network controller: Intel Corporation Wireless 3165 (rev 79)
```
### 2.如果无线网卡支持监听模式，就可用如下两种方法打开监听
* 方法一：先关闭无线网卡，再改变工作模式，再打开无线网卡

```
sudo ifconfig wlp5s0 down
sudo iwconfig wlp5s0 mode monitor
sudo ifconfig wlp5s0 up
```
但是我的电脑在启动Wireshark后，无线网卡wlp5s0又变为了Managed模式，所以我决定尝试一下第二种方法（苦涩的微笑）
* 方法二：用airmon-ng切换网卡模式

```
sudo apt install airmon-ng
sudo airmon-ng start wlp5s0
```
然后查看一下网卡的模式，然鹅我的wlp5s0网卡依旧显示：

```
smj@smj-Inspiron-7559:~$ iwconfig
lo        no wireless extensions.

enp4s0    no wireless extensions.

wlp5s0    IEEE 802.11  ESSID:"OUC-WIFI"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: 70:F9:6D:2E:E5:E0   
          Bit Rate=150 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0

mon0      IEEE 802.11  Mode:Monitor  Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```
Managed, Managed, Managed......

这大概是告诉我我的无线网卡其实是不支持Monitor模式的吧，所以说第一步的确认很关键呀，硬件罢工那就只有找同学借下电脑继续做作业了orz

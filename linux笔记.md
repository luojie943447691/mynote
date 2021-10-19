## 联网

nat方式联网 

第一步

vim /etc/sysconfig/network-scripts/ifcfg-eth0

```
DEVICE="eth0"
BOOTPROTO="static"   #static，静态ip，而不是dhcp，自动获取ip地址。
IPV6INIT="yes"
NM_CONTROLLED="yes"
ONBOOT="yes"
TYPE="Ethernet"
UUID="4b1bfb40-df4f-48e5-9712-b402c67a2ea6"
IPADDR="192.168.159.66"    # 自定义 前面66之前和宿主机一致，66之后只要不和主机一直即可
NETMASK="255.255.255.0"    # 宿主机子网掩码一致
GATEWAY="192.168.159.2"			# 宿主机网关IP一致
DNS1="8.8.8.8"
DNS2="114.114.114.114"
```

第二步

vi /etc/sysconfig/network 

```
NETWORKING=yes
HOSTNAME=Matt
```

第三步 

cd /etc/udev/rules.d

ll查看 找到 70-persistent-net.rules

删掉 70-persistent-net.rules

命令 rm -f  70-persistent-net.rules

ll再次查看 如果没有则删除成功



第四步

init 6
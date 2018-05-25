### Linux Bond

>The configuration below is only verified on centos7.

1. Modify eno1 and eno2 config files

Open both configuration using a text editor such as vi/vim, and make sure file read as follows for eno1 interface.

`# vi /etc/sysconfig/network-scripts/ifcfg-eno1`

```
TYPE=Ethernet
BOOTPROTO=none
ONBOOT=yes
NM_CONTROLLED=no
SLAVE=yes
DEVICE=eno1
MASTER=admin
```

`# vi /etc/sysconfig/network-scripts/ifcfg-eno2`

```
TYPE=Ethernet
BOOTPROTO=none
ONBOOT=yes
NM_CONTROLLED=no
SLAVE=yes
DEVICE=eno1
MASTER=admin
```

2. Create a bond configuration file

`# vi /etc/sysconfig/network-scripts/ifcfg-admin`

```
TYPE=Bond
BONDING_MASTER=yes
ONBOOT=yes
USERCTL=no
NM_CONTROLLED=no
BOOTPROTO=none
NAME=admin
IPADDR=6.19.5.41
NETMASK=255.255.255.0
BONDING_OPTS="mode=1 miimon=100"
DEVICE=admin
GATEWAY=6.19.5.254
```

3. Restart network service

`# systemctl restart network`

4. Test configuration

`# cat /proc/net/bonding/admin`
```
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: fault-tolerance (active-backup)
Primary Slave: None
Currently Active Slave: eno1
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: eno1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 6c:92:bf:51:f9:f2
Slave queue ID: 0

Slave Interface: eno2
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 6c:92:bf:51:f9:f3
Slave queue ID: 0
```

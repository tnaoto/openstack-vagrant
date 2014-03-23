easy install openstack by vagrant for devel

env
====
virtualbox on OSX.

openstack installer is RDO.

add modify
====

- eth1

/etc/sysconfig/network-scripts/ifcfg-eth1

```
TYPE=OVSPort
DEVICETYPE=ovs
OVS_BRIDGE=br-ex
NM_CONTROLLED=no
BOOTPROTO=none
ONBOOT=yes
DEVICE=eth1
PEERDNS=no
```


- br-ex

/etc/sysconfig/network-scripts/ifcfg-br-ex

```
DEVICE=br-ex
DEVICETYPE=ovs
TYPE=OVSBridge
BOOTPROTO=static
IPADDR=192.168.65.11
NETMASK=255.255.255.0
ONBOOT=yes
```

# vbox centos7虚拟机网卡配置案例

## 两张网卡

| 网卡   | 配置文件     | 网络模式      | IP设置 | 功能         |
| ------ | ------------ | ------------- | ------ | ------------ |
| 网卡一 | ifcfg-enp0s3 | NAT模式       | 动态IP | 用于连接外网 |
| 网卡二 | ifcfg-enp0s8 | Host-Only模式 | 静态IP | 用于外部连接 |

## 具体配置

ifcfg-enp0s3需修改

    ...
    ONBOOT=yes

ifcfg-enp0s8需修改

    ...
    BOOTPROTO=static
    ...
    ONBOOT=yes
    IPADDR=192.168.56.2
    NETMASK=255.255.255.0
    GATEWAY=192.168.56.1

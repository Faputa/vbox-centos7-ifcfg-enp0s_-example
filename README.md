# vbox centos7虚拟机网卡配置案例

1. 新建虚拟机

    类型：Linux  
    版本：Red Hat (64-bit)

2. 设置网络

    添加两张网卡

    | 网卡   | 配置文件     | 网络模式      | IP设置 | 功能         |
    | ------ | ------------ | ------------- | ------ | ------------ |
    | 网卡一 | ifcfg-enp0s3 | NAT模式       | 动态IP | 用于连接外网 |
    | 网卡二 | ifcfg-enp0s8 | Host-Only模式 | 静态IP | 用于主机连接 |

3. 安装系统

    1. 启动虚拟机
    2. 选择启动盘

4. 修改网卡配置

    切换到配置文件目录

        cd /etc/sysconfig/network-scripts/

    修改ifcfg-enp0s3

        ...
        ONBOOT=yes

    修改ifcfg-enp0s8，这里设置主机号是2

        ...
        BOOTPROTO=static
        ...
        ONBOOT=yes
        IPADDR=192.168.56.2
        NETMASK=255.255.255.0
        GATEWAY=192.168.56.1

5. 重启网络

        systemctl restart network

# VPN

Bare Bones (PPTP) VPN Installer for CentOS
See [http://drewsymo.com/networking/vpn/install-ptpp/](http://drewsymo.com/networking/vpn/install-ptpp/) for more information.

## Installation

To get started with your own secure VPN, simply execute the following commands at your servers command-line:

	$ yum install -y git
	$ cd /opt && git clone git://github.com/drewsymo/VPN.git
	$ cd VPN && bash vpn-setup-vanilla.sh

If you're on Linode, you can simply rebuild your instance with the `PPTP VPN Installer` [stackscript](http://www.linode.com/stackscripts/view/?StackScriptID=6346).

## Author

**Drew Morris**
============================================================================================================================


Link: https://blog.linuxeye.cn/412.html

wget http://mirrors.linuxeye.com/scripts/vpn_centos.sh

chmod +x ./vpn_centos.sh

./vpn_centos.sh
=============================================================================================================================
CentOS下单网卡使用PPTP搭建VPN
Link: https://www.linuxidc.com/Linux/2012-06/61923.htm

环境：CentOS5.5  （服务器），Windows 7（客户机）

服务器ip地址：218.198.180.8  ，客户机ip地址：218.198.180.105

------------------------------本服务作用：待定...-----------------------

一：下载安装pptp包（yum源中没有，google搜索下载）,这个软件没什么依赖性，可直接安装；

CentOS下单网卡使用PPTP搭建VPN

二：配置pptp

A;首先修改内核设置，使其支持转发功能（建议使用方法1）

1，永久生效设置如下：

打开/etc/sysctl.conf

CentOS下单网卡使用PPTP搭建VPN

修改net.ipv4.ip_forward = 1

CentOS下单网卡使用PPTP搭建VPN

使设置永久生效

CentOS下单网卡使用PPTP搭建VPN

2，临时生效设置如下（重启系统或网卡后又为0了）：

CentOS下单网卡使用PPTP搭建VPN

B：在服务器上新增网段192.168.10.0/24（分配给vpn客户机的）做snat（需要访问外网啊），使vpn拨号进来后可以访问Internet(外网)；

创建脚本文件/root/snat.sh

CentOS下单网卡使用PPTP搭建VPN

内容如下（注释内容仅为参考）：

CentOS下单网卡使用PPTP搭建VPN

执行此脚本,sh /root/snat.sh

CentOS下单网卡使用PPTP搭建VPN

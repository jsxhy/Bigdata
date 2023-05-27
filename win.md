# win

## Linux Centos-7

**常用命令**

|命令|描述|
|:---|:---|
|jps|查看进程|
|pwd|查看当前路径|
|命令 &|命令后台运行|
|nohub 命令|程序免挂断|
|mkdir|创建目录|
|ps -aux|查看进程详细信息|
|kill -9 [进程号|进程名称]|结束进程|
|tar 参数 解压文件 解压路径|解压|
|mv 源文件 目标地址|移动文件地址|
|sudo 命令|以管理者的身份执行|
|source 文件|刷新当前shell环境|
|sed -i "s/要替换的/替换为/g" 文件路径|此命令用于替换内容|
|hostnamectl set-hostname master|修改主机名为master|
|service network restart|重启网络|
|systemctl stop firewalld.service|关闭防火墙|
|systemctl disable firewalld.service|关闭防火墙自启动|
|systemctl status firewalld.service|查看防火墙状态|
|ls |grep "guava"|在当前目录下找文件名含 guava 的文件|
|rpm -ivh ./*.rpm --force --nodeps|使用 rpm 包管理器安装当前目录所有 .rpm 软件包<br>-ivh：复合写法<br>-i：安装<br>-v：可视化安装<br>-h：显示进度<br>--force：强制安装<br>--nodeps：不处理依赖问题（无网络环境下安装）|
|halt|立刻关机|
|poweroff|立刻关机|
|shutdown -h now |立刻关机(root用户使用)|
|shutdown -h 10 |10分钟后自动关机|

### 静态ip

```
TYPE="Ethernet"
PROXY_METHOD="none"
BROWSER_ONLY="no"
BOOTPROTO="static"          #设置ip为静态
DEFROUTE="yes"
IPV4_FAILURE_FATAL="no"
IPV6INIT="yes"
IPV6_AUTOCONF="yes"
IPV6_DEFROUTE="yes"
IPV6_FAILURE_FATAL="no"
IPV6_ADDR_GEN_MODE="stable-privacy"
NAME="ens33"
UUID="b02b0313-c7b0-4597-aa60-d7d120cd6e66"
DEVICE="ens33"
ONBOOT="yes"                    #是否随网络服务启动当前网卡生效
IPADDR="192.168.70.102"         #ip地址
GATEWAY="192.168.70.2"          #网关
NETMASK="255.255.255.0"         #子网掩码
DNS1=114.114.114.114            # 可自定义
DNS2=8.8.8.8                    # 可自定义
```

## ssh

**常用命令**

|命令|描述|
|:---|:---|
|scp 参数 本地文件 用户名@虚拟机ip:目录|从本地上传文件到虚拟机<br>参数:<br>-r   上传整个目录|
|ssh root@192.168.70.101|用root账户连接192.168.70.101|
|exit|登出|
|clear|清屏|

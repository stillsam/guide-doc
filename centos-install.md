## VirtualBox里安装CentOS7 minimal
#### 一、准备工作
1. BOIS里CPU设置为 Virtualization Technology   enable
2. VirtualBox里创建硬盘时，选64位的redhat （因为host是64位的）。

#### 二、CentOS7 配置
##### 1. 配置网络

安装minimal版, 默认是开机不启用网卡的, 通过root登录后, 使用 `service network start` 命令启动网卡。 
执行 `ip -s address` , 我们会看到ip信息。

但我们不能每次开机后都执行一遍启动网卡, 下面我们设置网卡开机自动：

修改配置文件: `vi /etc/sysconfig/network-scripts/ifcfg-enp0s3`  
将该文件 ONBOOT="no" 改成yes 

下次启动时网卡会开机启动。

##### 2. 添加用户，用作日常使用系统
```
# useradd martin
# passwd martin
```

编辑 `/etc/sudoers` 文件，添加用户martin：

`# visudo`   添加一行： `martin  ALL=(ALL)  ALL`

##### 3. 修改yum源
更换yum源到国内，可以获得更高的速度。推荐选择中国科技大学的yun源，使用广泛、资源收录全。

1.进入到yum源管理目录：

`cd /etc/yum.repos.d/`

2.备份Base源：

`mv CentOS-Base.repo CentOS-Base.repo.bak`

3.根据不同操作系统选择不同url源：

>**Centos 7**
>`wget -O CentOS-Base.repo https://lug.ustc.edu.cn/wiki/_export/code/mirrors/help/centos?codeblock=3`
 
 运行 `yum makecache` 生成缓存

##### 4.修改hostname
修改 `/etc/hostname` 文件

`# vim /etc/hostname`

把localhost.hostname改成你想要的值，如VB-cent 。

#### 三、Xshell ssh 到虚拟机
VirtualBox里，“设置-网络”， 选“网络地址转换（NAT）”， “高级”里，“端口转发”添加一条规则，将“子系统端口”填“22”，“主系统端口”设为想要的端口号，比如“1022”。

然后就可以在Xshell里，ssh到 127.0.0.1:1022，也就是我们的虚拟机里了。

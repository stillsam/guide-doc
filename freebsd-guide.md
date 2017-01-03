### Freebsd启动出My unqualified host name unkown...Sleeping for retry...解决方案 

add   
`sendmail_enable="NONE"` to `/etc/rc.conf`  
to disable sendmail if you won't be using it... 

### 修改freebsd可以用sshd权限用户登录ssh
```
PermitRootLogin yes #允许root登录
PermitEmptyPasswords no #不允许空密码登录
PasswordAuthentication yes # 设置是否使用口令验证。
```
重启sshd服务：  
service sshd restart

### 安装vim-lite
pkg install vim-lite

### pkg源

>pkg0.twn.freebsd.org  
>ping为105ms,来自官网 http://pkg.freebsd.org/

设置一下软件源，  
vi /etc/pkg/FreeBSD.conf  

>把`pkg.FreeBSD.org`修改为 `pkg.tw.FreeBSD.org`或者`pkg.jp.FreeBSD.org`速度应该会有较大改善


通过 `pkg.freebsd.org`，用`host -t srv _http._tcp.pkg.freebsd.org`得到的结果，可以替换`/etc/pkg/FreeBSD.conf`中url。 

	url: "pkg+http://pkg.us-west.FreeBSD.org/${ABI}/latest"//,挺快的 
	url: "pkg+http://pkg0.ydx.freebsd.org/${ABI}/latest"//,是俄罗斯那面的吧，反映也快。

我测的 pkg0.isc.freebsd.org 比较好，230ms的延迟，是US West的

```
以下为参考，似乎不行了。

俄罗斯
mirror.yandex.ru/freebsd/

日本
ftp.jaist.ac.jp/pub/FreeBSD/
ftp.iij.ad.jp/pub/FreeBSD/
ftp.yz.yamagata-u.ac.jp/pub/FreeBSD/

台湾
ftp.stu.edu.tw/FreeBSD/
ftp.isu.edu.tw/pub/freebsd/

http://ftp.kr.freebsd.org/   “我是选了这个觉得速度可以，韩国的源”
```

### 使用sudo
`pkg install sudo`  

visudo 配置权限的格式如下：
      
	USER MACHINE=(EFFECTIVE USER)  [NOPASSWD:] COMMAND
        
第一列(USER)指定要授权的帐号。第二列(MACHINE)定义在那些机器上，这条执行生效，其好处是在多台机器上使用同一份配置文件。括号里的(EFFECTIVE USER)是使用指定实际执行该命令的帐号，这就方便一个帐号允许用另外一个帐号来执行特定的命令，而不非得是root帐号。第四列(COMMAND)是指定的命令. NOPASSWD是可选项代表USER在sudo到某身份
时不必输入该身份的密码即可执行命令。
     
     下面是配置sudo的简单方法：
     
        M-gtuiw ALL=(ALL) ALL
   
     指定了M-gtuiw可以在任何地点以任何身份执行整个系统的全部命令。
     
       %wheel ALL=(ALL) ALL
  
     这个命令指定了wheel这个组的用户可以在任何地点以任何身份执行整个系统的全部命令。
     
        M-gtuiw ALL=(apache) /usr/bin
   
     指定了M-gtuiw可以在任何地点但只能以apache用户身份且只能执行/usr/bin目录下的命令。
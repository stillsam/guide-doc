命令行：

`sudo apt-get install python-pip`
`pip install shadowsocks`

我们可以在`/home/martin/` 下新建个文件shadowsocks.json  (martin是我在我电脑上的用户名，这里路径你自己看你的)。内容是这样：
```bash
{
"server":"11.22.33.44",
"server_port":50003,
"local_port":1080,
"password":"123456",
"timeout":600,
"method":"aes-256-cfb"
}
```
server  你服务端的IP
servier_port  你服务端的端口
local_port  本地端口，一般默认1080
passwd  ss服务端设置的密码
timeout  超时设置 和服务端一样
method  加密方法 和服务端一样

确定上面的配置文件没有问题，然后我们就可以在终端输入 `sslocal -c /home/martin/shadowsocks.json` 回车运行。

GUI：

https://github.com/shadowsocks/shadowsocks-qt5/wiki/Installation

##### Ubuntu
PPA is for Ubuntu >= 14.04.

`sudo add-apt-repository ppa:hzwhuang/ss-qt5`
`sudo apt-get update`
`sudo apt-get install shadowsocks-qt5`






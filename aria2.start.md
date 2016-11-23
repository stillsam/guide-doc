#### 小白用户可以直接copy我的配置文件保存成aria2.conf进行使用.

然后在终端里面输入 `aria2c --conf-path=<PATH>`   注意PATH必须是绝对路径.  
例如: D:\aria2\aria2.conf 可以使用 -D 参数使Aria2在后台运行,即使关闭终端也不会停止运行.

Win下可以把这个命令行保存成bat文件进行运行.注意路径不需要使用引号括起来.

接下来是如何管理Aria2的下载任务了,推荐使用binux菊苣的YAAW,超级好用,下载打开即用.
懒得下载的话可以使用在线版,只需在设置里面修改下RPC PATH为 http://localhost:6800/jsonrpc



```
aria2c -D --conf-path=/home/kemon/aria2.conf
```
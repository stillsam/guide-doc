#### 终端的网络访问也用上代理

```bash
export http_proxy=socks5://127.0.0.1:1080
export https_proxy=$http_proxy
```

这个方法应该是最方便的了，不需要开其他软件。
但是如果在终端直接运行的话，每次打开新的session这个代理设置就会失效，永久生效的方法是写入.zshrc或其他配置文件里。
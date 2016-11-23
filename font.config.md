#### 字体配置

默认情况下ArchLinux的字体并不好看，中文字体发虚。通过安装字体渲染包infinality可以改善这个问题。首先需要导入infinality的密钥并在本地签名。

```
# pacman-key -r 962DDE58
# pacman-key --lsign-key 962DDE58
```
然后需要在 `/etc/pacman.conf`中添加infinality的软件源：
```
[infinality-bundle]
Server = http://bohoomil.com/repo/$arch
[infinality-bundle-multilib]
Server = http://bohoomil.com/repo/multilib/$arch
[infinality-bundle-fonts]
Server = http://bohoomil.com/repo/fonts
```
>(或者使用中科大的镜像源，如下)
>```
>[infinality-bundle]
Server = http://mirrors.ustc.edu.cn/infinality-bundle/$arch
>[infinality-bundle-multilib]
Server = http://mirrors.ustc.edu.cn/infinality-bundle/multilib/$arch
>[infinality-bundle-fonts]
Server = http://mirrors.ustc.edu.cn/infinality-bundle/fonts
>```
>如果在更新过程中遇到了签名错误, 您可以选择设置 SigLevel = Optional TrustAll , 或者通过执行以下命令导入公钥来解决
>```
># pacman-key -r 962DDE58
># pacman-key --lsign-key 962DDE58
># pacman -Syy
>```

添加完成之后需要重新刷新缓存，然后就可以安装infinality的软件包了。安装时会提示与freetype2冲突，询问你是否替换，选择是即可。
```
# pacman -Syy
# pacman -S infinality-bundle
```
重启后生效。
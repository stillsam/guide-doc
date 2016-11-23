### archlinux 屏幕亮度调整 (dell studio系列的15z-1569笔记本)


dell studio系列的15z-1569笔记本 装完Archlinux 后，屏幕默认最高亮度，眼睛受不了。Fn切换屏幕亮度的热键无效，无法改变屏幕亮度，很不给力。

linux 需要折腾，经过多种方法终于找到解决办法。

#### 1 先编辑一文件，改变屏幕亮度的脚本。

`vim /usr/local/sbin/brightness.sh`

`echo 1200 > /sys/class/backlight/intel_backlight/brightness`

保存,退出(:wq)

解释一下：

1200是一个自定义值，自已设置适合自己的亮度。不要超过最大值，也不要设置太小，太小了屏幕黑的什么也看不见

**最大值查看方法**

`＃ cat  /sys/class/backlight/intel_backlight/max_brightness`

4882   <-  dell 这个值比较大。

#### 2 增加可执行属性

`# chmod  +x /usr/local/sbin/brightness.sh`

#### 3 系统启动时自动运行改变屏幕亮度的脚本

`＃ vim /etc/rc.local`

增加一下面这一条命令

`/usr/local/sbin/brightness.sh`

保存，退出

#### 4， 重启电脑，看看屏幕的亮度是否降低了！

收工，这下眼睛舒服了。
# overview

这里是平时在使用Macbook Pro的过程中遇到的一些系统小问题和解决方案

## 1\. 解决 macos Sierra 系统「安全性与隐私」设置中没有任何来源选项问题

```
1.打开电脑终端
2.sudo spctl --master-disable
3.输入电脑开机密码
ps：其实对于升级系统前，已经是任何来源选项的，还会显示，不会改变，但别的选项的，升级后就会消失.
```

![](../../static/images/macbook/preference1.png)

## 2\. Macbook 切换用户，更换用户名(/User/niceBoy)等问题

在此路径下可更换当前用户的配置

![](../../static/images/macbook/group1.png)

个人目录选项，如果在/User/下改换成一个新的用户名，则系统会在/Users下生成一个新的用户名文件夹及其空间，当前用户下的所有资料不可访问，但可打开应用程序；

![](../../static/images/macbook/group2.png)

**_注：有一些应该程序，如Chrome 有的时候默认会安装在Macintosh HD下面，mackPro在购买后第一次设置时，当时用户名会和根用户名一致，所有更换用户名会导致类似Macintosh HD下的应用不可访问或者损坏_**

## 3\. macbook pro 锁定屏幕的文案修改

![](../../static/images/macbook/lock_screen_hint.png)

## 4\. mac上npm包的安装路径

打开文件夹->前往->前往文件夹，或者打开文件夹->cmd-shift-G,粘贴

```
/usr/local/lib/node_modules
```

/usr/local/里面是我们下载的东西的库

# overview

这里是平时在使用MacBook Pro的过程中遇到的一些系统小问题和解决方案

## 1.解决 macos Sierra 系统「安全性与隐私」设置中没有任何来源选项问题

```
1.打开电脑终端
2.sudo spctl --master-disable
3.输入电脑开机密码
ps：其实对于升级系统前，已经是任何来源选项的，还会显示，不会改变，但别的选项的，升级后就会消失.
```

![](Images/macBook/preference1.png)

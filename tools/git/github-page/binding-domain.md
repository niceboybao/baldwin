# 简介

现在有很多的前端开发者用XXX.github.io作为自己的博客，然后绑定到自己的域名上面，感觉起来挺不错。一、不用花钱买服务器了，二、一套流程下来前端完全可以搞定。部署完成是这样的 [niceboybao.github.io](http://niceboybao.com/) [niceboybao.com](http://niceboybao.com/) 有创意的小伙伴还可以用现在流行的三大框架(angular,react,或者vue)构建自己的博客工程呢，这一块我也在着手开始，在工作的业余时间，让自己变得更充实！`对没错，生活不止眼前的苟且 还有诗和远方。`下面开始正式环节，以niceboybao为例！

## 主要参考资料

[Using a custom domain with GitHub Pages](https://help.github.com/articles/using-a-custom-domain-with-github-pages/)

[用阿里云免费ssl证书把网站从http变成https](https://jingyan.baidu.com/album/9f7e7ec09c80976f281554f1.html?picindex=8)

## 配置 niceboybao.github.io

### 创建repository

首先需要在GitHub上面创建一个repository，并且命名为`niceboybao.github.io`。

![](https://user-gold-cdn.xitu.io/2018/1/31/1614c1924c69adc2?w=1732&h=540&f=jpeg&s=96363)

### 添加CNAME文件

小伙伴可以把repository克隆下来，在repository下创建一个`CNAME`文件,文件名大写且没有后缀，如下图。文件里面添加需要绑定的域名，注意没有www和https前缀。

![](https://user-gold-cdn.xitu.io/2018/1/31/1614c19a45f9c446?w=1436&h=768&f=jpeg&s=75268)

### settings

然后到repository的设置页面设置将自己的仓库发布到网站上面，并且添加上域名 如图： ![](https://user-gold-cdn.xitu.io/2018/1/31/1614c19fda812a47?w=1516&h=1196&f=jpeg&s=252525)

## 域名解析

现在挺流行的阿里云，我这边用阿里云举例，首先要找到自己购买的域名（控制台->域名与网站(万网)->域名->解析）然后配置下面2步

![](https://user-gold-cdn.xitu.io/2018/1/31/1614c1af9c56cbe9?w=2098&h=570&f=jpeg&s=118670) 第一步，@符号的是指定你的域名xxx.com映射到xxx.github.io，第二布，www那一条是指定你的主域名www.xxx.com映射到xxx.github.io。这边看别人配置的时候都说一定不要忘记`xxx.github.io.`后面的`.`，可是好像加上去了没效果，不知道有没有小伙伴遇到过呢！

配置完了勾选点击启动就ok啦！要全球解析生效，好像得等上一会了。后面就开始你们的表演吧，用自己熟悉的框架开发一个属于自己的blogs吧！[niceboybao.com](http://niceboybao.com/)

另外，在GitHub上面的仓库只要在settings里面把他们发布到网站上面，就可以用niceboybao.com/xxx（xxx表示仓库名）访问到如：[valentines_day](http://niceboybao.com/valentines_day/)。

## 用阿里云免费ssl证书把网站从http变成https

![](https://user-gold-cdn.xitu.io/2018/2/27/161d5ff0380407be?w=200&h=60&f=png&s=9232)

HTTP 协议是不加密传输数据的，也就是用户跟你的网站之间传递数据有可能在途中被截获，破解传递的真实内容，所以使用不加密的 HTTP 的网站是不太安全的。所以， Google 的 Chrome 浏览器将在 2017 年 1 月开始，标记使用不加密的 HTTP 协议的网站为 Not Secure，不安全。

### 登录阿里云后台，找到，产品与服务-》找到证书服务，购买证书

![](https://user-gold-cdn.xitu.io/2018/2/27/161d5f804d1e857e?w=3348&h=1362&f=jpeg&s=392645)

### 找到免费型的DV SSL

![](https://user-gold-cdn.xitu.io/2018/2/27/161d6010aeacc461?w=2006&h=1032&f=jpeg&s=140192)

购买后在订单页面点击`补全`，输入你的域名，如xxx.com，最后提交审核。当证书是已签发状态时，就可下载

+++
author = ""
comments = true
date = "2016-05-18T02:08:49-04:00"
draft = false
image = ""
menu = "main"
share = true
slug = "listen_miao_li"
tags = ["Podcast"]
title = "考拉FM、荔枝FM转换播客"

+++

不知怎么最近播客又开始火起来了，播客即Podcast，是乔布斯将 i`POD`，和broad`CAST`合并起来的。中国内独立播客相对较小，大量内容分散在喜马拉雅、荔枝FM、考拉FM、蜻蜓FM等播客托管网站，个人非常喜欢使用*泛用型*播客客户端订阅：

1. 更好的内容管理
2. 变速播放
3. 记录播放位置
4. 更少干扰，无广告

喜马拉雅默认支持使用播客客户端订阅，参考少数派[http://sspai.com/33246](http://sspai.com/33246),将喜马拉雅专辑地址中`album`前面的数字（和多的那个`/`删掉)，并在URL后加上`.xml`。

荔枝FM和考拉FM则默认不支持使用播客订阅，于是写了一个东西，将荔枝FM和考拉FM中的*播客*或者*专辑*转换成播客客户端进行订阅的地址。使用方法如下:

## 荔枝FM
一般荔枝FM的播客地址如

    http://www.lizhi.fm/48168/

获取播客id `48168`，在播客客户端中订阅即可

    http://listen.miao.li/lizhi/48168/
   
## 考拉FM
考拉FM中的专辑都是类似:

    www.kaolafm.com/zj/DgD9XxEQ.html

我们需要获取其中的`albumid`，你可以查看页面源代码，查找`albumid`,或者使用这个bookmarklet

    javascript:prompt("URL","http://listen.miao.li/kaola/"+document.getElementById("albumID").value+"/")

bookmarklet使用方法，新建一个浏览器书签，将上面的内容设为书签地址，浏览器访问地址为考拉FM时，使用该书签即可得到订阅地址。
![kaolafm bookmarklet](https://dn-zhim.qbox.me/kaolafm_bookmarklet.gif)

## 问题

1. 目前只能将荔枝FM和考拉FM最新的20个节目，之前的节目无法获取。
2. 程序通过抓取原网站内容，如果原网站有变化（例如改版），该程序会无法工作。
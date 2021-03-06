---
author: ""
comments: true
date: "2016-05-18T02:08:49-04:00"
draft: false
image: ""
menu: "main"
share: true
slug: "listen_miao_li"
tags: ["Podcast"]
title: "考拉FM、荔枝FM、网易云音乐电台转换播客"

---

最近播客又开始火起来了，播客即Podcast，是乔布斯将 i`POD`，和broad`CAST`合并起来的。中国内独立播客相对较小，大量内容分散在喜马拉雅、荔枝FM、考拉FM、蜻蜓FM等播客托管网站，个人更喜欢使用*泛用型*播客客户端订阅：

1. 更好的内容管理
2. 变速播放
3. 记录播放位置
4. 更少干扰，无广告

喜马拉雅默认支持使用播客客户端订阅，参考少数派[http://sspai.com/33246](http://sspai.com/33246),将喜马拉雅专辑地址中`album`前面的数字（和多的那个`/`删掉)，并在URL后加上`.xml`。

荔枝FM和考拉FM则默认不支持使用播客订阅，于是写了一个web应用，将荔枝FM和考拉FM中的*播客*或者*专辑*转换成播客客户端进行订阅的地址。使用方法如下:

## 荔枝FM
一般荔枝FM的播客地址如

    http://www.lizhi.fm/48168/

获取播客id `48168`，在播客客户端中以下订阅即可

    http://listen.miao.li/lizhi/48168/ 
   
## 考拉FM
考拉FM中的专辑都是类似:

    www.kaolafm.com/zj/DgD9XxEQ.html

我们需要获取其中的`albumid`，你可以查看页面源代码，查找`albumid`,或者使用这个bookmarklet

    javascript:prompt("URL","http://listen.miao.li/kaola/"+document.getElementById("albumID").value+"/")

bookmarklet使用方法，新建一个浏览器书签，将上面的内容设为书签地址，浏览器访问地址为考拉FM时，使用该书签即可得到订阅地址。
![kaolafm bookmarklet](https://dn-zhim.qbox.me/kaolafm_bookmarklet.gif)


## 网易云音乐 (添加时间2016-05-25)
添加网易云音乐的主播电台支持，网易云音乐电台获取节目的API加密算法不知道，也是只能通过抓取页面的方式。
网易云音乐电台地址一般是:

	http://music.163.com/#/djradio?id:4020

获取URL中id后`4020`,在播客客户端中订阅以下URL即可
	
	http://listen.miao.li/netease/4020/

## 缓存逻辑 (更新时间2016-06-03)
最近发现客户端例如[Overcast](http://overcast.fm/)，都是使用服务器端抓取的，而我现在处理请求的方式是每次有请求则实时去抓取页面，抓取页面后返回XML内容。这样的方式实时性最好，但是比较耗费服务器资源，于是做了一个缓存机制。系统在请求时判断是否有缓存，有缓存则发送缓存，如果上次现在距更新缓存的时间超过2小时，系统会添加一个更新缓存的任务(task queue)。


## 问题

1. 目前只能将荔枝FM和考拉FM最新的20个节目，之前的节目暂时无法获取。网易云音乐的节目数限制暂为500期
2. 程序通过抓取原网站内容，如果原网站有变化（例如改版），该程序会无法工作。
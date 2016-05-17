---
date: '2016-05-17'
draft: false
title: Chrome中启用mactype
slug: chrome_enable_mactype

---
Windows的字体渲染一直难以忍受，于是安装了Mactype，可以在Windows中体验Mac中的字体渲染效果，但是Mactype在Chrome浏览器中似乎不生效。于是：

原帖应该位于： https://www.reddit.com/r/chrome/comments/3l49gm/how_to_using_mactype_with_chrome_45/
翻译转贴于：http://tieba.baidu.com/p/4197666762

步骤1： 浏览器地址栏打开chrome://flags 
步骤2：启动 “禁用DirectWrite” #disable-direct-write 
步骤3：启用 “Enable one-copy rasterizer”即#enable-one-copy（46版本以上默认就是启用的，忽略这一步） 
步骤4：调整Number of raster threads 光栅线程数(#num-raster-threads) 为1 ps：在chrome://flags页面中找不到这几项，可以利用浏览器右上角菜单中的查找工具(<kbd>Ctrl</kbd> + <kbd>F</kbd>)， 设置完成在该页面左下角有重启浏览器按钮。
步骤5： 按这个帖子的方法http://tieba.baidu.com/p/3620746806 在chrome的快捷方式后面加上 --disable-directwrite-for-ui （注意空格） 
步骤6： 完全关闭chrome，可以调用任务管理器来关闭 

enjoy

pps: 步骤五是有必要的，可以解决chrome右键、选单无法渲染的问题。
但步骤四好像不需要。详见http://tieba.baidu.com/p/3616752082


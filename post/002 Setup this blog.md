---
date: "2016-05-07T10:58:00"
draft: true
title: "使用Caddy Server和hugo还有git简单建设博客"
slug: "blog_using_caddy_hugo_git"

---

使用Caddy Server和hugo还有git简单建设博客

Caddy是一个配置简单的服务器，使用Go语言开发，配置非常简单，开箱即用。最喜欢的特色功能有:
1. 支持http/2[^1]
2. 默认使用https，自动获取、配置、续期let's encrypt证书

## 准备工作

1. Debian 8的VPS，我使用的VPS提供的Debian 8 86_X64_minimal,即64位最简配置。没有安装apache2，如果有安装apache2,需要卸载
2. Hugo, 静态博客生成器
3. Caddy, 服务器
4. Git 用于管理博客内容

## 准备服务器

1. 更新服务器和安装git
    apt-get update && apt-get upgrade
    apt-get install git
2. 安装hugo
访问hugo的github release 页面下载对应服务器版本的deb文件包。下载到服务器
    dpkg -i hugo.deb
安装完成后，运行hugo --help试一下
3. 安装caddy
访问caddy server的下载页面，feature勾上git和hugo。下载对应服务器版本。

## 配置Caddy

### 使用Caddyfile

### 配置systemd
使用systemd配置caddy为一个服务，保证caddy总是能正常运行。
## 配置Git

### 使用 Webhook 实时更新

## 配置Hugo


## 下一步？
使用其他工具进行进行写作。


[^1]: http/2 是基于Google SPDY 的协议，目标是更快，更低的延迟。[https://http2.github.io](https://http2.github.io)


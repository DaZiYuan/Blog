---
title: 巨应动态壁纸-官方网站
date: 2018-10-19 11:05:00
categories: products
tags:
---

<center><img  style="display:inline !important;width:200px;height:200px" src="/res/imgs/products/logo_livewallpaper.png"/></center>
## 用意：
* 真正免费无功能限制开源的动态壁纸软件

## 关于本项目：
  * 动态壁纸的WPF实现版本，类似wallpaper engine
  * 只支持Win10比较新的版本，因为用了Win10特性
  * Golang制作的一个小型解析器，有兴趣的可以按源码api，开发自己的壁纸源。
  * UI能省既省，我的目的是动态壁纸，不希望在UI花太多精力。也不想为了实现一点UI，搞太多黑科技。
  （漂亮的UI是系统或框架应该做的事，不要逆系统而为。
  例如UWP天生比WPF美省内存。用Winform制作UWP的感觉,浪费一些无益的开销，这是我的最新感受）
  * 有Win10内购只是一种捐赠形式，没有功能限制。但是目前商店不知道能否通过，无法使用。
  *  语言其实是支持的，鉴于我的英语水平没有翻译。有好心人可以pull这里  [链接](https://github.com/MscoderStudio/LiveWallpaper/blob/master/LiveWallpaper/Res/Languages/zh.json)
  * c#交流群：191034956
  
## 开发者寄语：
* 这款软件我做了很久，一开始只是一个demo研究如何制作动态壁纸。后来我利用Desktopbridge和UWP打算把他开发成一个产品。
* 本项目是开源项目，内购只是一种捐赠的形式

## 历史记录：
* **v1.0**：基本功能完成。
    目前的不足：
    * 只支持视频壁纸，exe和web其实demo是支持的，实现也很容易。后面看用户反馈，有需求在做
    * 声音无法关闭，可以通过系统音量混合器，禁音Livewallpaper。后面看用户反馈，有需求在做
    * 不支持自定义分组。后面看用户反馈，有需求在做
    * 对WPF性能的一些担忧（打算用Go制作一个纯净版，直接用Web UI控制。或者用进程通信，每次UI可以完全释放，只保留壁纸核心进程省内存，都只是初步想法，是否实现还是看用户量吧）

## 下载地址：
* [Win10商店](https://www.microsoft.com/store/apps/9MV8GK87MZ05)
* [Github](https://github.com/MscoderStudio/LiveWallpaper)
* [用户交流群](/about/contact.html)

## 截图预览：
## 客户端
![client](/res/imgs/products/livewallpaper/client.png)
## 商店
![store](/res/imgs/products/livewallpaper/store.png)
## 早期Demo
![早期Demo](/res/imgs/products/livewallpaper/example.gif)

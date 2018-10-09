title: hexo next主题 禁用代码段.code pre滚动条以及自动换行
author: 打字员
tags:
  - css
  - hexo
categories:
  - hexo
date: 2018-10-09 17:46:00
---
##### 解决以下问题:
* Hexo 插入代码段有时候会显示垂直滚动条导致无法滚动问题
* 超出边框会显示横向滚动条难看问题

##### 第一步：
打开这个文件
themes\next\source\css\_common\components\highlight\highlight.styl

##### 第二布：
按下面代码修改样式

```CSS
  .code pre {
		// width: 100%  注释这句或者下面两句，解决有时候会显示垂直滚动条问题
    padding-left: 10px
    padding-right: 10px
    background-color: $highlight-background
    white-space: pre-wrap  //自动换行，不显示横向滚动条
    word-wrap: break-word  //自动换行，不显示横向滚动条
  }
```
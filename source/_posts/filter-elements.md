title: Javascript 查找包括指定文字的所有元素
author: 打字员
tags:
  - JavaScript
categories:
  - JavaScript
date: 2018-10-09 10:44:00
---
##### 利用ES2015原声支持的querySelectorAll查找包含指定文本的元素

例如查找steam市场页面的所有撤下按钮:
steamcommunity.com/market/

```Javascript
//查找所有
Array.from(
                    document.querySelectorAll(".item_market_action_button_contents")
                ).filter(el => el.innerText === '撤下');

//查找第一个
Array.from(
                    document.querySelectorAll(".item_market_action_button_contents")
                ).find(el => el.innerText === '撤下');
```
title: electron-react-boilerplate调试主进程
author: 打字员
tags:
  - JavaScript
categories:
  - JavaScript
date: 2018-11-13 17:11:00
---
electron-react-boilerplate如何调试

1.修改package.json,增加 --inspect=5858
```
    "start-main-dev": "cross-env HOT=1 NODE_ENV=development electron -r @babel/register --inspect=5858 ./app/main.dev.js",
```
2.访问chrome://inspect/#devices。点击Configure增加5858端口
title: Golang Json 结构体互转
author: 打字员
tags:
  - Golang
categories:
  - Golang 代码片段
date: 2018-09-27 11:34:00
---
#### 目的
记录如何在golang中进行json序列化和反序列化（与结构体互转）操作的相关代码片段

#### 结构体定义

```Go
type Tag struct {
	createTime string
	tagId      string
	isDelete   string
	tagName    string
}

type Tags struct {
	data []Tag
	flag bool
}

```

#### Json字符串转为结构体
```Golang
func GetTags() (rTags Tags) {
	//请求服务器获取json
	res, err := http.Get("http://wallpaper.upupoo.com/async/getTags.htm?callback=")
	if err != nil {
		log.Fatal(err)
	}
	jsonStr, err := ioutil.ReadAll(res.Body)
	res.Body.Close()
	if err != nil {
		log.Fatal(err)
	}

	//反序列化
	if err := json.Unmarshal(jsonStr, &rTags); err != nil {
		//反序列化错误
		log.Fatal(err)
	}
	return
}

```
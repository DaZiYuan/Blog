title: Golang slice切片映射
author: 打字员
tags:
  - Golang
categories:
  - Golang
date: 2018-09-30 18:10:00
---
#### 记录如何把切片转换为另一个不同结构体的切片

结构体A：
```Golang
//大写开头才能在外部包中访问
type UTag struct {
	CreateTime int    `json:"createTime"` //Jsontag 是映射json对应的字段
	TagId      int    `json:"tagId"`
	IsDelete   int    `json:"isDelete"`
	TagName    string `json:"tagName"`
}

type UTags struct {
	Data []UTag `json:"data"`
	Flag bool   `json:"flag"`
}
```
结构体B:
```Golang
type Tag struct {
	ID   int
	Name string
}
```

#### 功能：把UTags.Data转换成 []Tag
```Golang
func GetTags() (result []model.Tag, err error) {
	//请求服务器获取json
	res, err := http.Get("http://wallpaper.upupoo.com/async/getTags.htm?callback=")
	if err != nil {
		return
	}

	body, err := ioutil.ReadAll(res.Body)
	res.Body.Close()
	if err != nil {
		return
	}

	//多了两个括号需要移除掉
	tmpJson := string(body[1 : len(body)-1])
	// 反序列化
	var temp UTags
	err = json.Unmarshal([]byte(tmpJson), &temp)

	// UTags转换成标准Tags
	for _, v := range temp.Data {
		result = append(result, model.Tag{ID: v.TagId, Name: v.TagName})
	}
	return
}
```

这是我开发 [解析第三方壁纸服务](https://github.com/MscoderStudio/LiveWallpaperServer) 中的代码，记录一下Golang的自学过程，也希望帮到和我遇到一样问题的人。

巨应工作室第一年，国庆快乐~

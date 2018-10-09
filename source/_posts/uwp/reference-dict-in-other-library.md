title: UWP 引用其他Class Library库中的样式文件
author: 打字员
date: 2018-10-09 23:57:26
tags:
---
###### 如果样式库和调用库不是在同一解决方案中，首先要在样式库的属性页中勾选"Generate library layout"
![图片](/res/imgs/posts/Fh20j.jpg)

###### 引用代码：

```Xaml
<ResourceDictionary>
    <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="ClassLibrary1/Styles/Custom.xaml" />
        <ResourceDictionary Source="ClassLibrary1/Styles/ButtonStyle.xaml"/>
        <ResourceDictionary Source="ClassLibrary1/Styles/ListsStyle.xaml"/>
    </ResourceDictionary.MergedDictionaries>
</ResourceDictionary>
```
或者
```Xaml
<ResourceDictionary>
    <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="ms-appx:///ClassLibrary1/Styles/Custom.xaml" />
        <ResourceDictionary Source="ms-appx:///ClassLibrary1/Styles/ButtonStyle.xaml"/>
        <ResourceDictionary Source="ms-appx:///ClassLibrary1/Styles/ListsStyle.xaml"/>
    </ResourceDictionary.MergedDictionaries>
</ResourceDictionary>
```
title: UWP 读写其他目录的文件  Broader file-system access
author: 打字员
tags:
  - UWP
categories:
  - UWP
date: 2018-10-15 10:01:00
---
##### 概要：
曾经UWP只能读写当前应用的存储目录。  
2018年微软开放了一种更广泛的IO读写权限，使UWP可以像传统应用程序一样读写几乎所有目录。让UWP的能力更上一层楼。

[相关连接](https://blogs.windows.com/buildingapps/2018/02/23/windows-community-standup-discussing-multi-instancing-console-uwps-broader-file-system-access/#lDQ5SHeBiXKQsbHM.97)

##### 如何开启：
打开Package.appxmanifest。
添加命名空间rescap，并将其添加到IgnorableNamespaces：
```XML
<Package
  ...
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
  IgnorableNamespaces="uap mp uap5 rescap">
...
<Capabilities>
    <rescap:Capability Name="broadFileSystemAccess" />
</Capabilities>
```

##### 创建文件:
```CSharp
//写入文件
    string dir = "d:\\";
    string fileName = "sample.txt";
    string fullPath = Path.Combine(dir, fileName);
    StorageFolder storageFolder = await StorageFolder.GetFolderFromPathAsync(dir);
    StorageFile writeFile = await storageFolder.CreateFileAsync(fileName, CreationCollisionOption.ReplaceExisting);
    await FileIO.WriteTextAsync(writeFile, DateTime.Now.ToString());

    //读取文件
    StorageFile readFile = await storageFolder.GetFileAsync(fileName);

    //全路径读取
    //StorageFile readFile = await StorageFile.GetFileFromPathAsync(fullPath);
    var stream = await readFile.OpenAsync(FileAccessMode.Read);
    ulong size = stream.Size;
    using (var inputStream = stream.GetInputStreamAt(0))
    {
        using (var dataReader = new Windows.Storage.Streams.DataReader(inputStream))
        {
            uint numBytesLoaded = await dataReader.LoadAsync((uint)size);
            string text = dataReader.ReadString(numBytesLoaded);
        }
    }
```

测试发现系统盘根目录还是没有权限，其他目录可以。已经可以满足大多数需求了。
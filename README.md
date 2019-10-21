# Flutter FileReader
[![pub package](https://img.shields.io/pub/v/flutter_filereader.svg)](https://pub.dartlang.org/packages/flutter_filereader)

##### 一个本地文件浏览的工具,Android端使用腾讯x5浏览器实现,iOS端使用WKWebView实现
## Usage
 
 
### iOS
Make sure you add the following key to Info.plist for iOS
```
<key>io.flutter.embedded_views_preview</key><true/>
```
 
### Example
```
import 'package:flutter/material.dart';
import 'package:flutter_filereader/flutter_filereader.dart';

class FileReaderPage extends StatefulWidget {
  final String filePath;

  FileReaderPage({Key: Key, this.filePath});

  @override
  _FileReaderPageState createState() => _FileReaderPageState();
}

class _FileReaderPageState extends State<FileReaderPage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("文档"),
      ),
      body: FileReaderView(
        filePath: widget.filePath,
      ),
    );
  }
}
```


## 注意事项

1. Android端不支持x86和64位arm(x5不支持),解决办法参考[x5如何支持64位手机](https://x5.tencent.com/tbs/technical.html#/detail/sdk/1/34cf1488-7dc2-41ca-a77f-0014112bcab7 "x5如何支持64位手机")
2. 因为问题1,所以在debug模式下,64位机器会显示x5内核加载不成功。主要是debug模式下,Flutter引擎会根据连接的机器打入对应的库,一但包含有armv8-a,则无法加载x5内核所需的so库
3. txt文档如果显示乱码,请将txt文档编码改成gbk


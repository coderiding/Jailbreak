[https://github.com/lefex/WeChatShot](https://github.com/lefex/WeChatShot)

- 有时候我想知道app使用的第三方库，但是使用 class-dump 导出的头文件非常多，仅靠肉眼查看时，根本不能很好的找出来。于是有人发明了一个工具，能够获取某个app的三方库，并且查看pod库的star数，以及源地址。
- 该工具的实现原理是利用三方库的头文件去反查第三方库。
- 在GitHub - lefex/WeChatShot中下载源码。
- 下载源码后修改main.py文件的IPA_HEADER_PATH为 class-dump 导出的头文件目录。
- 命令行cd到main.py目录中，执行python [main.py](http://main.py/)。

下载源码后修改main.py文件的IPA_HEADER_PATH为 class-dump 导出的头文件目录。

命令行cd到main.py目录中，执行python3 [main.py](http://main.py/)。
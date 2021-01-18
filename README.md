# Jailbreak
越狱体验

学习目标：破解一款应用，安装到别人的手机上。重签名一个ipa文件。

### 逆向思路

1、界面分析（Cycript、Reveal）

2、代码分析（提取ipa，分析mach-O，对Mach-O文件的静态分析MachOView、class-dump、Hopper Disassembler、ida等）

3、动态调试（对运行中的APP进行代码调试debugserver、LLDB）

4、代码编写（注入代码到APP中，必要时还可能需要重新签名、打包ipa）

参考：

* http://bbs.iosre.com/
* https://github.com/jackrex/FakeWeChatLoc(手把手教你制作一款iOS越狱App，伪装微信位置)
* https://github.com/lanvsblue/AppBrowser (AppBrowser(Application属性查看器，不需要越狱！！！))
* https://mp.weixin.qq.com/s?__biz=MzUzMTk3ODc0OA==&mid=2247484391&idx=1&sn=7684c851bc3a9f9ebd234014baffe706(分析一个App需要的技术手段)
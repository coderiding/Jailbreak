# 越狱的Cycript语言

* https://github.com/CoderMJLee/mjcript
* 【越狱-逆向】基于Cycript实现的一些实用函数


### Cycript语言

* Cycript是Objective-C++、ES6（JavaScript）、Java等语法的混合物
* 可以用来探索、修改、调试正在运行的Mac\iOS APP
* 官网： http://www.cycript.org/
* 文档： http://www.cycript.org/manual/
* 通过Cydia安装Cycript，即可在iPhone上调试运行中的APP

### Cycript的开启和关闭
* 开启
* cycript
* cycript -p 进程ID  // 使用命令ps -A来查看 ，那个app记得要打开，这样才能在进程中找到
* cycript -p 进程名称 // 与上面的2选一

* 列出所有的进程
* ps –A
* ps aux

* 搜索关键词
* ps –A | grep 关键词

* 取消输入：Ctrl + C
* 退出：Ctrl + D
* 清屏：Command + R

### 常用语法1

* UIApp
* [UIApplication sharedApplication]
* UIApp.keyWindow.rootViewController

* 定义变量
* var 变量名 = 变量值
* var app = UIApp.keyWindow
* app

* 用内存地址获取对象

```
#内存地址
```

* ObjectiveC.classes
* 已加载的所有OC类

* 查看对象的所有成员变量
* *对象

### 常用语法2
* 递归打印view的所有子控件（跟LLDB一样的函数）
* view.recursiveDescription().toString()

* 筛选出某种类型的对象
* choose(UIViewController)
* choose(UITableViewCell)

---

### 封装Cycript - .cy文件编写
* 我们可以将常用的Cycript代码封装在一个.cy文件中
* exports参数名固定，用于向外提供接口

### 封装Cycript - 存放和使用.cy文件
* 将.cy文件存放到/usr/lib/cycript0.9目录下
* 在Cycript中引用.cy文件，并使用它提供的接口

### Cycript库
* https://github.com/CoderMJLee/mjcript
* 具体用法参考mjcript.cy文件

#### mjcript使用
* 1、下载mjcript库
* 2、将mjcript.cy文件拖到/usr/lib/cycript0.9
* 3、SSH连接iOS设备
* 4、使用Cycript监听APP，通过@import导入mjcript
* @import mjcript

#### mjcript一些常用属性
* MJAppId
* MJAppPath
* MJDocPath
* MJCachesPath
* MJFrontVc() // 拿到显示在最前面的控制器

### 利用python打印字符
```objectivec
UIApp
[UIApplication sharedApplication]

定义变量
var 变量名 = 变量值

用内存地址获取对象
#内存地址

ObjectiveC.classes
已加载的所有OC类

查看对象的所有成员变量
*对象
```

- 递归打印view的所有子控件（跟LLDB一样的函数）

```objectivec
view.recursiveDescription().toString()
```

- 筛选出某种类型的对象

```objectivec
choose(UIViewController)
choose(UITableViewCell)
```
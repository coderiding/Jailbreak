# 第三步：研究越狱脱壳后的Mach-o文件

*  查看mach-o文件类型
```
file xxx
```

### 使用class-dump查看头文件
* 1.首先获取到ipa里面的mach-o
* 2.然后这个mach-o必须脱壳
* 3.class-dump -H To-Do -o Headers

### 使用Hopper查看汇编代码

### 使用MachOView查看
* https://github.com/gdbinit/MachOView

### 使用otool查看mach-o文件
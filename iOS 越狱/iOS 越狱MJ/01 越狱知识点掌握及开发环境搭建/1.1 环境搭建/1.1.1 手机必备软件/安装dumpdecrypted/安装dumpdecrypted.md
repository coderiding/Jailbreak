- 最早的砸壳工具是stefanesser写的dumpdecrypted，通过手动注入然后启动应用程序在内存进行dump解密后的内存实现砸壳，这种砸壳只能砸主App可执行文件。
- 对于应用程序里面存在framework的情况可以使用conradev的dumpdecrypted，通过_dyld_register_func_for_add_image注册回调对每个模块进行dump解密。但是这种还是需要拷贝dumpdecrypted.dylib，然后找路径什么的，还是挺麻烦的。

[https://github.com/stefanesser/dumpdecrypted/](https://github.com/stefanesser/dumpdecrypted/)
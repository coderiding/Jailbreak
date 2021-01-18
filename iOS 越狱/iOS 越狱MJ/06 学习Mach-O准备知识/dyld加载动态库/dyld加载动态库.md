dyld动态链接编辑器是Mach-O文件MH_DYLINKER类型

- 通过dyld加载
- dyld源码[https://opensource.apple.com/tarballs/dyld/](https://opensource.apple.com/tarballs/dyld/)
    - dynamic link editor，动态链接编辑器
    - dynamic loader，动态加载器
- 在Mac\iOS中，是使用了/usr/lib/dyld程序来加载动态库 
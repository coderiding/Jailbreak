如果想单独分析动态库的某个framework，就把它从动态共享库抽取出来

### 抽取方法

- 步骤1：获取dsc_extractor.cpp

```objectivec
可以使用dyld源码中的launch-cache/dsc_extractor.cpp

将#if 0前面的代码删除（包括#if 0），把最后面的#endif也删掉
```

- 步骤2 ：编译dsc_extractor.cpp

```objectivec
clang++ -o dsc_extractor dsc_extractor.cpp
```

- 步骤3：使用dsc_extractor

./dsc_extractor 动态库共享缓存文件的路径 用于存放抽取结果的文件夹
1. 编写Tweak代码
2. $make：编译Tweak代码为动态库（*.dylib）
3. $make package：将dylib打包为deb文件
4. $make install：将deb文件传送到手机上，通过Cydia安装deb
5. 插件将会安装在/Library/MobileSubstrate/DynamicLibraries文件夹中
    1. .dylib：编译后的Tweak代码
    2. .plist：存放着需要hook的APP ID
6. 当打开APP时
    1. Cydia SubStrate(Cydia已自动安装的插件)会让APP去加载对应的dylib
    2. 修改APP内存中代码逻辑，去执行dylib中的函数代码
7. 所以，theos的tweak并不会对APP原来的可执行文件进行修改，仅仅是修改了内存中的代码逻辑

### 疑问？

1. 未脱壳的APP是否支持tweak？（支持，因为tweak是在内存中实现的，并没有修改.app包中的可执行文件）
2. tweak效果是否永久性的？（取决于tweak中用到的app代码是否被修改过）
3. 如果一旦更新app，tweak会不会失效？（取决于tweak中用到的app代码是否被修改过）
4. 未越狱的手机是否支持tweak（不支持）
5. 能不能对Swift/C函数进行tweak（可以，方式跟OC不一样）
6. 能不能对游戏项目进行tweak（可以，但是游戏大多是通过C++/c#编写的，而且类名、函数名会进行混淆操作）
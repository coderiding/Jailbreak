# Tweak介绍和Theos环境安装

## Tweak介绍
* Tweak的实质就是iOS平台的动态库（iOS包含dylib与framework两种动态库）
* Framework用的比dylib多。
* Tweak使用dylib动态库。
* Tweak目录（越狱手机中所有Tweak）
	* /Library/MobileSubstrate/DynamicLibraries
	* 包含plist文件（plist文件是用来标识该Tweak的作用范围）
	* 包含bundle文件（bundle是Tweak所用到的资源文件）

---

* 一般使用Tweak是通过Theos.
* iOS越狱开发中，各种破解补丁的统称为Tweak,通常意义上我们说的越狱开发,都是指开发一个Tweak.基本上,Tweak都依赖于一个名叫cydia Substrate (以前名字也叫Mobile Substrate)的动态库
* Mobile Substrate是Cydia的作者Jay Freeman (@saurik)的作品，也叫Cydia Substrate,它的主要功能是hook某个App，修改代码比如替换其中方法的实现，Cydia上的Tweak都是基于Mobile Substrate实现的.


## Theos开发环境搭建
* 安装dpkg和ldid，前者是用来打包deb的，后者用来签名
```
brew install dpkg ldid
```

* 下载theos代码到/opt/theos 目录下，并修改权限(下面两条命令)
* （汶：recursive参数表示递归下载，所以依赖的子模块也会下载）
```
sudo git clone --recursive https://github.com/theos/theos.git /opt/theos
sudo chown $(id -u):$(id -g) /opt/theos
```

* 修改~/.bash_profile环境变量，在该文件下面添加
```
export THEOS=/opt/theos
export PATH=/opt/theos/bin/:$PATH
```

* 在终端刷新环境变量
```
source ~/.bash_profile
```

## Tweak工程创建

* Theos环境部署好了之后，可以通过下面开始测试是否已经部署成功。

##### 第一步：Tweak创建
* （命令路径：/opt/theos/bin/nic.pl）

```
nic.pl
```

* 按照下面的操作
```
[1.] iphone/activator_event
[2.] iphone/application_modern
[3.] iphone/cydget
[4.] iphone/flipswitch_switch
[5.] iphone/framework
[6.] iphone/ios7_notification_center_widget
[7.] iphone/library
[8.] iphone/notification_center_widget
[9.] iphone/preference_bundle_modern
[10.] iphone/tool
[11.] iphone/tweak
[12.] iphone/xpc_service

Choose a Template (required): 11（汶：选择11，选择tweak工程）
Project Name (required): MyFirstRePoject（汶：工程名）
Package Name [com.yourcompany.myfirstrepoject]: com.iosre.myfirstrepoject（汶：deb包的名字）
Author/Maintainer Name [chenzhou]: chuck（汶：作者）
[iphone/tweak] MobileSubstrate Bundle filter [com.apple.springboard]: com.apple.springboard（汶：Tweak作用对象的bundle indentifier）
[iphone/tweak] List of applications to terminate upon installation (space-separated, '-' for none) [SpringBoard]: SpringBoard（汶：Tweak安装完成后需要重启的应用）
Instantiating iphone/tweak in myfirstrepoject/...
Done.
```
* 如果出现上面到结果表示安装成功！


##### 第二步：Tweak发布

* Tweak两种发布方式
	* 在越狱设备上安装的打包成deb格式的安装包
	* 直接使用开发者自己的证书/企业证书直接将补丁打包成ipa,这样不需要越狱也是可以安装的,只是这种非越狱的限制比较大,通常只是用来给某个app打个补丁或者类似的功能啥的

---

参考链接：

* https://www.zybuluo.com/xidianli/note/809841  （百度网盘备份 + 印象笔记备份）
方式一：越狱工具方式

方式二：通过查看AppInfoPlist方式（未越狱iOS11版本下可以通过私有方法查看）

猥琐一点：遍历/var/mobile/Applications/XXX/XXX.app/Info.plist；

优雅一点：SpringBoard中通过SBApplicationController拿到所有SBApplication，从中取出bundle ID
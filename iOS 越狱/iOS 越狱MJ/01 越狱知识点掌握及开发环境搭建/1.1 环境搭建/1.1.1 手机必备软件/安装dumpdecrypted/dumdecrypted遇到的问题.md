[]()

![https://gitee.com/threecornerstones/ThreeCornerstones_Pic/raw/master/uPic/OwW45P.png](https://gitee.com/threecornerstones/ThreeCornerstones_Pic/raw/master/uPic/OwW45P.png)

[https://gitee.com/threecornerstones/ThreeCornerstones_Pic/raw/master/uPic/OwW45P.png](https://gitee.com/threecornerstones/ThreeCornerstones_Pic/raw/master/uPic/OwW45P.png)

原因：对dylib所在的文件夹权限不够

解决方案：将dylib放在用户所在文件夹，比如
如果是root用户，请将dylib放在/var/root目录
如果是mobile用户，请将dylib放在/var/mobile目录
- 步骤1：下载源代码，然后在源代码目录执行make指令进行编译，获得dylib动态库文件
- 步骤2：将dylib文件拷贝到iPhone上（如果是root用户，建议放/var/root目录）
- 步骤3：终端进入dylib所在的目录
- 步骤4:使用环境变量DYLD_INSERT_LIBRARIES将dylib注入到需要脱壳的可执行文件（可执行文件路径可以通过ps -A查看获取）DYLD_INSERT_LIBRARIES=dumpdecrypted.dylib  可执行文件路径

- .decrypted文件就是脱壳后的可执行文件

    ![https://gitee.com/threecornerstones/ThreeCornerstones_Pic/raw/master/uPic/aO7l7I.png](https://gitee.com/threecornerstones/ThreeCornerstones_Pic/raw/master/uPic/aO7l7I.png)
 
# **通过命令行操作iPhone**

### 了解SSH、OpenSSH

* SSH
* Secure Shell的缩写，意为“安全外壳协议”，是一种可以为远程登录提供安全保障的协议
* 使用SSH，可以把所有传输的数据进行加密，“中间人”攻击方式就不可能实现，能防止DNS欺骗和IP欺骗

* OpenSSH
* 是SSH协议的免费开源实现
* 可以通过OpenSSH的方式让Mac远程登录到iPhone

### 了解SSL、OpenSSL
* 很多人会将SSH、OpenSSH、SSL、OpenSSL搞混

* SSL
* Secure Sockets Layer的缩写，是为网络通信提供安全及数据完整性的一种安全协议，在传输层对网络连接进行加密

* OpenSSL
* SSL的开源实现
* 绝大部分HTTPS请求等价于：HTTP + OpenSSL
* OpenSSH的加密就是通过OpenSSL完成的

* SSH的版本
* SSH协议一共2个版本
* SSH-1
* SSH-2
* 现在用的比较多的是SSH-2，客户端和服务端版本要保持一致才能通信
* 查看SSH版本（查看配置文件的Protocol字段）
* 客户端：/etc/ssh/ssh_config
* 服务端：/etc/ssh/sshd_config






### SSH的通信过程
* SSH的通信过程可以分为3大主要阶段
* 建立安全连接
* 客户端认证
* 数据传输

#### 建立安全连接
* 在建立安全连接过程中，服务器会提供自己的身份证明
* Mac-客户端~/.ssh/known_hosts
* iPhone-服务器端
    * 公钥/etc/ssh/ssh_host_rsa_key.pub
    * 私钥/etc/ssh/ssh_host_rsa_key
* 如果客户端并无服务器端的公钥信息，就会询问是否连接此服务器

#### 服务器身份信息变更
* 在建立安全连接过程中，可能会遇到以下错误信息：提醒服务器的身份信息发生了变更
* 如果确定要连接此服务器，删除掉之前服务器的公钥信息就行
* ssh-keygen -R 服务器IP地址
* 或者直接打开known_hosts文件删除服务器的公钥信息就行
* vim ~/.ssh/known_hosts



#### SSH的客户端认证方式
* SSH-2提供了2种常用的客户端认证方式
    * 基于密钥的客户端认证
    * 使用账号和密码即可认证

* 基于密钥的客户端认证
    * 免密码认证「mx：不需要每次登录的时候都输入密码」
    * 最安全的一种认证方式
* SSH-2默认会优先尝试“密钥认证”，如果认证失败，才会尝试“密码认证”

#### SSH - 基于密钥的客户端认证
* Mac客户端
    * 公钥~/.ssh/id_rsa.pub
    * 私钥~/.ssh/id_rsa
* 将公钥内容追加到授权文件尾部
* 登录认证
* iPhone服务器端
* 授权文件~/.ssh/authorized_keys




--------------- 拷贝mac的公钥到手机方法1：
具体步骤:
* 在客户端生成一对相关联的密钥（Key Pair）：一个公钥（Public Key），一个私钥（Private Key）
* ssh-keygen
* 一路敲回车键（Enter）即可
* OpenSSH默认生成的是RSA密钥，可以通过-t参数指定密钥类型
* 生成的公钥：~/.ssh/id_rsa.pub
* 生成的私钥：~/.ssh/id_rsa

* 把客户端的公钥内容追加到服务器的授权文件（~/.ssh/authorized_keys）尾部
* ssh-copy-id root@服务器主机地址 
* 例如：ssh-copy-id root@192.168.1.9
* 需要输入root用户的登录密码  root和mobile用户的初始登录密码都是alpine
* ssh-copy-id会将客户端~/.ssh/id_rsa.pub的内容自动追加到服务器的~/.ssh/authorized_keys尾部

* 注意：由于是在~文件夹下操作，所以上述操作仅仅是解决了root用户的登录问题（不会影响mobile用户）

遇到问题：mkdir: cannot create directory `.ssh': File exists
* rm ~/.ssh 去iphone上移除这个文件就行，然后在尝试上面的命令




--------------- 拷贝mac的公钥到手机方法2：公钥 >> 授权文件

* 可以使用ssh-copy-id将客户端的公钥内容自动追加到服务器的授权文件尾部，也可以手动操作
* 复制客户端的公钥到服务器某路径
* scp ~/.ssh/id_rsa.pub root@服务器主机地址:~
* scp是secure copy的缩写，是基于SSH登录进行安全的远程文件拷贝命令，把一个文件copy到远程另外一台主机上
* 上面的命令行将客户端的~/.ssh/id_rsa.pub拷贝到了服务器的~地址

* SSH登录服务器
* ssh root@服务器主机地址
* 需要输入root用户的登录密码

* 在服务器创建.ssh文件夹
* mkdir .ssh

* 追加公钥内容到授权文件尾部
* cat ~/id_rsa.pub >> ~/.ssh/authorized_keys

* 删除公钥
* rm ~/id_rsa.pub

* 查看服务器的授权文件
* cat .ssh/authorized_keys

------------- 文件权限问题

* 如果配置了免密码登录后，还是需要输入密码，需要在服务器端设置文件权限
* chmod 755 ~
* chmod 755 ~/.ssh
* chmod 644 ~/.ssh/authorized_keys





-------------------------------------


### 通过USB-SSH来登录
* iPhone默认是使用22端口进行SSH通信，采用的是TCP协议
* 端口就是设备对外提供服务的窗口，每个端口都有个端口号（范围是0~65535，共2^16个）
* * 有些端口号是保留的，已经规定了用途，比如
21端口提供FTP服务
* 80端口提供HTTP服务
* 22端口提供SSH服务（可以查看/etc/ssh/sshd_config的Port字段）
* 更多保留端口号： https://baike.baidu.com/item/%E7%AB%AF%E5%8F%A3%E5%8F%B7/10883658#4_3

* 默认情况下，由于SSH走的是TCP协议，Mac是通过网络连接的方式SSH登录到iPhone，要求iPhone连接WiFi
* 为了加快传输速度，也可以通过USB连接的方式进行SSH登录
* Mac上有个服务程序usbmuxd（它会开机自动启动），可以将Mac的数据通过USB传输到iPhone
* /System/Library/PrivateFrameworks/MobileDevice.framework/Resources/usbmuxd


#### usbmuxd的使用1
* 下载usbmuxd工具包（下载v1.0.8版本，主要用到里面的一个python脚本：tcprelay.py）
* https://cgit.sukimashita.com/usbmuxd.git/snapshot/usbmuxd-1.0.8.tar.gz

* 将iPhone的22端口（SSH端口）映射到Mac本地的10010端口
* cd ~/Documents/usbmuxd-1.0.8/python-client
* python tcprelay.py -t 22:10010
* 加上-t参数是为了能够同时支持多个SSH连接
* 注意：要想保持端口映射状态，不能终止此命令行（如果要执行其他终端命令行，请新开一个终端界面）
* 不一定非要10010端口，只要不是保留端口就行

#### usbmuxd的使用2
* 端口映射完毕后，以后如果想跟iPhone的22端口通信，直接跟Mac本地的10010端口通信就可以了
* 新开一个终端界面，SSH登录到Mac本地的10010端口（以下方式2选1）
* ssh root@localhost -p 10010
* ssh root@127.0.0.1 -p 10010
* localhost是一个域名，指向的IP地址是127.0.0.1，本机虚拟网卡的IP地址
* usbmuxd会将Mac本地10010端口的TCP协议数据，通过USB连接转发到iPhone的22端口

* 远程拷贝文件也可以直接跟Mac本地的10010端口通信
* scp -P 10010 ~/Desktop/1.txt root@localhost:~/test
* 将Mac上的~/Desktop/1.txt文件，拷贝到iPhone上的~/test路径
* 注意：scp的端口号参数是大写的-P






------------------------

### 使用OpenSSH远程登录
* 在iPhone上通过Cydia安装OpenSSH工具（软件源http://apt.saurik.com）
* OpenSSH的具体使用步骤可以查看Description中的描述

### 使用OpenSSH远程登录 - 使用步骤
* SSH是通过TCP协议通信，所以要确保Mac和iPhone在同一局域网下，比如连接着同一个WiFi
* 在Mac的终端输入ssh 账户名@服务器主机地址
* 比如ssh root@10.1.1.168（这里的服务器是手机）
* 初始密码alpine
* 登录成功后就可以使用终端命令行操作iPhone
* 退出登录命令是exit



### 了解登录后的账户root、mobile
* iOS下有2个常用账户：root、mobile
* root：最高权限账户，$HOME是/var/root
* mobile：普通权限账户，只能操作一些普通文件，不能操作系统级别的文件，$HOME是/var/mobile
* 登录mobile用户：root mobile@服务器主机地址
* root和mobile用户的初始登录密码都是alpine
* 最好修改一下root和mobile用户的登录密码（登录root账户后，分别通过passwd、passwd mobile完成）


### sh脚本文件
* 我们可以将经常执行的一系列终端命令行放到sh脚本文件中（shell），然后执行脚本文件
* 可以通过sh、bash、source命令来执行sh脚本文件
* sh、bash
* 当前shell环境会启动一个子进程来执行脚本文件，执行后返回到父进程的shell环境
* 执行cd时，在子进程中会进入到cd的目录，但是在父进程中环境并没有改变，也就是说目录没有改变

* source
* 在当前的shell环境下执行脚本文件
* 执行cd后会跳转到cd的目录
* source可以用一个点”.”来替代，比如”. test.sh”



### iOS终端的中文乱码问题
* 默认情况下，iOS终端不支持中文输入和显示
* 解决方案：新建一个~/.inputrc文件，文件内容是

* 不将中文字符转化为转义序列
* set convert-meta off 

* 允许向终端输出中文
* set output-meta on

* 允许向终端输入中文
* set meta-flag on 
* set input-meta on

* 如果是想在终端编辑文件内容，可以通过Cydia安装一个vim（软件源http://apt.saurik.com）


##  connect to host 192.168.0.109 port 22: Connection refused
手机上要安装必备的软件，才能被ssh
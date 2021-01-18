### 步骤1：在设备上安装frida，Mac上安装frida的命令：

```objectivec
sudo pip3 install frida

//Mac上安装frida的命令：
sudo pip3 install frida
//或者 
sudo pip3 install frida –upgrade –ignore-installed six
```

### 步骤2：安装github项目说的必要文件requriment

- [https://github.com/AloneMonkey/frida-ios-dump](https://github.com/AloneMonkey/frida-ios-dump)

```objectivec
sudo pip install -r requirements.txt --upgrade
```

### 步骤3：iPhone上安装frida的方法：

- 打开Cydia->软件源->编辑->添加，输入build.frida.re，添加软件源后，搜索安装Frida即可
- 我在iphone上手动打开frida-server，说“可执行文件中的CPU类型错误”。然后我安装了“ frida for A12之前的设备”，它可以工作。

### 步骤4：然后将越狱设备通过USB连上电脑，进行端口映射

- 默认是将Mac的2222端口映射到手机的22端口，命令如下：（注意，这里的映射的端口必须与frida-ios-dump中的dump.py文件指定的端口一致，只要是未被占用的端口就可以，也可以用以前说过的10010端口，这样用sh usb.sh命令就可以代替iproxy 2222 22了）

### 步骤5：运行

```objectivec
python3 ./dump.py Display name或Bundle identifier

// 例如美团
python3 ./dump.py com.meituan.imeituan
```

### 步骤6：到mac的对应操作指令的文件夹先看结果
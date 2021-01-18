- 默认情况下，由于SSH走的是TCP协议，Mac是通过网络连接的方式SSH登录到iPhone，要求iPhone连接WiFi
- 为了加快传输速度，也可以通过USB连接的方式进行SSH登录
Mac上有个服务程序usbmuxd（它会开机自动启动），可以将Mac的数据通过USB传输到iPhone

```objectivec
/System/Library/PrivateFrameworks/MobileDevice.framework/Resources/usbmuxd
```

- Mac上有个服务程序usbmuxd（它会开机自动启动），可以将Mac的数据通过USB传输到iPhone
- 注意：要想保持端口映射状态，不能终止此命令行（如果要执行其他终端命令行，请新开一个终端界面）不一定非要10010端口，只要不是保留端口就行
- 理解：就是客户端mac先登录电脑的10010端口（可以是其他的端口），然后通过usbmuxc的方式转发数据到服务器端的22端口进行数据传输
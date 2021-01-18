SSH协议一共2个版本
SSH-1
SSH-2

现在用的比较多的是SSH-2，客户端和服务端版本要保持一致才能通信

查看SSH版本（查看配置文件的Protocol字段）

客户端：/etc/ssh/ssh_config
服务端：/etc/ssh/sshd_config
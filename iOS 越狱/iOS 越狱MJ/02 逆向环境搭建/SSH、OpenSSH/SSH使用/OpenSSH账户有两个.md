iOS下有2个常用账户：root、mobile

root：最高权限账户，$HOME是/var/root

mobile：普通权限账户，只能操作一些普通文件，不能操作系统级别的文件，

$HOME是/var/mobile

登录mobile用户：root mobile@服务器主机地址

root和mobile用户的初始登录密码都是alpine

最好修改一下root和mobile用户的登录密码（登录root账户后，分别通过passwd、passwd mobile完成）
如果是想在终端编辑文件内容，可以通过Cydia安装一个vim（软件源http://apt.saurik.com）

默认情况下，iOS终端不支持中文输入和显示

解决方案：新建一个~/.inputrc文件，文件内容是
不将中文字符转化为转义序列
set convert-meta off

允许向终端输出中文
set output-meta on

允许向终端输入中文
set meta-flag on
set input-meta on
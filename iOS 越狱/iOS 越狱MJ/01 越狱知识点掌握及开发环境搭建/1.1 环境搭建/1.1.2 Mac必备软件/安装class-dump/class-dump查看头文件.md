# class-dump查看头文件

* 顾名思义，它的作用就是把Mach-O文件的class信息给dump出来（把类信息给导出来），生成对应的.h头文件
* 官方地址：http://stevenygard.com/projects/class-dump/
* 下载完工具包后将class-dump文件复制到Mac的/usr/local/bin目录，这样在终端就能识别class-dump命令了

* 常用格式
    * class-dump  -H  Mach-O文件路径  -o  头文件存放目录
    * -H表示要生成头文件
    * -o用于制定头文件的存放目录


---

* class-dump获取mach-o的头文件
    * 前提是ipa已经脱壳
    * 直接从pp助手上下载的是脱壳的
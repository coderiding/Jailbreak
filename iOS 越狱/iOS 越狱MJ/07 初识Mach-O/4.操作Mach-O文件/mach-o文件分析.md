- mach-o文件包括了header、load command、data
- mach-o中有多个segment，每个segment有多个section
- 要分析一下header的结构体的字段有哪些？
- 要分析一下load_command的结构体的字段有哪些？
- 要分析一下segemnt_command的结构体的字段有哪些？
- 要分析一下section_64的结构体的字段有哪些？
- -------------mx：mach-o应用01-获取未使用的类文件

拿到app的mach-o，可以分析里面的两个section，
一个是Section64(_DATA,_objc_classlist),表示项目中全部类列表
一个是Section64(_DATA,_objc_classrefs),表示项目中被引用的类列表

- 取上面两个Section64两者之差，就能删除一些项目中没使用的类文件
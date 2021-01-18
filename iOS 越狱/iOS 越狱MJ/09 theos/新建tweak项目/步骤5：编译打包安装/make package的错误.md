```objectivec
$ make package
Can't locate IO/Compress/Lzma.pm in @INC (you may need to install the
IO::Compress::Lzma module) (@INC contains: /Library/Perl/5.18/darwinthread-multi-2level /Library/Perl/5.18 /Network/Library/Perl/5.18/darwinthread-multi-2level /Network/Library/Perl/5.18 /Library/Perl/Updates/5.18.2
/System/Library/Perl/5.18/darwin-thread-multi-2level
/System/Library/Perl/5.18 /System/Library/Perl/Extras/5.18/darwin-threadmulti-2level /System/Library/Perl/Extras/5.18 .) at
/Users/mj/theos/bin/dm.pl line 12.
BEGIN failed--compilation aborted at /Users/mj/theos/bin/dm.pl line 12.
make: *** [internal-package] Error 2
```

- 是因为打包压缩方式有问题，改成gzip压缩就行
- 修改dm.pl文件，用#号注释掉下面两句

```objectivec
$ vim $THEOS/vendor/dm.pl/dm.pl
#use IO::Compress::Lzma;
#use IO::Compress::Xz;
```

- 修改deb.mk文件第6行的压缩方式为gzip

```objectivec
$ vim $THEOS/makefiles/package/deb.mk
_THEOS_PLATFORM_DPKG_DEB_COMPRESSION ?= gzip
```
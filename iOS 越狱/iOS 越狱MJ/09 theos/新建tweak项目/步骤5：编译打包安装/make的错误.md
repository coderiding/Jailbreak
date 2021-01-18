### 问题1：

```objectivec
$ make
Error: You do not have an SDK in
/Library/Developer/CommandLineTools/Platforms/iPhoneOS.platform/Developer/S
DKs
```

- 是因为多个xcode导致路径（有可能安装了号几个xcode），需要指定一下xcode

```objectivec
$ sudo xcode-select --switch
/Applications/Xcode.app/Contents/Developer/
```

### 问题2：

```objectivec
$ make
> Making all for tweak xxx…
make[2]: Nothing to be done for `internal-library-compile'.
```

- 是因为之前已经编译过，有缓存导致的，clean一下即可

```objectivec
$ make clean
$ make
```
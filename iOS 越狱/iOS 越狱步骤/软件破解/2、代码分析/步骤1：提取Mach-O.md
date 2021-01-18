### 1、获取bundle id

```swift
python3 ./dump.py -l
```

2、脱壳,得到解密后的ipa

```swift
python3 ./dump.py xxbundleid
```

3、获取Mach-O

1、修改ipa后缀为zip

2、解压zip

3、右键查看包内容

4、找到Mach-O文件
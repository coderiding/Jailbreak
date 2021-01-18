- 下载theos之前配置成全局使用

### 步骤1：

```swift
vim ~/.bash_profile
```

### 步骤2：

- 在.bash_profie文件后面加入以下两行，配置PATH参数

```objectivec
export THEOS=~/theos
export PATH=$THEOS/bin:$PATH
//最后的$PATH代表其他的路径
```

### 步骤3：

- 让bash_profile文件生效

```objectivec
source ~/.bash_profile
```
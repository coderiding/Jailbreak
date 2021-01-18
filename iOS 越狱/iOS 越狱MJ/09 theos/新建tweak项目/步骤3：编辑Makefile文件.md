- 编辑Makefile文件，修改端口和ip

    ```objectivec
    export THEOS_DEVICE_IP=127.0.0.1
    export THEOS_DEVICE_PORT=10010
    include $(THEOS)/makefiles/common.mk
    TWEAK_NAME = ting_tweak
    ting_tweak_FILES = Tweak.xm
    include $(THEOS_MAKE_PATH)/tweak.mk
    after-install::
        install.exec "killall -9 SpringBoard"
    ```

- 通过那个IP和端口访问手机
    - THEOS_DEVICE_IP
    - THEOS_DEVICE_PORT

### 如果全局配置端口和IP

```objectivec
$ vim ~/.bash_profile
export THEOS=~/theos
export PATH=$THEOS/bin:$PATH
export THEOS_DEVICE_IP=127.0.0.1
export THEOS_DEVICE_PORT=10010
$ source ~/.bash_profile
```

- 如果不希望每个项目的Makefile都编写IP和端口环境变量，也可以添加到用户配置文件中
- 编辑完毕后，$source ~/.bash_profile让配置生效（或者重启终端）
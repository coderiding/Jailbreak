- Reveal是一款调试iOS程序UI界面的神器
- 官网：[https://revealapp.com](https://revealapp.com/)
- 下载：[https://revealapp.com/download/](https://revealapp.com/download/)(建议下载至少Reveal4版本，支持USB连接调试，速度快。低版本的只能WiFi连接调试)
- 找到Mac的Reveal中的RevealServer文件，覆盖iPhone的/Library/RHRevealLoader/RevealServer文件
- 重启SpringBoard或者重启手机，可以在iPhone上输入终端命令
- 重启SpringBoard：

    ```objectivec
    killall -9 SpringBoard
    ```

- 重启手机：reboot 
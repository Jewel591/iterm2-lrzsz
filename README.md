# 解决 macOS 上 iterm2 使用 rz/sz 卡死的问题
# 安装 lrzsz
首先需要我们安装一下 lrzsz，使用命令进行安装：
`brew install lrzsz`

# 配置 iTerm2
安装完成后我们需要在 iTerm2 中使用的话，还需要一些配置

进入到 /usr/local/bin 目录下，下载两个脚本文件
```
cd /usr/local/bin 
sudo wget https://gist.githubusercontent.com/sy-records/1b3010b566af42f57fa6fa38138dd22a/raw/2bfe590665d3b0e6c8223623922474361058920c/iterm2-send-zmodem.sh 
sudo wget https://gist.githubusercontent.com/sy-records/40f4ba22e3fbdeedf58463b067798962/raw/b32d2f7ac3fa54acca81be3664797cebb724690f/iterm2-recv-zmodem.sh
sudo chmod 777 /usr/local/bin/iterm2-* 
```
下载好之后我们进行 iTerm2 的配置

点击 iTerm2 的设置界面 Perference -> Profiles -> Default -> Advanced -> Triggers 的 Edit 按钮

![iterm2](https://i.loli.net/2020/01/07/WBPzoJ49q6bV58F.png)

点击 + 号，添加如下的参数
```
Regular expression: rz waiting to receive.\*\*B0100
            Action: Run Silent Coprocess
        Parameters: /usr/local/bin/iterm2-send-zmodem.sh
           Instant: checked

Regular expression: \*\*B00000000000000
            Action: Run Silent Coprocess
        Parameters: /usr/local/bin/iterm2-recv-zmodem.sh
           Instant: checked
```
添加完成如下图所示

![iterm2](https://i.loli.net/2020/01/07/WBPzoJ49q6bV58F.png)


至此，我们就可以愉快的使用 sz 和 rz 命令了

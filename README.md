mac
===

The mac way

### 玩mac必备 - 安装oh-my-zsh

oh-my-zsh让你的terminal更好看，附带的各种插件（例如git插件）让你的terminal更便捷强悍。
具体的安装办法请猛击 [这里！！！](https://github.com/robbyrussell/oh-my-zsh)

### 玩mac必备 - 安装mac下的包管理器homebrew

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

更多homebrew的信息请猛击 [这里！！！](http://brew.sh/)

### sudo命令无法穿越proxifier代理

```bash
sudo gem install cocoapods
```

在office wifi下开启proxifier代理后无法连接网络

解决办法:

1. 关掉proxifier
2. 切换成staff wifi


### 更新svn

mac osx自带的svn版本一般比较旧，
可以利用brew安装最新的svn，同时在.bash_profile中将新安装的svn路径添加到PATH变量中，覆盖系统自带的svn路径。

```bash
brew doctor
brew install svn
```

brew安装的svn软路径是：

    /usr/local/bin/svn/

用brew list svn命令可以查看实际的安装路径为：

    /usr/local/Cellar/subversion/

而系统自带的svn路径是：

    /usr/bin/svn
  
为了覆盖系统的svn，我们将新svn的路径添加到PATH环境变量中,并放到/usr/bin前面：

打开.bash_profile文件，添加以下行

    export PATH=/usr/local/bin:/usr/local/sbin:$PATH

注：如果你用的oh-my-zsh，需要修改.zshrc文件而不是.bash_profile
    
    export PATH="/usr/local/bin:/usr/local/git/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    
### 更新git

和svn类似，mac osx自带的git也比较旧，用类似的方法可将git更新到最新版本

```bash
brew doctor
brew install git
```

设置环境变量

打开.bash_profile文件，添加以下行

    export PATH=/usr/local/git/bin:$PATH

注：如果你用的oh-my-zsh，需要修改.zshrc文件而不是.bash_profile
    
    export PATH="/usr/local/bin:/usr/local/git/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    
    
### 更新node（不推荐）

系统自带的node和brew安装的node在同一个位置，直接brew install node安装完会报很多的错误，所以不建议更新系统自带的node!!

我做的操作如下


```bash

brew doctor

#delete all the old staff
sudo rm -rf /usr/local/lib/node_modules
sudo rm -rf /usr/local/include/node
sudo rm -rf /usr/local/lib/dtrace/node.d
sudo rm /usr/local/share/man/man1/node.1

#clear all broken symlinks
brew prune

#install node via brew
brew install node

#if brew link node cause error with permissions

#run： sudo chmod 777 /usr/local/lib/dtrace/node.d

```

如果还不行，请运行：

```bash
sudo brew postinstall node
```

### 截屏

首先是截取整个屏幕：

      快捷键：Command+shift+3,这样就截图了整个屏幕，然后截屏的图片保存在桌面上，默认是png格式的。

 

截图某个特定的活动窗口：

      操作方式：按下快捷键：Command+shift+4+空格

 

随意截图：

      操作方式：按下快捷键：Command+shift+4，然后通过鼠标来选取要截图的区域，松下鼠标按键即可完成截图，截图同样保存在桌面，默认png格式。
      
如果想截屏到剪贴板，请在上面的快捷键中多加一个control键！

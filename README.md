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

brew安装的svn路径是：

    /usr/local/opt/subversion/
  
而系统自带的svn路径是：

    /usr/bin/svn
  
为了覆盖系统的svn，我们将新svn的路径添加到PATH环境变量中：

    export PATH=/opt/local/bin:/opt/local/sbin:$PATH


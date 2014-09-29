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
    
    
### 更新node

系统自带的node和brew安装的node在同一个位置，直接brew install node安装完会报错，我做的操作如下


```bash
brew doctor
npm uninstall npm -g

brew uninstall node

brew install node

sudo rm -rf /usr/local/lib/dtrace/node.d

brew link node (caused error with permissions)

sudo chmod 777 /usr/local/lib/dtrace/node.d

brew link node
```



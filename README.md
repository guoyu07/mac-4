mac
===

The mac way

<h2 style="color:red">此文档不再更新维护</h2>

注意：此文档不再更新维护，新老用户请订阅[凹凸实验室](http://aotu.io)的[MAC全栈开发环境搭建指南](http://aotu.io/mac)

### Finder（地址栏问题，及其他实用功能）

解决地址栏复制及输入，可安装FinderPath插件(http://www.macupdate.com/app/mac/33870/finderpath)。
还有一些其他实用功能，可安装XtraFinder插件(http://www.trankynam.com/xtrafinder/)。

### oh-my-zsh

oh-my-zsh让你的terminal更好看，附带的各种插件（例如git插件）让你的terminal更便捷强悍。

具体的安装办法请猛击 [这里！！！](https://github.com/robbyrussell/oh-my-zsh)

10.11.1安装后可能会发生不生效的现象，请参考[这里！！](https://medium.com/@mark_design/install-zsh-and-oh-my-zsh-on-osx-10-11-el-capitan-cfaa0ebb97dc#.jmiak9qgg)进行安装。

安装完毕后在`Terminal > Preferences > General > Shell Open With`的地方填写`/usr/local/bin/zsh`

### homebrew(包管理器)

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

更多homebrew的信息请猛击 [这里！！！](http://brew.sh/)

### 更新zsh

```
# check the zsh info
brew info zsh

# install zsh
brew install --disable-etcdir zsh

# add shell path
sudo vim /etc/shells

# add the following line into the very end of the file(/etc/shells)
/usr/local/bin/zsh

# change default shell
chsh -s /usr/local/bin/zsh
```

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

> update 2015/10/31 使用[nvm](https://github.com/creationix/nvm)来管理node版本

> curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash

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

### 如何查看iPhone应用崩溃时的日志

首先用iTunes的同步功能，将手机的各种信息同步至电脑:

![iTunes Sync](https://cdn.rawgit.com/mamboer/mac/master/assets/img/Picture-1.jpg)

然后，崩溃日志可以在这里找到：

        ~/Library/Logs/CrashReporter/MobileDevice/<DEVICE_NAME>

### Markdown Cheatsheet

学习使用markdown的小抄本：

[Markdown Cheatsheet](http://assemble.io/docs/Cheatsheet-Markdown.html)

### 更新rubygems

```bash
sudo gem update --system
```

### 利用homebrew更新vim

```
brew update
brew doctor
brew install vim
```

如果报以下错误：
        Vim won't build with Python support on OS X 10.9.4

则为10.10系统python的bug，具体可以见这里：[https://github.com/Homebrew/homebrew/issues/32066](https://github.com/Homebrew/homebrew/issues/32066)。暂无解决办法。

安装完成后验证版本：

```bash
vim --version
```

如果发现还是旧的版本，说明新版vim的路径/usr/local/bin在环境变量中不存在，或者在老版本路径/usr/bin的后面。
这个问题可以通过以下两种方法的其中一个来解决：

Option 1: Update your path:
In your .zshrc (you are using Zsh right?) or .bashrc update your path.

```bash
#this
export PATH=/usr/bin:/usr/sbin
#to this
export PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin
```

Option 2: Move your old Vim and symlink the new one
You can move the Vim that comes with OSX and Symlink the one brew installed

```bash
sudo mv /usr/bin/vim /usr/bin/oldvim
ln -s /usr/local/bin/vim /usr/bin/vim
```

我们更新了vim，但是vi还是原来的版本，有时候出于方便我们希望敲打vi命令的时候调用的是vim~
可以通过设置别名来达到该目的：

```bash
# 在.bash_profile(或.zshrc，如果使用zsh的话)文件中添加vi别名
alias vi='vim'
```

[参考文章](http://mikegrouchy.com/blog/2012/05/compile-vim-with-python-support-on-osx-with-homebrew.html)

装完记得装屌屌的[vimrc](https://github.com/amix/vimrc)


### 安装mongodb 并开机启动

[wiki: mongodb安装](https://github.com/mamboer/mac/wiki/mongodb)


### 修改host不生效

```
127.0.0.1 baidu.com
```

改完后，shell里面ping baidu.com 返回ip 127.0.0.1，但是浏览器输入baidu.com依然跳转至baidu。

原因是：

	如果浏览器设置了代理，改host的话要走https,不然还会被reset

让指定域名自动走https协议：

```
chrome://net-internals/#hsts
```
将指定的域名添加进去

参考文档：http://cn.v2ex.com/t/25512

### nginx web服务器的安装

参考：http://mwholt.blogspot.com/2014/10/installing-nginx-on-mac-os-x-yosemite.html

1. 安装

  ```
  brew update
  brew install nginx
  ```

2. 启动

  ```
  sudo nginx
  ```

3. 测试

  默认端口是8080，可以打开http://localhost:8080测试是否安装并运行

  配置文件地址

  	/usr/local/etc/nginx/nginx.conf

4. 修改端口listen

  ```
  sudo nginx -s stop
  sudo vi /usr/local/etc/nginx/nginx.conf
  # 改完后重启
  sudo nginx
  ```

5. 多站点配置

  为了灵活配置nginx的站点，可以参考以下配置：

  A. 在/usr/local/etc/nginx/下面新建两个目录：sites-available和sites-enabled

  B. 在sites-available里面新建default.conf，将nginx.conf里面的默认站点配置的内容拷贝过去，并注释掉原内容

  C. 在nginx.conf里面增加以下内容

    ```
    include /usr/local/etc/nginx/sites-enabled/*;
    ```

  D. 将sites-available目录下的配置建立symlink至site-enabled目录

    ln -sfv /usr/local/etc/nginx/sites-available/default.conf /usr/local/etc/nginx/sites-enabled/default.conf

  E. 重启nginx服务

    ```
    # restart
    sudo nginx -s stop
    sudo nginx
    ````

6. 开机启动

  ``` bash
  # symbolic link
  ln -sfv /usr/local/opt/nginx/*.plist ~/Library/LaunchAgents
  # root permission
  sudo chown root:wheel ~/Library/LaunchAgents/homebrew.mxcl.nginx.plist
  # load
  sudo launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.nginx.plist
  # start
  sudo launchctl start ~/Library/LaunchAgents/homebrew.mxcl.nginx.plist
  # detect whether nginx is running
  ps aux | grep nginx
  ```

7. 修改默认的html站点目录

  默认的目录在这里：

  ```
  /usr/local/Cellar/nginx/1.2.3/html
  ```

  其中1.2.3是版本，根据实际按照情况不同

  跑去nginx.conf文件中修改默认目录：

  ```
  server {
    listen       80;
    server_name  localhost;

    #access_log  logs/host.access.log  main;

    location / {
        root   html;
        index  index.html index.htm;
    }
  ```

  默认目录即上面的root的地方，可以修改成用户目录，例如: /User/lv/www

  ### npm install xxx报 EACCESS,mkdir错误

  ~/.npm目录权限问题，

  ```
  sudo chown -R $USER:$GROUP ~/.npm
  npm cache clean
  ```

  然后重新试试

  ### Terminal crashes "pointer being freed was not allocated"

  原因可能是你改了系统自带的一些路径的权限，例如`/usr/bin/`

  解决办法是利用打开Disk Utility程序修复磁盘权限

### 修改主机名

```
sudo scutil --set HostName MacBookPro
```

### 修改电脑共享名

```
sudo scutil --set ComputerName MacBookPro
```

### nvm加速

为了使用淘宝的[nvm镜像](https://github.com/cnpm/cnpm)，我们可以安装`cnpm`代替`npm`命令。

```
npm install cnpm -g --registry=https://registry.npm.taobao.org
```

### 设置默认的编辑器

很多应用调用默认编辑器时会使用`$EDITOR`这个环境变量，因此我们可以设置该变量为我们喜欢的编辑器。

例如设置默认编辑为atom：

```
export EDITOR=atom
```

或者，右单击某种扩展名的文件来改变其默认打开程序：

> "Get Info" -> "Open with:" -> (Select Atom) -> "Change All"

# Mac安装homebrew(简称brew)



###### brew 是MacOS上的包管理工具，可以简化 macOS 和 Linux 操作系统上软件的安装。

1、启动mac终端（command + 空格弹出搜索框 检索 终端），并执行如下命令

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

 2、输入本机用户密码，自动安装

3、根据提示，输入镜像序号（选中科大镜像则输入的是1）

4、等待安装完毕即可，然后终端输入命令 brew --version查看版本



### brew常用命令

```
$ brew --help #简洁命令帮助
$ man brew #完整命令帮助
$ brew install git #安装软件包(这里是示例安装的Git版本控制)
$ brew uninstall git #卸载软件包
$ brew search git #搜索软件包
$ brew list #显示已经安装的所有软件包
$ brew update #同步远程最新更新情况，对本机已经安装并有更新的软件用*标明
$ brew outdated #查看已安装的哪些软件包需要更新
$ brew upgrade git #更新单个软件包
$ brew info git #查看软件包信息
$ brew home git #访问软件包官方站
$ brew cleanup #清理所有已安装软件包的历史老版本
$ brew cleanup git #清理单个已安装软件包的历史版本
```



### 程序安装路径及文件夹



````
-bin #用于存放所安装程序的启动链接（相当于快捷方式）
-Cellar #所有brew安装的程序，都将以[程序名/版本号]存放于本目录下
-etc #brew安装程序的配置文件默认存放路径
-Library #Homebrew 系统自身文件夹
+–Formula #程序的下载路径和编译参数及安装路径等配置文件存放地
+–Homebrew #brew程序自身命令集
````

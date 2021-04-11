## Mac安装Jdk1.8步骤

1、官网下载Jdk[Oracle官网下载Jdk1.8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html) 一步步继续默认安装

>不想注册可以乘纸飞机 百度网盘https://pan.baidu.com/share/init?surl=CVuWES-F1PoaV63oL3nCHQ  提取码 c62d

2、通过访达Finder进入默认安装目录，**资源库即Library，看不到资源库就设置打开隐藏文件夹**

```
/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home
```

3、打开终端窗口，如果你是第一次配置环境变量，可以使用**vim .bash_profile**创建一个**.bash_profile**的隐藏配置文件(如果你是为编辑已存在的配置文件，则使用**open -e .bash_profile**命令)

4、输入以下配置，注意JAVA_HOME的**jdk版本号**，本人用的是**jdk1.8.0_211.jdk**

```
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home
PATH=$JAVA_HOME/bin:$PATH:.
CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
export JAVA_HOME
export PATH
export CLASSPATH
```

5、使用Linux命令，**:wq**保存退出

```
q：表示退出
wq：表示保存退出
q!：表示强制退出，不对文件进行保存
wq!：强制性写入文件并退出。即使文件没有被修改也强制写入，并更新文件的修改时间
```

6、输入命令**source .bash_profile**使配置生效

7、输入命令**echo $JAVA_HOME**查看刚才配置的路径

8、输入命令**java -version**查看版本号

9、输入命令**java**，打印出来信息成功


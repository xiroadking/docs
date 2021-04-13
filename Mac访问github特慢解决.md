## 你是否为访问github太慢而烦恼？别着急，请耐心看完本文。

github被墙，据我所知只是DNS污染，IP并没有封杀。所以可以**修改hosts**文件即可访问github。速度特快！

### 修改道路千万条 ，天才第一步可不是雀氏纸尿裤啊！

### 第一步你得先进入/etc目录下找到hosts文件呀！

```
a、你可以在 访达Finder 用Mac快捷键 command + shift + g 输入 /etc/hosts 前往文件夹 找到hosts文件
b、也可以通过 终端命令 进入 /etc/hosts
c、如果我描述的你还是听不懂，那好吧。给你个纸飞机直达图解版，我这里就不再花费时间啦：	   	  
   https://blog.csdn.net/weixin_51245542/article/details/109528350
```

### 第二步把最新（2021年）域名IP配置复制到你刚才打开的hosts文件

```
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1	localhost
255.255.255.255	broadcasthost
::1              localhost

# GitHub Start 

151.101.1.194	github.global.ssl.fastly.net
185.199.110.153	assets-cdn.github.com
185.199.108.153	documentcloud.github.com
140.82.113.3	gist.github.com
185.199.111.133	gist.githubusercontent.com
185.199.109.154	github.githubassets.com
185.199.110.154	help.github.com
140.82.113.10	nodeload.github.com
185.199.111.133	raw.github.com
140.82.112.18	status.github.com
185.199.108.153	training.github.com
185.199.111.133	avatars.githubusercontent.com
185.199.110.133	avatars0.githubusercontent.com
185.199.110.133	avatars1.githubusercontent.com
185.199.110.133	avatars2.githubusercontent.com
185.199.111.133	avatars3.githubusercontent.com
185.199.110.133	avatars4.githubusercontent.com
185.199.108.133	avatars5.githubusercontent.com
185.199.109.133	avatars6.githubusercontent.com
185.199.111.133	avatars7.githubusercontent.com
185.199.109.133	avatars8.githubusercontent.com
185.199.108.133	favicons.githubusercontent.com
140.82.113.10	codeload.github.com
52.217.44.204	github-cloud.s3.amazonaws.com
52.216.132.43	github-com.s3.amazonaws.com
52.216.94.155	github-production-release-asset-2e65be.s3.amazonaws.com
52.217.39.148	github-production-user-asset-6210df.s3.amazonaws.com
52.217.201.249	github-production-repository-file-5c1aeb.s3.amazonaws.com
185.199.110.153	githubstatus.com
64.71.168.201	github.community
185.199.108.133	media.githubusercontent.com
185.199.108.133	camo.githubusercontent.com
185.199.109.133	raw.githubusercontent.com
185.199.108.133	cloud.githubusercontent.com
185.199.109.133	user-images.githubusercontent.com
185.199.110.153	customer-stories-feed.github.com
185.199.110.153	pages.github.com
140.82.113.6	api.github.com
140.82.113.26	live.github.com
140.82.113.30	githubapp.com
140.82.114.3	github.com

# GitHub End
```

### 第三步要刷新hosts让其生效（以下2选1，命令刷新了就不用重启电脑）

1、在当前hosts文件目录下**右键空白处找到服务**点击终端标签或者终端窗口，输入以下命令

```
sudo killall -HUP mDNSResponder
```

2、重启电脑让hosts生效

### 最后，发现访问github超级快有没有！



### 最最最最后，再贡献一个查IP的网址:smirk:

```
https://www.ipaddress.com/
```



### 希望本文对你有所帮助，我今天的目标还没完成 ! :sob::sob:

### 整理不易，希望一键三连一起努力、加油！！:stuck_out_tongue::stuck_out_tongue:


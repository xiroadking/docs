## 常用词含义    

```
watch：会持续收到项目的动态   
fork：复制某个项目到自己的仓库
star：可以理解为点赞
clone：将项目下载到本地
follow：关注你感兴趣的作者，会收到他们的动态
```

## 1、in查询：

```
Springboot in: name　　查找项目名称中包含Springboot
SringBoot in: description　　查找项目描述中包含SringBoot
SringBoot in: readme　　查找readme中包含SringBoot
SpringBoot in: name,description,readme　　查找项目名称、描述、readme中包含Springboot
```

## 2、:>或:<

格式 xxx关键词 stars/forks 通配符 

```
Springboot stars :> 5000　　查找点赞数超过5000的项目
Springboot forks :> 5000　　查找forks数大于5000的项目
```

## 3、数字1..数字2

区间范围数字查询

```
SpringCloud stars:200..9999 forks:100..2000　　查找stars在200~9999，forks在100~2000的项目
```

## 4、awesome加强搜索

awesome一般是用来收集学习、工具、书籍类相关的项目 

```
awesome redis　　搜索优秀的redis相关项目，包括框架、教程等
```

## 5、高亮显示某一行代码

- 高亮显示1行：地址后紧跟#L行数
- 高亮显示多行：地址后紧跟#L行数-L行数

```
https://github.com/stunstunstun/.../spring/SpringBootJdbcExampleApplication.java#L13　　高亮显示13行
https://github.com/stunstunstun/.../spring/SpringBootJdbcExampleApplication.java#L13-L53　　高亮显示标注13行到53行代码
```

## 6、项目内搜索

使用按键 t

可以看到目录结构有变化，都变为平铺显示，不用翻目录就可以直接查看

## 7.搜索某地区牛人

```
location:guangzhou language:java
```


# 模块解析

可参考网页：[http://wiki.jikexueyuan.com/project/python-crawler-guide/the-use-of-urllib-library.html](http://wiki.jikexueyuan.com/project/python-crawler-guide/the-use-of-urllib-library.html)

#### 一、URL管理器：管理已抓取的网页和未抓取的网页

作用：重复抓取浪费资源

实现方式：区分两个集合

* 存放在内存中：python的set可以去除集合中重复的元素（个人）
* 存放在关系数据库中MySQL，一个表存储带爬取和已爬取的两个数据集合（个人）
* 存储在缓存数据库中：redis（企业）

#### 二、网页下载器：将需求网页下载到本地-核心组件

以html的形式下载到本地，形成本地字符串

python有哪几种网页下载器：urllib2（官方提供、性能以不错）、requests\(第三方很强大\)

实现方式三种：

```
#!/usr/bin/python
#-*-coding:utf-8 -*-
import cookielib
import urllib2

url = "https://www.baidu.com/"  
print 'the simplest way'
response1 = urllib2.urlopen("https://www.baidu.com/")
print response1.getcode()       #获取状态码
print len(response1.read())     #返回网页内容的长度

######################################
print'the second way'
request = urllib2.Request(url)
request.add_header('user-agent', 'Mozilla/5.0')       #把爬虫伪装成浏览器
resopnse2 = urllib2.urlopen(request)
print(resopnse2.getcode())
print(len(resopnse2.read()))

#############################
print('the third way')
cj = cookielib.CookieJar()    #添加登录密码，创建cook容器
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
urllib2.install_opener(opener)
response3 = urllib2.urlopen(url)
print response3.getcode()
print cj     #打印cook的内容
print len(response3.read())

```




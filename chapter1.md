# 模块解析

可参考网页：http://wiki.jikexueyuan.com/project/python-crawler-guide/the-use-of-urllib-library.html

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

* 最简单：urllib2.urlopen\(url\)






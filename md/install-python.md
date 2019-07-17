# python 安装与配置（windows 10）

有两种安装方式：
1. 从官网下载，然后再安装需要的模块。
2. 直接从Anaconda下载一个全家桶，一次性完成所有的安装。

推荐第二种方式。

## python 下载与安装

在Anaconda官网[https://www.anaconda.com/distribution/](https://www.anaconda.com/distribution/)下载对应版本的Python:

![](/md/static/2019-07-17-18-49-57.png)

由于历史原因，python分为`python2`和`python3`。一般来说，选择`python3`。

在windows 10平台下，下载之后，双击即可进行安装。按照指引一步一步即可完成安装。类似下面的流程：

![](/md/static/2019-07-17-18-52-11.png)
![](/md/static/2019-07-17-18-52-51.png)
![](/md/static/2019-07-17-18-53-12.png)
![](/md/static/2019-07-17-18-53-41.png)
![](/md/static/2019-07-17-18-54-35.png)
![](/md/static/2019-07-17-18-55-34.png)
![](/md/static/2019-07-17-18-55-58.png)
![](/md/static/2019-07-17-18-56-24.png)
![](/md/static/2019-07-17-18-56-49.png)

## 启动jupyter notebook

python的使用分为两种：
1. 先把脚本编写完成，然后一次性执行该脚本。
2. 在python的交互式环境中，一边写，一边执行。

日常使用，主要采用第二种方式，在交互式的环境中编写。交互式的环境，推荐`jupyter notebook`。

Anaconda python安装完成之后，在`cmd`中或者`powershell`中输入：`jupyter notebook`即可打开。

输入命令：
![](/md/static/2019-07-17-19-01-33.png)

命令会自动在浏览器中打开页面`http://localhost:8888/tree`：
![](/md/static/2019-07-17-19-04-05.png)

新建一个文件，会在新的页面打开：

![](/md/static/2019-07-17-19-04-29.png)

在这里面，可以编写脚本。

![](/md/static/2019-07-17-19-05-13.png)

编写完成之后，再保存。可以在`http://localhost:8888/tree`中看到：

![](/md/static/2019-07-17-19-05-58.png)
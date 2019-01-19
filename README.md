# Github Pages 内容发布系统

## 背景

github pages可以免费托管静态文件。

若要将内容发布到github pages，需要先把内容转化成html。

官方上看到的解决办法是使用类似Jekyll这样的静态站点生成器来生成。在Jekyll的帮助文档中，看到需要安装各种依赖，进行各种配置。想来想去，还是太过麻烦。

毕竟，写博客的频率不是那么高，不想在计算机上安装那么多不怎么用的软件，不想记住那么多偶尔用到的配置。

所以，就打算DIY一个简单版本的内容发布系统。


## 需求

为了能够安心地写内容，需要有一个独立的工作目录。

当需要写的时候，在这个目录中建立一个`markdown`文件，在里面将内容写好。

当想要发布内容的时候，在一个`目录文件`中，将发布信息配置好。之后，在页面上，就能够看到内容。

也就是说，**若要发布新得内容，只需要两步**：

1. 新建文件，写
2. 在目录文件中添加文件信息


## 设计

### 存在的问题

github pages只能托管静态文件。这个限制，要求所有的功能在前端页面中实现。

主要的问题有：

- 数据传输
- markdown解析
- 目录显示


### 解决的办法

#### 数据传输

可以通过`ajax`实现，在这里，采用`axios.js`库。

#### markdown解析

前端解析`markdown`，当前有很多成熟的库，这里采用`markdown-it.js`

#### 目录显示

正常情况下，目录是要动态生成的。在`github pages`，暂时没有找到动态生成的方法。

这里的解决办法是，建立一个`toc.json`文件，人工添加，其中包含目录信息。

`toc.json`的格式为：

```json
[
    {
        "title": "github pages 内容发布系统",
        "created_at": "2019/01/19",
        "url": "/md/20190119-github-pages-博客系统.md"
    }
]
```

## 实现

通过两个页面`md.html`和`index.html`来实现所有的功能。

### md.html

该页面的功能是：解析`markdown`并显示。

![](/md/static/2019-01-19-11-12-53.png)

#### 过程

1. 确定要显示哪个文件

    通过`URL`中的参数来确定，代码如下：

    url为：
    
    `https://www.chengbw.cn/md.html?src=README.md`

    解析：

    ```js
    let url = new URL(window.location.href);
    let src = url.searchParams.get("src")
    ```

1. 获取数据

    通过`axios`，详见[代码](https://github.com/chengbw/chengbw.github.io/blob/master/md.html)

1. 解析数据

    通过`markdown-it`，详见[代码](https://github.com/chengbw/chengbw.github.io/blob/master/md.html)

1. 确定markdown样式

    解析后的markdown，是html。其样式，即可以找到一些外部的css，也可以自定义。

    在这里，采用自定义的css文件`md.css`


### index.html

该页面的功能是：显示目录。

![](/md/static/2019-01-19-11-12-13.png)

#### 过程

1. 获取数据

    通过`axios`，详见[代码](https://github.com/chengbw/chengbw.github.io/blob/master/index.html)

2. 显示目录

    首先，按时间倒序排列
    
    然后，按月份分组，其中分组的代码（来源于网络）为：
    ```js
    function groupBy(array, f) {
            let groups = {};
            array.forEach(function (o) {
                let group = JSON.stringify(f(o));
                groups[group] = groups[group] || [];
                groups[group].push(o);
            });
            return Object.keys(groups).map(function (group) {
                return {
                    'group': JSON.parse(group),
                    'toc': groups[group]
                };
            });
        }
    ```

    最后，生成表格，并显示，详见[代码](https://github.com/chengbw/chengbw.github.io/blob/master/index.html)


## 代码

完整代码，放在了[github](https://github.com/chengbw/chengbw.github.io)
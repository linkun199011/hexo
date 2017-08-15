---
title: 如何构建利用github配合hexo构建一个网站
date: 2017-08-15 13:51:44
tags: #github #gitbook #hexo
---

# 安装hexo

```
npm install -g hexo-cli
```

linux上可能会出现错误, 实践过程中碰到文件夹权限的问题, 从hexo的issue中可以参考大家的workaround:

```
root@xxxxxxxxxx:~# npm config set user 0
root@xxxxxxxxxx:~# npm config set unsafe-perm true
root@xxxxxxxxxx:~# npm install -g hexo
```

更多的hexo使用技巧请参考:

https://hexo.io/zh-cn/docs/setup.html 建站指南


# 利用hexo建站


安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。

```
$ hexo init <folder>
$ cd <folder>
$ npm install
```

新建完成后，指定文件夹的目录如下：

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

### _config.yml  

网站的 配置 信息，您可以在此配置大部分的参数。

### package.json

应用程序的信息。EJS, Stylus 和 Markdown renderer 已默认安装，您可以自由移除。

```
package.json

{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": ""
  },
  "dependencies": {
    "hexo": "^3.0.0",
    "hexo-generator-archive": "^0.1.0",
    "hexo-generator-category": "^0.1.0",
    "hexo-generator-index": "^0.1.0",
    "hexo-generator-tag": "^0.1.0",
    "hexo-renderer-ejs": "^0.1.0",
    "hexo-renderer-stylus": "^0.2.0",
    "hexo-renderer-marked": "^0.2.4",
    "hexo-server": "^0.1.2"
  }
}
```

### scaffolds

模版 文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。

Hexo的模板是指在新建的markdown文件中默认填充的内容。例如，如果您修改scaffold/post.md中的Front-matter内容，那么每次新建一篇文章时都会包含这个修改。


### source

资源文件夹是存放用户资源的地方。除 _posts 文件夹之外，开头命名为 _ (下划线)的文件 / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去。

### themes

主题 文件夹。Hexo 会根据主题来生成静态页面。


# 发布到github

整个hexo文件夹下有两个部分组成:

1. hexo: 整个hexo的网站构建模块, 包括node_modules 以及 其他的配置文件都在该文件夹下.

2. public: 通过hexo新建的文件, 已经最终构造出来的样式被保存在这个文件夹下面.

正常来讲, 如果作为博客, 只需要将public下的所有内容push到github的linkun199011.github.io工程即可, 将该工程设置成gitbook, 就能够达到做成博客的目的.    
但是, 为了让我整个hexo工程可以跨平台跨主机工作, 我还是将整个hexo工程push到了github 的 hexo 工程.    
这样, 利用 `hexo new someFile` 则就会在 `source/_posts/` 文件夹下面创造出对应的文件, 文件修改完毕后, `hexo g`, 然后就在 `public`文件夹下面生产了相应的html.   
这个时候需要在hexo根目录push一下, 然后再到public目录下push一下.

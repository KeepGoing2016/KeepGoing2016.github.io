---
title: Hexo搭建博客小结
date: 2020-09-19 15:59:04
tags:
---

### 遇到的问题
* **node.js版本不对**

由于电脑之前安装过node.js，而hexo安装是最近安装的导致两者版本不兼容，运行命令行报错。

* 环境配置完一直看不到blog
    1.  终端没有运行`hexo clean && hexo deploy` 运行后才会生成gh-pages分支 
    2. GitHub Pages分支要改成gh-pages
    3. .travis.yml文件gh-pages分支也要保存一份
    4. 如果blog设置正常
      ![](/images/Jietu20200919-161920.jpg)



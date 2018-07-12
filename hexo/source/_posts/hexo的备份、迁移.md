---
title: hexo的备份、迁移
date: 2018-07-12 10:10:05
tags:
  - hexo
---
之前做过在另一台电脑中得hexo忘记备份，更换电脑后迁移比较麻烦，官网记录的备份是从hexo备份到其他博客的方案，所以在这里记录一下hexo备份迁移流程。

<!-- more -->
### 具体的操作如下

选择一个目录，克隆gitHub上面生成的静态文件到本地
``` bash
$ git clone https://github.com/yourname/hexo-test.github.io.git
```

删除本地文件夹中的**除了**有关git的所有文件,复制写博客的hexo目录（所有文件）到当前路径，忽略不必要提交的文件
``` bash
$ touch .gitignore
```
在生成”.gitignore” 文件里输入你要忽略的文件夹及其文件就可以了。（注意格式）

创建一个叫hexo的分支
``` bash
$ git checkout -b hexo
```

新增复制过来的文件到暂存区（注意若hexo中有从git上下载的主题，先把主题的git信息清除）
``` bash
$ git add --all
```

提交文件到暂存区
``` bash
$ git commit -m "新建分支源文件"
```
推送分支到github
``` bash
$ git push --set-upstream origin hexo
```
到这里基本上就搞定了，以后再推就可以直接git push了，hexo的操作跟以前一样。

今后无论什么时候想要在其他电脑上面用hexo写博客，就直接把创建的分支克隆下来，npm install安装依赖之后就可以用了。

克隆分支的操作
``` bash
$ git clone -b hexo https://github.com/yourname/hexo-test.github.io.git
```
这样做完了以后，每次写完博客发布之后不要忘了还要git push把源文件推到分支上

参考文章：https://www.jianshu.com/p/4e068f4dd726

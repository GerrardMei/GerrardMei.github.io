---
title: git记住用户名和密码
date: 2018-03-14 11:19:37
tags:
---

方式一：使用SSH，添加ssh key。

方式二：在全局中存储用户的账号密码，方式如下

在%HOME%目录中，一般为C:\users\Administrator，也可以是你自己创建的系统用户名目录，反正都在C:\users***中。创建.git-credentials文件。

Windows中创建以.开头的文件的方法：

1：新建test.txt记事本，然后另存为.git-credentials
2：使用git bash

touch .git-credentials
1
创建完成后，在该文件中输入：

https://username:password@github.com

注：username对应你的用户名，password对应你的密码

然后再进入git bash中

git config --global credential.helper store
1
store为永久存储，当然也可以设置临时的

git config –global credential.helper cache
1
默认为15分钟，如果想设置保存时间的话，可以输入：

git config credential.helper ‘cache –timeout=3600’
1
这样就设置了一个小时的有效时间。

执行完后查看%HOME%目录下的.gitconfig文件，会多了一项：

[credential]helper=store

重新开启git bash会发现git push时不用再输入用户名和密码

方式三：单独对某个项目免密

如果还未添加远程地址，可以输入一下命令：

git remote add origin https://username:password@git.oschina.net/diligentyang/ysy107lab.git 
1
如果已添加远程地址

最为简单的方式就是，直接在.git/config文件中进行修改，按如上格式，添加用户名和密码
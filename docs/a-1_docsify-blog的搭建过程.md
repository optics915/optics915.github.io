> 作者：optics915。
>
> **介绍:** 这是一个随手化的类似笔记的个人博客 作者: **[optics915](https://optics915.gitee.io/docsify-blog)** 。一般会在此记录一些从知乎、B站、GitHub上学来的有意思的操作，每一个过程都先自己操作成功之后再将其记录下来，以方便日后碰到相似类型时有理可依。

新式复现这一板块主要是在学习的过程中，根据别人的分享以及新遇到的问题，通过上网查找资料，综合记录一些此前未曾掌握的技巧以及复现别人的操作，我想对于我这样一个小白，从模仿、复现开始也是一种自我加强学习的过程吧。

## 1 docsify-blog的搭建过程

### 1.1 终端安装相关软件模块？
mac终端安装node，node应该是一种js运行环境，用官方的表述：Node.js就是运行在服务端的 JavaScript，我们在html文件里面需要使用这种语言来编写代码，以本博客的index.html为例，需要使用js来渲染我们的HTML页面，<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>里面就引用了.js文件。

#### 1.1.1 命令行安装node
`brew install node`
```
root:~ ZouYue$ brew install node 
Warning: node 14.3.0 is already installed and up-to-date
To reinstall 14.3.0, run `brew reinstall node`
```
我已经安装过了，所以会显示`Warning: node 14.3.0 is already installed and up-to-date`，按Guide哥以及自己的操作经验来看大概2、3分钟左右，如果你显示`command not found`，可能是你没有安装`brew`，可以参考一下下面一篇我以前安装的记录过程，`2 mac终端安装brew`。

#### 1.1.2 检测是否安装成功（可选）
`node -v`
```
root:~ ZouYue$ node -v
v14.3.0
```
#### 1.1.3 用npm工具管理包安装客户端工具
`npm i docsify-cli -g`
这条命令的作用，按官方的解释是“有利于本地初始化和预览网站”，根据我测试后的理解应该是方便下一行代码`docsify init /.h`生效以及在vscode中修改代码并保持后，能够在网页端不用刷新就立刻更新页面内容。

#### 1.1.4 创建一个本地文件夹
```
mkdir docsify-blog
cd docsify-blog
```

#### 1.1.5 初始化
```
root:docsify-blog ZouYue$ docsify init ./

Initialization succeeded! Please run docsify serve ./

root:docsify-blog ZouYue$ docsify serve ./

Serving /Users/macos/docsify-blog now.
Listening at http://localhost:3000
```
这里只需要输入两行命令`docsify init ./`以及`docsify serve ./`，然后在浏览器中输入`http://localhost:3000`即可。在这儿我遇到了一个严重的问题，就是好几次我用`crl+c`中断运行，再次重复1.1.5操作时，再也打不开网站页面，如图所示：

网页端`crl+c`中断前后对比
![](https://s1.ax1x.com/2020/07/12/U86fZd.png)

`crl+c`中断后vscode页面展示
![](https://s1.ax1x.com/2020/07/12/U86hdA.png)

后来我想既然README和index.html都变成了最初的样子，会不会是因为`docsify init ./`将它们都初始化了，于是重新打开终端，<u>刻意跳过`docsify init ./`，输入两行命令，如下`cd /Users/macos/docsify-blog`和`docsify serve ./`</u>
```
root:~ ZouYue$ cd /Users/macos/docsify-blog 
root:docsify-blog ZouYue$ docsify serve ./

Serving /Users/macos/docsify-blog now.
Listening at http://localhost:3000
```
重复操作多次，果然问题是在`docsify init ./`，希望这里能够引起初学者注意，不然辛苦编辑的内容，就这么没了，还是不划算的。

#### 1.1.6 博客内容填充以及侧边栏、搜索栏
这里详情请参考Guide哥的视频以及他GitHub上所用到的资源，资源使用链接:https://github.com/Snailclimb/docsify-demo
### 1.2 将项目上传至GitHub
#### 1.2.1 终端上传该项目至GitHub
##### 1.2.1.1 在GitHub上新建一个仓库
![](https://s1.ax1x.com/2020/07/13/UYWwSs.png)
##### 1.2.1.2 给项目命名
![](https://s1.ax1x.com/2020/07/13/UYW3OP.png)
##### 1.2.1.3 根据页面终端命令提示，在终端进行项目提交
![](https://s1.ax1x.com/2020/07/13/UYWGef.png)
```
root:~ ZouYue$ cd /Users/macos/docsify-blog 
root:docsify-blog ZouYue$ git init
重新初始化已存在的 Git 仓库于 /Users/macos/docsify-blog/.git/
root:docsify-blog ZouYue$ git add .
root:docsify-blog ZouYue$ git commit -m "second commit"
[master f1c71f1] second commit
 5 files changed, 226 insertions(+), 413 deletions(-)
 rewrite README.md (100%)
 delete mode 100755 "docs/a-1\345\244\207\346\210\230\351\235\242\350\257\225.md"
 create mode 100755 "docs/a-1\346\226\260\345\274\217\345\244\215\347\216\260.md"
 rewrite index.html (94%)
root:docsify-blog ZouYue$ git remote add origin https://github.com/optics915/docsify-blog.git
fatal: 远程 origin 已经存在。
root:docsify-blog ZouYue$ git push -u origin master
Username for 'https://github.com': optics915
Password for 'https://optics915@github.com': 
枚举对象: 12, 完成.
对象计数中: 100% (12/12), 完成.
使用 4 个线程进行压缩
压缩对象中: 100% (7/7), 完成.
写入对象中: 100% (7/7), 5.65 KiB | 5.65 MiB/s, 完成.
总共 7（差异 3），复用 0（差异 0），包复用 0
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To https://github.com/optics915/docsify-blog.git
   5f3dc76..f1c71f1  master -> master
分支 'master' 设置为跟踪来自 'origin' 的远程分支 'master'。
root:docsify-blog ZouYue$ 
```
我这儿有出现验证提示，如图，直接选择拒绝，之后会自动弹出输入GitHub账号和密码，输入即可
![](https://s1.ax1x.com/2020/07/13/UYWJw8.png)
下面我截了一张前后两次上传的对比图，以表示这段代码成功提交
![](https://s1.ax1x.com/2020/07/13/UYWYTS.png)
##### 1.2.1.4 通过在settings里面设置来实现一个外网可以访问的域名
![](https://s1.ax1x.com/2020/07/13/UYWUYQ.png)
##### 1.2.1.5 选择master这个分支
![](https://s1.ax1x.com/2020/07/13/UYWNFg.png)
##### 1.2.1.6 出现这个项目的域名，我们通过这个域名可以在外网进行访问
![](https://s1.ax1x.com/2020/07/13/UYWaWj.png)

下面是一张我在手机端的截图
![](https://s1.ax1x.com/2020/07/13/UYW0ln.png)

至此，在GitHub上部署成功，以后我们就可以通过https://optics915.github.io/docsify-blog 这个域名来访问这样一个博客。

### 1.3 将项目上传至Gitee

Guide哥在视频里建议那些因为GitHub访问比较慢的小伙伴，这里可以访问下面`3 解决服务器在国外访问缓慢问题`，将项目上传至国内的托管平台Gitee，基本操作差不多，在终端上传项目至Gitee，只需要把`git remote add origin https://github.com/optics915/docsify-blog.git`里面的`github`改成`gitee`即可，后面我有在第二次提交时出现问题处有提及，Guide哥在这儿采用了另一种直接通过GitHub导入至Gitee的方法，过程如下：

#### 1.3.1 从GitHub导入仓库
![](https://s1.ax1x.com/2020/07/13/UYWByq.png)

#### 1.3.2 从GitHub中项目主页导入地址
![](https://s1.ax1x.com/2020/07/13/UYWsmV.png)

#### 1.3.3 导入仓库
![](https://s1.ax1x.com/2020/07/13/UYWDO0.png)

#### 1.3.4 从Gitee项目主页的服务里选择Gitee Pages
![](https://s1.ax1x.com/2020/07/13/UYWywT.png)

#### 1.3.5 生成域名
![](https://s1.ax1x.com/2020/07/13/UYWgkF.png)
![](https://s1.ax1x.com/2020/07/13/UYW6TU.png)

### 1.4 将新增内容后的项目再次更新至GitHub与Gitee

#### 1.4.1 更新至GitHub

经操作发现更新至GitHub比较简单，只需要简单的几个命令行，把项目上传至GitHub即可，通过原有的域名即可看到更新后的博客，命令行如下：
```
root:~ ZouYue$ cd /Users/macos/docsify-blog 
root:docsify-blog ZouYue$ git init
重新初始化已存在的 Git 仓库于 /Users/macos/docsify-blog/.git/
root:docsify-blog ZouYue$ git add .
root:docsify-blog ZouYue$ git commit -m "forth commit"
位于分支 master
您的分支与上游分支 'origin/master' 一致。

无文件要提交，干净的工作区
root:docsify-blog ZouYue$ git remote add origin https://github.com/optics915/docsify-blog.git
fatal: 远程 origin 已经存在。
root:docsify-blog ZouYue$ git remote rm origin
root:docsify-blog ZouYue$ git remote add origin https://github.com/optics915/y
root:docsify-blog ZouYue$ git push -u origin master
分支 'master' 设置为跟踪来自 'origin' 的远程分支 'master'。
Everything up-to-date
root:docsify-blog ZouYue$ 

```
以下错误是我在另一个项目中遇到的问题，如果出现以下错误，那么再输入`git push -u origin +master`
```
 ! [rejected]        master -> master (fetch first)
error: 推送一些引用到 'https://github.com/optics915/MyBlog.git' 失败
提示：更新被拒绝，因为远程仓库包含您本地尚不存在的提交。这通常是因为另外
提示：一个仓库已向该引用进行了推送。再次推送前，您可能需要先整合远程变更
提示：（如 'git pull ...'）。
提示：详见 'git push --help' 中的 'Note about fast-forwards' 小节。
```
#### 1.4.2 更新至Gitee
但是在更新至Gitee时出现了一个问题，就是我用相同的方法将更新后的内容成功提交至gitee之后，无法向GitHub那样在网站地址自动更新HTML，无论是暂停、更新，还是重新新建项目从终端上传项目，不知道问题出在哪儿。

##### 1.4.2.1 更新至Gitee遇到的问题
此前将该项目再次上传至码云时发生了两个错误:

1、`fatal: 远程 origin 已经存在。`

2、
```
提示：更新被拒绝，因为远程仓库包含您本地尚不存在的提交。这通常是因为另外
提示：一个仓库已向该引用进行了推送。再次推送前，您可能需要先整合远
```
解决:

1、显示origin 已经存在，那我们只需要将origin删除，即命令`git remote rm origin`参考:https://www.cnblogs.com/LQ970811/p/12174743.html;

2、显示更新被拒绝，说明无法提交，按照后面这个链接的说法，我们进行强制提交，`origin +master`,完整命令：`git push -u origin +master`,参考:https://blog.csdn.net/qq_23100787/article/details/77529762?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.compare&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.compare




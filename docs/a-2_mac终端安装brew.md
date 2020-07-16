> 作者：optics915。
>
> **介绍:** 这是一个随手化的类似笔记的个人博客 作者: **[optics915](https://optics915.gitee.io/docsify-blog)** 。一般会在此记录一些从知乎、B站、GitHub上学来的有意思的操作，每一个过程都先自己操作成功之后再将其记录下来，以方便日后碰到相似类型时有理可依。

新式复现这一板块主要是在学习的过程中，根据别人的分享以及新遇到的问题，通过上网查找资料，综合记录一些此前未曾掌握的技巧以及复现别人的操作，我想对于我这样一个小白，从模仿、复现开始也是一种自我加强学习的过程吧。

## 2 mac终端安装brew
我记得当时尝试了好几个别人分享的方法，但是好像都或多或少在安装的过程中有一些错误而导致无法成功安装，下面记录了安装的每一个过程：
```
ZouYue:~ macos$ /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"

              开始执行Brew自动安装程序
             [cunkai.wang@foxmail.com]
           [2020-05-24 10:28:39][10.15]
       https://zhuanlan.zhihu.com/p/111014448


请选择一个下载镜像，例如中科大，输入1回车。
源有时候不稳定，如果git克隆报错重新运行脚本选择源。cask非必须，有部分人需要。
1、中科大下载源 2、清华大学下载源 3、腾讯下载源(不稳定) 4、阿里巴巴下载源(缺少cask源)
请输入序号: 1

  你选择了中国科学技术大学下载源

此脚本将要删除之前的brew(包括它下载的软件)，请自行备份。
->是否现在开始执行脚本（N/Y）y

--> 脚本开始执行
==> 通过命令删除之前的brew、创建一个新的Homebrew文件夹
(设置开机密码：在左上角苹果图标->系统偏好设置->"用户与群组"->更改密码)
(如果提示This incident will be reported. 在"用户与群组"中查看是否管理员)
请输入开机密码，输入过程不显示，输入完后回车
Password:
-> 创建文件夹 /usr/local/Homebrew
此步骤成功
-> 创建文件夹 /usr/local/Caskroom
此步骤成功
-> 创建文件夹 /usr/local/Cellar
此步骤成功
-> 创建文件夹 /usr/local/var/homebrew
此步骤成功
-> 创建文件夹 /usr/local/var/homebrew/linked
此步骤成功
git version 2.24.2 (Apple Git-127)

下载速度觉得慢可以ctrl+c或control+c重新运行脚本选择下载源
==> 克隆Homebrew基本文件(32M+)

未发现Git代理（属于正常状态）
Cloning into '/usr/local/Homebrew'...
remote: Enumerating objects: 137503, done.
remote: Total 137503 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (137503/137503), 33.52 MiB | 1.64 MiB/s, done.
Resolving deltas: 100% (101380/101380), done.
此步骤成功
==> 创建brew的替身
此步骤成功
==> 克隆Homebrew Core(224M+) 
此处如果显示Password表示需要再次输入开机密码，输入完后回车
Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-core'...
remote: Enumerating objects: 724426, done.
remote: Total 724426 (delta 0), reused 0 (delta 0)B | 8.19 MiB/s 
Receiving objects: 100% (724426/724426), 234.68 MiB | 2.03 MiB/s, done.
Resolving deltas: 100% (481993/481993), done.
此步骤成功
==> 克隆Homebrew Cask(248M+) 类似AppStore 
此处如果显示Password表示需要再次输入开机密码，输入完后回车
Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask'...
remote: Enumerating objects: 440570, done.
remote: Total 440570 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (440570/440570), 267.45 MiB | 2.21 MiB/s, done.
Resolving deltas: 100% (314892/314892), done.
此步骤成功
==> 配置国内镜像源HOMEBREW BOTTLE
此步骤成功
/Users/macos/.bash_profile:1: no such file or directory: 6/bin:.
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Fatal Python error: initfsencoding: unable to load the file system codec
ModuleNotFoundError: No module named 'encodings'

Current thread 0x000000010de51d40 (most recent call first):

==> 安装完成，brew版本

10.15
brew -v

Homebrew 2.2.17-96-g2e801c3-dirty
Homebrew/homebrew-core (git revision bce4b; last commit 2020-05-24)
Homebrew/homebrew-cask (git revision ca81bd; last commit 2020-05-23)
Brew前期配置成功

==> brew update

Already up-to-date.

        上一句如果提示Already up-to-date表示成功
            Brew自动安装程序运行完成
              国内地址已经配置完成

                初步介绍几个brew命令

        本地软件库列表：brew ls
        查找软件：brew search google（其中google替换为要查找的软件关键字）
        查看brew版本：brew -v  更新brew版本：brew update

现在可以输入命令open ~/.zshrc -e 或者 open ~/.bash_profile -e 整理一下重复的语句(运行 echo $SHELL 可以查看应该打开那一个文件修改)
```
参考：https://www.zhihu.com/question/35928898
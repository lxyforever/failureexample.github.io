---
title: 从零开始搭建我的个人博客（hexo+github）
date: 2019-04-29 11:41:36
tags:
---

# 个人博客搭建完全教程

## 1.为什么要搭建个人博客

## 2.如何搭建个人博客

## 3.环境准备

### 3.1 本地环境搭建

  ************
  本节完成本地 `git` 及 `Node.js` 的安装，电脑上已配置过可跳过本节。
  ************

* 安装 `git`  
  
  访问 [git官网][1] 来下载 `git` 安装包：  
![git官网点击Download下载git安装包][2]  
根据你的平台选择不同版本。本教程以win为例：  
![选择合适的安装版本][3]
安装包下载完成后一路默认即可完成 `git` 的安装：
![一路火花带闪电NNNNext][]  
ps：什么？你之前从未用过 git？那还不赶紧体验一下可能是这个星球目前为止**最好用最伟大的版本控制软件**？附上两个学习链接：  
[廖雪峰老师的git教程][5]  易上手易操作！半小时入门首选！  
[Pro Git的免费在线版本][6]  一整本讲 git 的书！看完完全掌握了 git！

[1]:https://git-scm.com
[2]:https://github.com/lxyforever/atest/raw/master/IMG/img/1.PNG
[3]:https://github.com/lxyforever/atest/raw/master/IMG/img/2.PNG
[4]:https://github.com/lxyforever/atest/raw/master/IMG/img/3.PNG
[5]:https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000 "廖雪峰老师的 git 教程"
[6]:https://git-scm.com/book/zh/v2 "Pro Git的在线版本"

* 安装 `Node.j

  进入[Node.js 官网下载页面][7]下载对应系统版本的 Node.js 的安装包，双击打开一路默认即可完成 `Node.js` 的安装：
  ![下载对应版本][8]  
  一路默认点击 next 即可完成安装：  
  ![一路next][9]  

  [7]:http://nodejs.cn/download/  "Node.js 官网下载页面"
  [8]:https://github.com/lxyforever/atest/raw/master/IMG/img/4.PNG  "我选择的64bit安装版本"
  [9]:https://github.com/lxyforever/atest/raw/master/IMG/img/5.PNG  "Node,js安装包打开界面"

### 3.2 注册Github账号并配置ssh key
  
* 注册 Github 账号
  进入 [Github 官网][10] 注册账号并登入，记住你的 `email`及`username`字段：  
  ![注册Github账号][11]
  点击右上角的 `+` 号并选择 `New repository` 新建一个空仓库，以后的hexo博客代码将会托管在这个库中：  
  ![新建远程库][12]
  新建时需要注意：
  1.`Repository name` 字段格式**务必为**   `xxxxxxx.github.io`，其中xxxxxx为用户自取，推荐使用github账号的username以避免不必要的麻烦。  
  2.为你的库添加合适的描述文字。  
  3.其他配置保持默认即可，确认无误点击绿色 `Create repository` 按钮完成创建  
  ![几个注意的地方][13]

* 配置本地 git

  打开资源管理器，在电脑合适的位置新建空文件夹存放博客相关文件。例如我的文件夹路径为 `D:\lxy\blog`。
  在文件夹内右键，选择 `Git Bush Here` 打开 git bash：
  ![新建文件夹][14]  
  打开后大概是这样：
  ![Git Bash][15]  
  输入下列代码配置 `git` 的基本信息，其中 `your username` 和 `your email` 根据个人的基本信息填写，推荐与注册 github 时的个人信息相同： 

      git config --global user.name "your username"  
      git config --global user.email "your email"  

* 配置ssh key
  为了把本地仓库的内容上传到 Github，需要为你的电脑配置 ssh key。简单的理解 ssh key 就是你这台计算机的身份证明，github 能确认是不是你本人在操作你托管在 github 上的仓库而不是非法访问。配置步骤如下：
  1.打开bash，输入如下代码生成RSA，将邮箱更换为注册 github 时的邮箱：
  
      ssh-keygen -t rsa -C "email@example.com"  

  输入后连按三下回车，进入 `C:\Users\Administrator\.ssh` 目录下，可以看到生成了三个文件：
  ![.ssh目录下][16]  
  使用文本编辑器打开图中标注的文件 `id_rsa.pub`，复制其中的内容（通常是一段乱码）。  
  
  进入 [github][10] 按如图所示进入设置界面：  
  ![github设置][17]
  
  按下图所示先点击右侧的 `SSH and GPG keys` 菜单进入 SSH 配置界面，再点击右上角绿色按钮 `New SSH key` 创建新的 SSH key：
  ![配置SSHkey][17]  （马赛克部分是我本来已经配置好的SSH key）

  title框中的内容随便填写，例如 `RSA_Home`。下面的 key 文本框复制入刚刚在 `id_rsa.pub` 文件中的乱码，检查后点击绿色按钮 `Add SSH key` 即可完成 SSH 配置。 
  ![配置SSHkey2][18]  

  配置完成后，在bash中输入：

      ssh -T git@github.com

  (不用将git@github.com替换，只输入上述指令即可)检查SSH是否配对完成。如果bash显示：

      Hi xxxxx(your user name)! You've successfully authenticated, but GitHub does not provide shell access.

  则表示SSH配对完成！至此，表示Github账号已经与个人电脑成功连接。

* 
[10]:https://github.com/ "Github官网"
[11]:https://github.com/lxyforever/atest/raw/master/IMG/img/6.PNG "注册Github账号"
[12]:https://github.com/lxyforever/atest/raw/master/IMG/img/7.PNG "新建远程库"
[13]:https://github.com/lxyforever/atest/raw/master/IMG/img/8.png "新建远程库2"
[14]:https://github.com/lxyforever/atest/raw/master/IMG/img/9.png "新建项目文件夹"
[15]:https://github.com/lxyforever/atest/raw/master/IMG/img/10.png "打开Git Bash"
[16]:https://github.com/lxyforever/atest/raw/master/IMG/img/11.png "本地生成ssh key"
[16]:https://github.com/lxyforever/atest/raw/master/IMG/img/12.png "github设置"
[17]:https://github.com/lxyforever/atest/raw/master/IMG/img/13.png "配置SSH key1"
[18]:https://github.com/lxyforever/atest/raw/master/IMG/img/14.png "配置SSH key2"

## 4.安装Hexo

### 4.1 初始化hexo

接下来进入最振奋人心的环节，配置Hexo!

在终端或者bash中输入下列命令安装Hexo：

    npm install hexo -g

*某些*网络问题会导致这一步需要一段时间。如果终端一直没反应，耐心等待即可。

漫长等待后，提示安装完成！此时使用以下命令检查安装是否完成：

    hexo -v

如果显示

![hexo安装成功][19]

则表示hexo已经成功安装到你的电脑上。

[19]:https://github.com/lxyforever/atest/raw/master/IMG/img/15.png "检验hexo是否安装成功"  

接下来在之前新建的 `blog` 文件夹下打开bash或者终端，输入以下命令初始化：

    hexo init
    npm install

新建完成后， `blog` 文件夹的目录如下：

    .
    ├── _config.yml
    ├── package.json
    ├── scaffolds
    ├── source
    |   ├── _drafts
    |   └── _posts
    └── themes

![文件夹路径图][20]

在初始化hexo博客前，输入如下命令：

>npm install hexo-deployer-git --save  

接下来依次输入如下命令启动hexo服务：

    hexo g
    hexo d
    hexo s

（文末附有hexo指令表，此处暂不解释）
之后命令行显示

    INFO  Start processing
    INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.

表示hexo服务成功启动，浏览器输入 http://localhost:4000 出现如下界面表示hexo初步配置完成:

![hexo初始界面][21]  

[20]:https://github.com/lxyforever/atest/raw/master/IMG/img/16.png "文件夹路径图"
[21]:https://github.com/lxyforever/atest/raw/master/IMG/img/17.png "hexo初始界面"

这个界面有点丑？没关系，hexo支持”海量主题，一键换装“，~~hexo暖暖启动~~

### 4.2 讲hexo部署到github上

现在我们可以通过本地端口访问搭建的本地hexo博客，现在我们将要把本地的hexo部署到 github 上。

用你的文本编辑器（不推荐使用win自带的记事本，推荐使用[Notepad++][23]）打开站点配置文件 `_config.yml` （此文件在你的项目根目录下对我来说也就是 `/blog`文件夹内）。

![hexo配置文件][22]

打开之后 `_config.yml` 之后拉倒最底下找到

    deploy:
     type:

![deploy字段][24]

字段，将其修改为：

    deploy:
     type: git
     repo: https://github.com/YourgithubName/YourgithubName.github.io.git
     branch: master

其中 YourgihubName 是你 github 自己的 username。然后在bash中输入以下指令：

    $ hexo clean      //清空缓存
    $ hexo generate   //生成静态页面
    $ hexo deploy     //部署博客至服务器/github/其他

也可以简写为

    $ hexo clean & hexo d -g

上一条命令会经常使用，建议抄在手心。

现在我们成功将hexo部署到了github上！在浏览器中输入 `yourusername.github.io` 试试看浏览你的博客吧！

[22]:https://github.com/lxyforever/atest/raw/master/IMG/img/18.png "hexo配置文件"
[23]:https://notepad-plus-plus.org/ "Notepad++ home page"
[24]:https://github.com/lxyforever/atest/raw/master/IMG/img/19.png "hexo配置文件deploy字段"


## 开始使用

hexo服务启动后，我们首先先来看看如何写博客，毕竟内容才是博客的第一生产力！关于hexo的主题以及各种配置之后我会另写一片文章专门讲解。下面先来详细讲解hexo新建命令

    $ hexo new [layout] \<title>

hexo 提供了三种布局 `draft`, `post`, `page` 文章的布局（layout）默认为 `post` 。他们分别对应不同的路径：

| 布局    | 路径            | 功能         |
| ------- | --------------- | ------------ |
| `post`  | `source/_post`  | 待推送的文章 |
| `draft` | `source/_draft` | 保存为草稿   |
| `page`  | `source/`       | 博客页面     |

想要新建一篇文章，那我们只要输入：

    $ hexo new "tittle"

如：

    $ hexo new "hello Hexo！"

其中tittle为你的博文标题。命令执行之后会在 `source/_post` 路径下新建一个 `tittle.md` 文件。`md` 为 `Markdown` 格式后缀，`Markdown` 是一种简单的标记语法，通过对文字进行一些标注，使文本具有一定的格式。附上 `Markdown` 的语法说明：

[Markdown.cn][25]

[25]:http://www.markdown.cn/ "markdown语法说明"

我们打开刚刚新建的 `title.md`，可以看到通过 `hexo` 指令创建的文本已经做好了初始化：

[title.md][26]

[26]:https://github.com/lxyforever/atest/raw/master/IMG/img/20.png "title.md打开"

其中 `title` 字段表示文章的标题，`date` 字段表示文章修改的时间， `tag` 字段表示文章所属的标签。刚建立的博客只有这三个默认字段，后续经过各种各样的配置之后可能还会有更多的字段来配置这篇文章的属性。

接下来，在 bash 中输入hexo的部署命令：

    $ hexo clean & hexo d -g

以后每次部署博客（发布新文章，修改博客样式）都是通过这个命令将本地博客部署到服务器上。

现在我们可以通过访问 `username.github.io` 来看看我们刚刚新发布的文章！
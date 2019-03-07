# GIT日记

![git cheap sheet](./gitcheapsheet.png)  

参考文档:  
[廖雪峰git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)  
[官方git中文教程](https://git-scm.com/book/zh/v2)  

## 安装Git  

* 在linux上安装git  
  首先,你可以试着输入`git`,看看系统有没有安装git:  
  ```
  $ git  
  the program 'git' is currently not installed. you can install it by typing:  
  sudo apt-get install git  
  ```  
* 在mac os x上安装git    
  如果你正在使用mac做开发,有两种安装git的方法.  
  一是安装homebrew,然后通过homebrew安装git,具体方法参考homebrew的文档:[http://brew.sh/](http://brew.sh/)  
  第二种方法更简单.也是推荐的方法,就是直接从App Store安装xcode,xcode集成了git.不过没有默认安装.你需要运行xcode.选择菜单"xcode"->"preferences",在弹出的窗口中找到"downloads",  
  选择"command line tools",点"install"就可以完成安装了.  

* 在Windows上安装git  
  在Windows上使用git,可以从git官网直接[下载安装程序](https://git-scm.com/downloads),(网速慢的同学请移步[国内镜像](https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fgit)),  
  然后按默认选项安装即可.  
  安装完成后,在开始菜单里找到"git"->"git bash",蹦出一个类似命令行窗口的东西.就说明git安装成功!  

  安装完成后,还需要最后一步设置,在命令行输入:  
  ```
  $git config --global user.name 'your name'  
  $git config --global user.email 'email@example.com'  

  ```  
  因为git是分布式版本控制系统,所以,每个机器都必须自报家门:你的名字和email地址.  
  注意:`git config`命令的`--global`参数,用了这个参数.表示你这台机器上的所有git仓库都会使用这个配置,当然也可以对某个仓库指定不同的用户名和email地址.  

## 创建版本库  
* 创建版本库  

  什么是版本库?版本库又叫仓库,英文名repository,你可以简单理解成一个目录,这个目录里的所有文件都可以被git管理起来,每个文件的修改,删除,git都能追踪,以便任何时刻都可以追踪历史,  
  或者在将来某个时刻可以"还原".  
  所以,创建一个版本库非常简单,首先,选择一个合适的地方,创建一个空目录:  
  ```
  $ mkdir git  
  $ cd git  
  $ pwd  
  /users/michael/git  
  ```
  `pwd`命令用于显示当前目录.
  **如果你使用Windows系统,为了避免遇到各种莫名其妙的问题,请确保目录名(包括父目录)不包含中文.**  
  第二步,通过`git init`命令把这个目录变成git可以管理的仓库:  
  ```
  $ git init  
  initialized empty git repository in /users/michael/git/.git/  
  ```
  瞬间git就把仓库建好了,而且告诉你是一个空仓库,细心的读者可以发现当前目录下多了一个`.git`的目录,这个目录是git来跟踪管理版本库的,没事千万不要手动修改这个目录里的文件.  
  也不一定必须在空目录下创建git仓库,选择一个已经有东西的目录也是可以的.  

* 把文件添加到版本库  
  我们编写一个`readme.txt`文件,内容如下:  
  ```
  git is a version control system.  
  git is free software.  
  ```
  一定要放到`git`目录下(子目录也行),因为这是一个Git仓库,放到其他地方git再厉害也找不到这个文件.  
  第一步,用命令`git add`告诉git,把文件添加到仓库:  
  ```
  $ git add readme.txt  
  ```
  执行上面的命令,没有任何显示,这就对了,Unix的哲学是"没有消息就是好消息",说明添加成功.  
  第二步,用命令`git commit`告诉git,把文件提交到仓库:  
  ```
  $ git commit -m 'wrote a readme file'  
  [master (root-commit) eaadf4e] wrote a readme file  
   1 file changed,2 insertions(+)  
   create mode 100644 readme.txt  
  ```
  简单解释一下`git commit`命令,`-m`后面输入的是本次提交的说明,可以输入任何内容,当然最好是有意义的,这样你就能从历史记录里方便地找到改动记录.  
  `git commit`命名执行成功后会告诉你,`1 file changed`:1个文件被改动;`2 insertions`:插入了两行内容.  
  **为什么git添加文件需要`add`,`commit`一共两步呢?因为`commit`可以一次提交很多文件,所以你可以多次`add`不同的文件,比如:**  
  ```
  $ git add file1.txt  
  $ git add file2.txt file3.txt  
  $ git commit -m 'add 3 files.'  
  ```
* 小结  
  初始化一个Git仓库,使用`git init`命令.  
  添加文件到git仓库,分两步:  
    1. 使用命令`git add <file>`,注意,可反复多次使用,添加多个文件; 
    2. 使用命令`git commit -m <message>`,完成.  


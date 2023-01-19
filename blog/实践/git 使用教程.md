## 什么是git
git是版本控制，提交跟踪的记录版本的软件，主要目的是提交资料到远程服务器。
说实话单纯用来备份数据实在是有点大材小用
不过也懒的整理了，而且必须数据备份，奶奶的，我一星期的工作量啊
主要也是跨平台
## 下载 git 和 初始化 git
[git官网](https://git-scm-com/downloads)
一路默认即可
安装后需要设置
`git config --global user.name "Your Name"`
`git config --global user.email "email@example.com"`
因为git是分布式版本控制系统，所以每台机器都必须有自己的名字和地址
注意`git config`这个命令的`--global`这个参数是表示这台机器所有的git仓库都使用这个配置
## 创建版本库
第一步先找到你要创立的git库，记好地址
或者用`pwd`来显示当前目录
2. 通过`git init` 来把这个目录变成git可以管理的仓库
先创建个文本文件`.txt` 的
1. 用`git add readme.txt` 来告诉Git，把文件添加到仓库
2. `git commit -m "wrote a readme file"` 来把文件提交到仓库
: `git commit` 后面的 `-m` 是输入本次提交的说明，不想输也没事，顶多会被骂
`add` 一次提交一份文件，`commit` 可以一次提交多个文件，所以有两步，简单来说就是先放进去，然后打包给提交了
## 基本使用技巧
3. `git status` 查看仓库当前状态
4. `git diff readme.txt` 查看上次修改了什么
5. `git log` 每次提交啥之类的历史记录，简化输出 `git log --pretty=oneline`
6. 回退版本 `git reset --hard HEAD^` 这个参数里`HEAD` 表示当前版本，`HEAD^`上次版本，`HEAD~`一百个版本之前
7. 如果想要返回去，
	1. 确保之前的命令窗口没关掉，
	2. 找到提交版本的id， 即`commit id`是多少，输入前五位就差不多了，几位也成
	3. 或者使用`git reflog` 查找每一次的命令，原理也很好理解
另外需要明白一些工作区和暂存区的知识，基本上就就能明白在干什么
8. `git checkout -- readme.txt`丢弃工作区的修改
9. `git reset HEAD readme.txt` 丢弃暂存区的修改，`HEAD`表示当前版本
10. 删除文件 `git rm test.txt` `git commit -m "remove test.txt"` 
11. 误删文件恢复最新版本 `git checkout -- test.txt`
## 添加远程仓库
1. 先创建密钥
`ssh-keygen -t rsa -C "youremail@example.com"`
根据提示找到你放密钥的地方，并找到 `id_rsa.pub`把里面的内容打开，复制
登录github，打开account setting，找到SSH Keys
点击 Add SSH Key ,填写任意 Title，在Key文本框粘贴
点击 Add Key
基本上就是添加个双重认证
在github上创建一个新仓库，名字随意
1. 与本地关联
`git remote add origin git@github.com:Jerry857/blog.git`
jerry857是你自己的github名字，后面是你仓库的地址
origin 是你本地对于github的起的别名，当然可以随意
2. 第一次推送`git push -u origin master`
3. 之后就`git push origin master` master是分支名字
如果有什么警告就同意即可
## 删除远程库
地址写错了或者其他
`git remote -v` 查看远程库信息，根据名字选择删除
`git remote rm origin` 其实就是接触绑定
## 从远程库克隆 
git clone 
## 分支管理
这个暂时不用管，就一个人也用不到，除非是写软件
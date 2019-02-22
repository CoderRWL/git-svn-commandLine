# git-svn-commandLine
git ,svn命令行控制


# 配置
git config user.name ###
git config user.email ###
git config --gloabal user.name ###
git config --global user.email ###
git config -l
git config -e 
git config alias
git config --gloabal

# 常用命令
### 文件名/路径 ###
git status ###
git statua 
git log ###
git log
git reflog
git log -N 
git diff ###
git diff

git init
git init ###
git add ###
git add .
git commit -m" 注释" ###
git commit -m"注释"

git reset --hard HEAD^
git reset --hard HEAD^^
git reset --hard HEAD^^^
...
git reset --hard HEAD~N
git reset --hard  版本号

git rm
git clone URL
git clone URL 路径

git pull
git push

# help
git help ：git指令帮助手册
查看其他指令的做法：git help 其他指令

git config ：git的配置信息相关（修改的是.git/config文件）
配置用户名：git config “user.name” 用户名（用于跟踪修改记录）
配置邮箱：git config “user.email” 邮箱（用于多人开发间的沟通）
查看配置信息：git config –l
编辑配置信息：git config –e（用vim编辑，:wq是退出vim编辑器）
设置指令的别名：git config alias.别名 原指令名称
设置带参数指令的别名：git config alias.别名 “原指令名称 参数”
将此设置应用到整个系统中：git config ––gloabal
git status ：查文件的状态
查看某个文件的状态：git status 文件名
查看当前路径所有文件的状态：git status

git log ：查看文件的修改日志
查看某个文件的修改日志：git log 文件名
查看当前路径所有文件的修改日志：git log
用一行的方式查看简单的日志信息：git log ––pretty=oneline
查看最近的N次修改：git log –N（N是一个整数）

git diff ：查看文件最新改动的地方
查看某个文件的最新改动的地方：git diff 文件名
查看当前路径所有文件最新改动的地方：git diff
git init ：初始化一个空的本地仓库，生成一个.git目录，用于维护版本信息
在当前路径初始化仓库：git init
在其他路径初始化仓库：git init 仓库路径

git add ：将工作区的文件保存到暂缓区
保存某个文件到暂缓区：git add 文件名
保存当前路径的所有文件到暂缓区：git add .（注意，最后是一个点 . ）

git commit ：将暂缓区的文件提交到当前分支
提交某个文件到分支：git commit -m ”注释” 文件名
保存当前路径的所有文件到分支：git commit -m ”注释” 
git reset ：版本回退（建议加上––hard参数，git支持无限次后悔）
回退到上一个版本：git reset ––hard HEAD^
回退到上上一个版本：git reset ––hard HEAD^^
回退到上N个版本：git reset ––hard HEAD~N（N是一个整数）
回退到任意一个版本：git reset ––hard 版本号（版本号用7位即可）

git reflog ：查看指令使用记录（能够查看所有的版本号）

git rm：删除文件（删完之后要进行commit操作，才能同步到版本库）
git clone：下载远程仓库到本地
下载远程仓库到当前路径：git clone 仓库的URL
下载远程仓库到特定路径：git clone 仓库的URL 存放仓库的路径

git pull：下载远程仓库的最新信息到本地仓库

git push：将本地的仓库信息推送到远程仓库


# svn
# 查看工作目录状态
$ svn st
# 将文件添加到本地版本库中
$ svn add main.c
# 将文件提交到服务器的版本库中
$ svn ci -m "添加了main.c文件"

"小结" - 添加文件的两个步骤
--------------------------------------------------------------------------------
1>  将新建的文件添加到本地代码库
$ svn add main.c
2>  将刚刚添加的文件提交到服务器
$ svn ci -m "备注信息"

注意：一定要养成写注释的良好习惯

03.	团队成员加入
================================================================================

1>  张三
$ svn co http://10.0.1.15/svn/weibo --username=zhangsan --password=zhangsan
2>  李四
$ svn co http://10.0.1.15/svn/weibo --username=lisi --password=lisi

"小结" 至此，一个项目的搭建工作就告一段落了
1> 项目准备工作，通常由项目经理完成
2> 程序员只需要把项目 co 到本地即可

提示：新入职一家公司后，别忘记让经理分配 svn 的账号和密码

04.	张三添加文件
================================================================================

# 添加文件 Person.h Person.m
$ touch Person.h Person.m
# 修改 Person.h Person.m
$ open Person.h
$ open Person.m
# 将 Person.h Person.m 添加到本地代码库
$ svn add Person.*
# 将内容提交到服务器
$ svn ci -m "添加了Person类"

05. 删除文件
================================================================================

# 删除文件
$ svn rm Person.h
# 提交删除
$ svn ci -m "删除了文件"

注意：不要使用文件管理器直接删除文件

06. 撤销修改
================================================================================
$ svn revert Person.m

07. 恢复到之前的某个版本
$ svn update -r 5
================================================================================
$ svn up

08. 冲突解决
(p) postpone            对比
(mc) mine-conflict      使用我的
(tc) theirs-conflict    使用对方的

svn st 显示的文件状态



状态说明：描述文件被添加、删除或其他修改
-----------------------------------------------------------------
' ' 没有修改
'A' 被添加到本地代码仓库
'C' 冲突
'D' 被删除
'I' 被忽略
'M' 被修改
'R' 被替换
'X' 外部定义创建的版本目录
'?' 文件没有被添加到本地版本库内,不在SVN的管理之下
'!' 文件丢失或者不完整(不识别该文件)
'~' 受控文件被其他文件阻隔
'U' 更新最新的代码到本地(本地有文件的情况下)
'G' 产生冲突后,更新操作去解决冲突,相当于进行合并


1>  显示隐藏文件夹
# 显示隐藏文件
$ defaults write com.apple.finder AppleShowAllFiles Yes && killall Finder
# 不显示隐藏文件
$ defaults write com.apple.finder AppleShowAllFiles No && killall Finder
















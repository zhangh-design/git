# git
Linux命令：
- pwd (命令，显示当前所在目录结构）
- cry+ c 在git 命令窗口中会放弃当前行，直接跳到下一个命令输入行上面
- cat file (file 某个文件的名称，查看当前文件的内容）
- cd ~ (切换到当前系统用户所在目录）/c/users/用户
- cd .. 返回上一层
- ls 查看文件目录中的文件列表
	
语句提示：
	Working Tree --工作区
	working directory --工作区
	Staged --暂存区
	unstage --工作区
	committed --对象区
	
	Local Repository --本地库
	Remote Repository --远程库
	
	On branch master --你当前在master分支
	No commits yet --你还没提交
	Untracket files --文件没有被追踪,表示当前处于工作区
	Changes to be committed --要提交可以执行commit
	use "git add <file>..."  to include in what will be committed --你可以使用add命令添加到暂存区
	will be committed --暂存区
	use "git reset head <file>..." to unstage --使用reset head 命令将文件从暂存区回退到工作区
	use "git checkout -- <file>..." to discard changes in working directory --使用checkout命令,在工作区里放弃修改操作回退到对象区
	1 file changed , 0 insertions（+）, 0 deletions（-）--1个文件改变/插入 , 文件中0个内容插入 , 0个内容删除
	Administrator@MS-20160315UFQB MINGW64 ~/Desktop/a/Vue-zVue-design (master) --master分支
	use "git rm --cached <file>..." to unstage --回退可以执行 ‘cached’ ,回退到工作区
	nothing to commit , working tree clean --nothing to commit 没有内容提交, 提交时对象区证明暂存区现在是干净没有文件的, working tree clean 工作区也是干净的, 证明文件现在都在对象区里了
	Changes not staged for commit --没有在暂存区, 操作系统删除的文件不会经过暂存区, git rm删除的文件会在暂存区
	use "git add/rm <file>..." to update what will be commited --可以执行add添加到暂存区
	is not fully merged --存在一个未合并的分支
	If your are show you want to delete it, run 'git branch -D new_branch' --强制删除可以使用-D大d 
	Auto-merging a.txt --自动合并a.txt
	CONFLICT (conent)：Merge conflict in a.txt --内容冲突, 合并冲突在a.txt
	fix conflicts and then commit the result --建议修改冲突, 并在提交一次
	Unmerged paths --没有合并
	use "git add <file>..." to mark resolution --告知git冲突已经解决
	not staged --不在暂存区
	HEAD is now at 298bf42值 --分支指针当前位于298bf42这个commit点
	You are in 'detached HEAD' state --你现在在游离状态
	You can look around --你可以到处看看,但是不能乱动，你的行为都有很严重的后果
	make experimental changes and commit them --如果你一定要改变也可以, 但是一定要commit 他们
	If you want to create a new branch to retain commits you create.... --你可以创建一个分支，现在是一个好机会
	Please commit you changes --请提交你的修改
	you are leaving 1 commit behind, not connected to any of you branches --在你的后面有一个commit提交, 但不会合并到你的分支中 
	commit your changes --提交你的修改
	stash them before you switch branches --保存临时现场
	commit your changes or stash them before you switch branches --提交你的修改或保存临时现场
	Auto-merging a.txt --自动合并a.txt
	Merge conflict in a.txt --冲突在a.txt
	The key you are authenticating with has been marked as read only -- 只读权限, 权限不足
	Your branch is up to date with 'origin/master' --你的分支和'origin/master'分支保持一致
	Your branch is ahead of 'origin/master' by 1 commit --你当前的分支比远程的分支前进了一个提交点，其实就是建议你赶紧 git push 把远程的跟新下
	local out of date --本地已经过期, 其实就是建议你赶紧 git pull
	Fast-forward --更新
	Fast-forward --拒绝了
	This is usually caused by another repository pushing --有另一个仓库也进行了push
	to the same ref --并且是同一引用，也就是同一行
	merge failed --合并冲突
 error: <file> has local modifications --本地文件已经修改，如果是rm 操作请求add和commit	

	to be committed --表示当前在暂存区

git commit提交的shal值：
	shal (分布式id生成器）
	
git目录结构：
	.git ：git版本控制的目录, 本地版本控制中心

Git 如何上传一个空文件夹：必须在空文件夹下面放一个.gitkeep文件在该文件中写下如下内容(可选)：
```
# Ignore everything in this directory 
* 
# Except this file !.gitkeep
```
	
git的状态：
	已管理			 工作区
	已修改(modified) 工作区 add->staged
	已暂存(staged)	 暂存区 commit->committed
	已提交(committed) 对象区 push->github

基础设置：
	设置邮箱、账户名：
		git config --global (基本不用，给整个计算机一次性设置）
		git config --system （推荐，给当前计算机用户一次性设置）C:/Users/Administrator/.gitconfig
		git config --local （给当前项目一次性设置）.git/config

		优先级是 local > system > global	

		git config --local user.name 'zhangh'
		git config --local user.email '506365426@qq.com'

	查看用户名和邮箱地址：
		git config user.name
		
		git config user.email
		
	删除账户和邮箱：(local级别unset进入.git目录)
		git config --local --unset user.name
		git config --local --unset user.email

git操作提交过程讲解：
	从工作区到暂存区是add, 从暂存区到对象区是commit, 从暂存区到工作区是cached, 从工作区放弃修改回退到对象区是checkout。
	在暂存区/对象区里修改文件后, 文件会自动回退到工作区。

忽略文件:
	.gitignore (这既是一个文件也是一个命令）需要在.git的同级目录创建
	要忽略.gitignore自身, 只需要把名字写到.gitignore文件中。
	.gitignore 通配符匹配：
	*任意字符
	*.properties (忽略所有以.properties结尾的文件）
	非 （排除符号）！
	!b.properties (排除b.properties文件）
	dir/*.txt
	
	
	忽略文件夹：
	文件夹名称/
	dir/ 忽略dir目录下的所有文件
	dir/*/*.txt 能够忽略 dir/abc/a.txt
	
	注意：如果是空文件夹则git会自动忽略
	#号可以在.gitignore 中进行单行注释
	
	
常用指令：
	git --version (查看版本）
	初始化git仓库
		git init (将某个目录纳入git管理,对应 ‘已管理’ 状态)
		git init --bare (git裸库,没有工作区的工作库,裸库一般都在远程服务端)

	git status (查看git状态)

	git log (查看提交日志, 回退的日志无法看到)
	git log --graph (查看图形化日志,有commit链信息)
	git log --graph --pretty=oneline --abbrev-comit (图形化日志,commit的shal值只显示前面几位)
	git log -2 (num次数, 只查看最近提交的2次记录日志)
	git log --pretty=oneline (一行展示shal值, 作者提交时间不显示)
 git log <last release> HEAD --grep feature (显示本次发布新增加的功能)	

	git relog (查看所有提交操作, 回退的日志也能看到)
	
	git log refs/remotes/origin/master (查看github远端分支的日志)
	
	
	git add <file> (将文件从工作区add到暂存区)
	git add . (将当前分支中工作区内已修改的文件add到暂存区)
	git add* (不建议使用会将忽略问价也add到暂存区)
 git add 文件夹/ (Git命令行添加整个文件夹及目录)	

git add -u (它仅监控已经被add的文件，它会将被修改的文件提交到暂存区，add -u不会提交新文件)

	git commit -m '注释' (commit提交命令)
	git commit -am '注释' (合并add 和 commit 一步操作, 不能用于文件的第一次操作)
	
	
	
	git checkout -- <file> (在工作区里放弃修改操作回退到对象区, 注意 -- 后面有一个空格)
	
	
	git rm --cached <file> (将文件从暂存区回退到工作区)
	
	git rm <file> (在对象区中删除一个文件, 此时文件回退到暂存区, 可以执行reset head回退到工作区或者commit提交删除操作此时文件彻底删除了, 所以彻底删除文件需要两步rm和commit)
	
git rm -r 文件夹/ (在本地仓库删除指定文件夹)

	git reset head <file> (将文件从暂存区回退到工作区)
	
	
	git mv hello.txt hello2.txt (git 文件重命名, 执行git add . 和 git commit -m "重命名"，文件重命名成功)
	
	git commit --amend -m '重写注释' (重写注释, 但是只能修改最近一次提交的注释)
	
	git rm *.properties (删除文件可以使用通配符)
	
	git branch (查看本地分支)
	git branch -a (查看本地和远程分支)
	git branch -av (查看本地和远程分支, 并且显示commit的shal值)
	
	git branch new_branch (创建分支new_branch分支名称, 可以是任意名称)
	
	git chenkout 分支名 (切换分支)
	
	git branch -d (删除分支, 不过不能在自己的分支里删本分支, 切换到其它分支在删除指定分支)
	
	git branch -D (忽略未合并, 强制删除分支)
	
	git checkout -b 分支名 (创建新分支并切换)
	
	git merger new_branch (合并分支) 
	
	git branch -v (查看分支最近一次提交的shal值)
	
	git branch -m new_branch new_branch1 (修改branch分支名称)
	
	git reset --hard HEAD~1 (回退到前1次)
	git reset --hard 7a69317 (回退到某一次, 7a69317是shal值)
	
	
	git checkout shal值 (版本穿梭处于游离状态)
		1：修改后，必须提交 （对未来的a.txt不会产生影响）
		2：创建分支的好时机 （git branch 分支名 shal值）
	
	git branch <new-branch-name> shal值 (穿梭回去后创建分支)
	
	git stash (保存现场, 默认名称)
	
	git stash save 'mystash' (保存现场, 起一个新的现场名称)
	
	git stash pop (还原并删除现场)
	
	git stash apply (还原但不删除现场)
	
	git stash list (查看现场)
	
	git stash drop stash@{0} (删除任意一次现场)
	
	git stash apply stash@{0} (还原任意一次现场)
	
	
	git tag 版本名 (创建标签)
	git tag -a 版本名 -m '注释' (创建标签)
	git tag (查看标签)
	git tag -d 版本名 (删除标签)
	git push origin 版本名 (Git把Tag推送到远程仓库)
git push origin --tags (push所有tag到远程仓库)
	
	git blame a.txt (查看a.txt的所有提交commit shal值，以及每一行的作者)
	
	git ls-files (git怎么查看哪些文件是在版本控制下)
	
	git diff (比较区中的文件差异)
	
	git diff commit的shal值 (对象区和工作区的差异)
	
	git diff --cached commit的shal值 (对象区和暂存区的差异)
	
	git diff --canched HEAD (当前对象区最近一次commit点和暂存区的差异)
	
	
	
	git clone 远程仓库名称 (克隆项目)
	
	git remote add origin https://github.com/zhangh-design/Vue-zVue-design.git (让git知道以后 ‘origin’ 就是代表了 后面那个仓库地址，意思就是起个别名)
	
	git push -u origin master (推送到github, 第一次推送需要关联)
	
	git push (推送到github)
	
	git remote rm origin (删除github和本地的关联)
	
	git remote show (查看当前服务器列表)
	
	git remote show origin (查看列表中origin远程服务器的配置详情信息)
	
	git clone 远程仓库名称 新名称 (克隆项目并修改名称)
	
	
	
	
	
	
	
	
	
	

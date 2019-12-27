
Git 笔记
======

作者：沐枫  
 日期：2019-05-09

> Git官方教程网址: [https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)

> git --version 		//查看版本



# Git的基本概念
#### 【git的运行流程】:
>	应该明白git底层的运行流程，当我们添加或者修改了文件并且add到Stage Area之后，首先会根据文件内容创建不同的blob，
	
>	当进行提交之后马上创建一个tree组件把需要的blob组件添加进去，之后再封装到一个commit组件中完成本次提交。
	
>	在将来进行reset的时候可以直接使用git reset --hard xxxxx可以恢复到某个特定的版本，
	
>	在reset之后，git会根据这个commit组件的id快速的找到tree组件，
	
>	然后根据tree找到blob组件，之后对仓库进行还原，整个过程都是以hash和二进制进行操作，所以git执行效率非常之高。


#### 【什么是版本库】:

	版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

	1、git管理就像是一个文件系统。每commit(commit 就是 root(根) 节点) 一次就创建一棵大树 tree ，tree下有很多blob，blob就相当于叶子节点存储文件值。

	2、没有文件也就是没有blob对象的目录是不会被git管理的，因为git要对文件进行版本管理，所以没有必要对空目录生成对象。

	git log --all --graph
	
#### 【区域】:
	工作区： 代码编辑器
	HEAD：
	暂存区： add
	版本库： commit
	

#### 【git集成使用禁忌 】
	1、 禁止向集成(公共)分支执行push -f操作。

	2、 禁止向集成(公共)分支执行变更历史的操作。


#### 【配置user信息， 新安装好git后一定要进行的最小基本配置】
	命令|注释
	----|----
	git config --global user.name 'myName'|		
	git config --global user.email 'myEmail'|	
	git config --global|						//全局 常用
	git config --local| 						//本地 很少用
	git config --system| 						//系统 基本不用

---
#### 【查看配置user信息】
	git config --list
	git config --list --local
	git config --list --blobal
	git config --list --system












# Git代码管理初始化方式：

---
#### 【一、本地创建方式】：

**1、已存在目项，把已有的项目代码纳入Git管理。**

	1、进入到要进行Git管理的目项的根目录。
	2、在当前目录打开，命令窗口。
	3、执行 git init //初始化git

**2、全新的项目，新建的项目直接用Git管理。**

	1、进入你常用来存放项目代码的目录。
	2、git init 项目名（注：用拼音或英文，不能用中文）， 会在当前目录中创建一个以你刚才输入的项目名称 同名的文件夹。
	3、进入你创建的这个项目目录中，就可以进行相应的git操了。


**3、关联远程仓库**
	1、git remote add origin 仓库地址

	如：git remote add origin git@gitlab.smgtech.net:01810597/git_demo.git

	由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
	
	如：git push -u origin master   以后就可以直接用 git pull 命就OK了。


---
#### 【二、远程克隆方式】：

	git clone url 项目名(可以在本地自定义一个分支名 或者 为空[和远程一样的名字]也行) --branch 分支名		//分支名 克隆远程git项目的分支

【参数说明】：
	git clone --help			//帮助信息
	git clone url 默认master分支		//克隆远程git项目   在GitHub 上 打开项目，点击Clone or Download 按钮选择 Use HTTPS 复制项目地址
	git clone url --branch 分支名 		//分支名 克隆远程git项目的分支
	


> 例：git clone git@gitlab.smgtech.net:01810266/xuantishenbao.git --branch test  或 master


---
#### 【重新获取】删除本地文件后 Git从远程仓库重新获取
	(1)、git fetch --all
	(2)、git reset --hard 或 git reset --hard origin/test
	(3)、git pull








# Git对代码的提交与维护：

---
#### 【代码提交】【注：提交】[如果在多人协作时，一定要 先拉 git pull 再推 git push]

	git pull			
	git pull origin test		//从指定的远程服务器拉取
	git pull --rebase		【推荐使用】

**代码提交到远程仓库的步骤下如：**

### 【一】、添加：到暂存区（本地）:

	git add .			//将文件的修改，文件的新建，添加到暂存区。 跟踪 Git的暂存区
	git add -u 			//将文件的修改、文件的删除，添加到暂存区。
	git add -A			//将文件的修改，文件的删除，文件的新建，添加到暂存区(git add -A 等同于git add -all)。
	git add *			//添加存储所有

	git add 文件名			//添加存储指定改动过的文件【注：要加上文件的路径哦！, 文件要加个文件后缀名，多个文件或目录中间用 空格 隔开】
	git add 文件名1 文件名2...	//添加存储指定改动过的多个文件 中间用空格分开


	工作中一般是用到 git add . 或者 git add -A 	//-A(-all)
	git add -A相对于git add -u命令的优点 ： 可以提交所有被删除、被替换、被修改和新增的文件到数据暂存区，而git add -u 只能操作跟踪过的文件


【文件差异对比】：

	1、比较 工作区(没add之前) 和 暂存区(add以后) 所含文件的差异
		git diff						//不指定文件时，会显示所有不同的文件，如都没差异则无任何显示！！
		git diff -- index.html css/base.css			//指定查看index.html和base.css这两个文的暂存区和 HEAD之间的差异，如没差异则无显示！！

	2、比较 暂存区(add后) 和 HEAD(没add) 所含文件的差异
		git diff --cached      或者	git diff —staged  	//不指定文件时，会显示所有不同的文件，如都没差异则无任何显示！！
		git diff --cached -- index.html css/base.css		//指定查看index.html和base.css这两个【多个文件之间用 空格隔开】文的暂存区和 HEAD之间的差异，如没差异则无显示！！



【文件恢复：工作区不想要用：checkout，暂存区不想要用：reset】：

	1、从暂存区(add以后) 恢复为 和 HEAD的一样，相当于取消add的操作
		git reset HEAD			//不指定文件时，会把暂存区所有的文件恢复到HEAD（工作区）
		git reset HEAD -- index.html	//指定要恢复的文件，多个文件之间用 空格隔开

	2、让工作区的文件 恢复为 和 暂存区一样
		git checkout -- index.html	//指定要恢复的文件，多个文件之间用 空格隔开


【文件比较 与 恢复总结】：
	git diff 			暂存区与工作区比较

	git diff --cached	暂存区与HEAD比较

	git reset HEAD		暂存区恢复成HEAD

	git checkout		暂存区覆盖工作区修改 


【总结】
	1、修改了工作区，恢复：git checkout 

	2、add后，想撤销： git reset HEAD 

	3、commit后，想撤销： git reset--hard hash值 （注：一旦执行，无法恢复）



### 【二】、提交：到版本库:

	git commit -m "描述"		//提交所有改动过的文件 并添加描述 到版本库 [执行提交时，系统会要求输入提交信息。请务必输入提交信息，因为在空白的状态下执行提交会失败的。]
	git commit -am "描述"		//提交所有改动过的文件 并添加描述 到版本库 （-am 表示 没有执行 git add . 也能提交）
	
【怎么修改最新commit的message注：--amend 此修改一般用于未push之前修改commit信息】

	git commit --amend 		//对最新(最近)一次提交做 commit 修改


【消除最近的几次commit提交 回退到之前的某次提交，注：请确定好，考虑清楚 后在操作，因为git reset --hard hash值 这个命令一下去，就不能恢复了！！！切记！！！】
	
	1、git log --all --graph	// 显示所有提交日志，会显示每次提交的hash值（就是commit_id），便于复制用于回退

	2、git reset --hard 970b99e2ce5 //回退到970b99e2ce5这个提交前，注：每次提交都有一个唯一的hash值 如commit 970b99e2ce57f93130d66eb1daef33a8f506a182 （只要唯一，复制一部分就可以了）


	【 git reset 有三个参数】：
		1、--soft		// 这个只是把 HEAD 指向的 commit 恢复到你指定的 commit，暂存区、工作区保持不变

		2、--hard		// 这个是 把 HEAD、工作区、暂存区、都修改为你指定的 commit 的时候的文件状态【--hard 危险参数】

		3、--mixed		// 这个是不加时候的默认参数，把 HEAD、暂存区 修改为 你指定的 commit 的时候的文件状态，工作区保持不变


【比较不同commit提交的文件差异】
	1、git log --all --graph	// 显示所有提交日志，会显示每次提交的hash值（就是commit_id），便于复制用于回退

	2、git diff 970b99e2ce57f 8f59099ce643e2	//所有查看 970b99e2ce57f提交 和 8f59099ce643e2提交的所有文件的差异

	2、git diff 970b99e2ce57f 8f59099ce643e2 -- index.html	//指定查看 970b99e2ce57f提交 和 8f59099ce643e2提交指定到index.html文件的差异

【比较不同branch分支的文件差异】
	git diff master dev 		//查看 master分支 和 dev分支的所有有差异的文件

	git diff master dev -- index.html	//指定查看 master分支 和 dev分支指定到index.html文件的差异

或者
	1、git branch -av		// 显示所有分支，会显示每个分支的hash值（就是branch_id），便于复制用于回退

	2、git diff d3ff58e dd9cc30 	//所有查看 d3ff58e分支 和 dd9cc30分支的所有文件的差异

	2、git diff d3ff58e dd9cc30 -- index.html	//指定查看 d3ff58e分支 和 dd9cc30分支指定到index.html文件的差异
	



### 【三】、推送：到远程仓库:
	git push -u origin test		//真正开始提交 到主分支 【注：加了参数-u后，在以后推送时可直接用git push 代替git push origin master 第一次为了产生关联 】
	git push -f 				//【注：除非只有自己一个人用，不然用 push --force 的都该去死，因为：git push -f表示【强行推送】将目前自己本机的代码库推送到远端，并覆盖！所以慎用！！】
	git push					//再修改后就可以这样提交(或叫 推)






### 【四】、Git的备份:

【常用的传输协议】:

	常用协议 | 语法格式 | 内容说明
	-------|-------|-------
	本地协议(1) | /path/iDitor.git | 哑协议【linux】（本地） 哑协议传输进度不可见
	本地协议(2) | file:///path/iDitor.git | 智能协议（本地） 智能协议传输进度可见，而且速度比哑协议要快
	http/https协议 | http://gitlab.smgtech.net/01810597/iDitor.git | 智能协议（远程: 用户名，密码）
	ssh协议 | git@gitlab.smgtech.net:01810597/iDitor.git | 智能协议【工作中最常用】（远程：密钥 SSH Key）

【查看关联的远程仓库信息】:
>   git remote					//查看关联的远程仓库的名称

>	git remote -v				//查看关联的远程仓库的详细信息
	
>	git remote show name 		//看查远程仓库name的详细信息


【添加(备份)远程仓库的关联】:
	远程仓库的名称一般默认为 origin ，当然，你可以设置为其他的名称。
	通过 git clone 下载项目到本地时，项目文件夹中的 .git 目录就是版本库目录。
	.git 目录中的 config 文件中有远程仓库的关联配置。

>   git remote add origin <url>		//git_url 为你的远程仓库的 url，可采用 http 协议或 ssh（git） 协议
 
 例如：
>   git remote add zhineng file:///e/gitDemo/zhineng.git //为远程仓库起别名zhineng


【删除远程仓库的关联】:
>	git remote remove <name>


【修改远程仓库的关联】
	比如，之前你关联的远程仓库使用的协议是 http ，你想将关联的远程仓库的 url 改为 ssh 协议的。
	修改关联的远程仓库的方法，主要有3种。

第1种：
>	git remote set-url origin <newurl>	//使用 git remote set-url 命令，更新远程仓库的 url

第2种：
	先删除之前关联的远程仓库，再来添加新的远程仓库关联，注：远程仓库的名称推荐使用默认的名称 origin
	
>	git remote remove <name>	//删除关联的远程仓库
>	git remote add <name> <url>	//添加新的远程仓库关联

第3种：
	直接修改项目目录下的 .git 目录中的 config 配置文件。

>	git remote add name url 	//为远程仓库起别名
>	git remote show name 		//显示远程仓库name的详细信息
	
	
	

	1）找个目录执行 clone 。或
	2）用init建个git仓库，然后从备份数据库添加remote，再push到新建仓库；或者
	3）用init建个git仓库，然后在新仓库添加remote，再把备份数据库fetch/pull到新仓库。


【忽略文件】.gitignore
	新建一个名为.gitignore的文件，注名字不能变，否则Git是不认的
	echo 'disc/' > .gitignore    // disc/ 表示把disc这个目录及里面的所以内容都不纳入git管理
	
	可用 vi .gitignore 打开编辑 添加你想要忽略的文件
例如：
	# 这是忽略的目录
	disc/						//忽略disc这个目录及内容
	node_modules/				//忽略node_modules/这个目录及内容
	
	# 这是忽略的文件
	*.exe
	*.out
	*.app
	
此时：
	git status	就看不到你在.gitignore文件中，忽略的这些目录或文件了，更不会添加到暂存区等等。。。。
	
各种文件、目录、语言的忽略模板，可参照  [GitHub](https://github.com/github/gitignore)

例如：
``` C++
	#这是GitHub中的C++语言的.gitignore文件
	
	# Prerequisites
	*.d

	# Compiled Object files
	*.slo
	*.lo
	*.o
	*.obj

	# Precompiled Headers
	*.gch
	*.pch

	# Compiled Dynamic libraries
	*.so
	*.dylib
	*.dll

	# Fortran module files
	*.mod
	*.smod

	# Compiled Static libraries
	*.lai
	*.la
	*.a
	*.lib

	# Executables
	*.exe
	*.out
	*.app
	*.i*86
	*.x86_64
	*.hex

	# Debug files
	*.dSYM/
	*.su
	*.idb
	*.pdb
```

【删除文件】
	 git rm 文件名
例如：
	 git rm data.json


【恢复文件】
	git reset --hard HEAD
	git reset --hard		//这是命令有点危险 它将把暂存区工作路径上面的所有变更都会被清理掉。









# Git常见问题的处理：
---
#### 【在开发中临时加塞了紧急任务怎么处理】

	1、git stash 	//保存工作目录和索引状态WIP，并恢复到上次提交的状态，
	
注：git stash默认情况缓存以下文件：
     	1、git跟踪的但未添加到暂存区的修改
     	2、添加到暂存区的修改

注：不会缓存以下文件：
      1、在工作目录中的新文件
      2、被忽略的文件
	
	2、git stash list	//查看stash列表 数组行式 stash@{0}，stash@{1}....

	3、git stash apply	//恢复临时存储，保留stash列表
	3、git stash pop	//恢复临时存储，删除stash列表

	4、git stash apply stash@{2} //指定恢复临时存储，保留stash列表  默认时：git stash apply = git stash apply stash@{0}
	4、git stash pop stash@{3} //指定恢复临时存储，删除stash列表


 git worktree add 

---
#### 【解决冲突】 
> **Git合并时遇到冲突或错误后取消合并 **

	1、当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

	2、解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容（就是当两个分支都修改一个文件，并双方都commit后，此时在合并merge时 就会报错，【Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，所以你将不要的代码删除，再 git add 后 git commit 】）就好了。


【或者】：
	1、当合并分支时遇到错误或者冲突，分支旁边会多出“|MERGING”这个东西
		Administrator@MuGuiLin MINGW64 /d/git/test/iditor (test|MERGING)

	2、有这个状态存在时，会导致后面想要再合并的时候提示如下

	3、git merge --abort  //取消这次合并
		
	4、git pull --rebase  //变基


	使用下面的关系区别这两个操作：

	git pull = git fetch + git merge
	git pull --rebase = git fetch + git rebase


	git rebase -skip	//忽略冲突。
	
	注：如果master主分支上有冲突，并且已纪解决了，此时其他分支如test等，要和master主分支保持一至，不然提交到master主分支上又会有冲突。


---
#### 【分离头指针 HEAD detached at .....】 

> 分离头指针： 是指HEAD头没有指向对应任何分支【正常情况下，HEAD头 总是和某个分支绑在一起的】如：git log 结果：commit a2b0cc55fdc09e4e7c2dc26fef871237f009f257 (HEAD -> test)。
	git checkout commitId：会出现分离头指针的情况，这种情况下比较危险，因为这个时候你提交的代码没有和分支对应起来，当切换到其他分支的时候(比如master分支)，容易丢失代码；
	但是分离头指针也有它的应用场景，就是在自己做尝试或者测试的时候可以分离头指针，当尝试完毕没有用的时候可以随时丢弃，但是如果觉得尝试有用，那么可以新建一个分支，使用 git branch <新分支的名称> commitId

> 【问题来源】：
* 在修改变更或创建文件时，一定是在基于某个branch（分支）下进行的，否则就会出现 分离头指针 的情况，这样你在切换分支git ckeckout branchName时，之前所修改变更 或 提交commit后的内容就不会被保存。】

> 例如： 
		1、git log --graph				//显示提交日志
		2、git checkout  ac47b9946759e	//将HEAD指向了一个commit上，此时就是 分离头指针了，因为：此时HEAD是没有指向分支的， 
		
		Administrator@MuGuiLin MINGW64 /e/gitDemo ((ac47b99...))  //查来括号中应该是：（master） 或 (dev) 或(test) 等，它是指向一个具体的分支的，不是指向commit_id的。



> 【解决办法】
* ：在切换分支之前，进行 git branch 新分支名 当前分离头指针】就是将没有和分支关联的commit给保存下来。

> 例如：
    git branch myNewFZ ac47b9946759e 	//将分离头 ac47b9946759e 的commit保存在一个叫myNewFZ的新分支下就好了。
      
如果：
    你没有执行上面的保存分支命令，并且切换到别的分支了，那你在分离头 ac47b9946759e修改的内容就丢失了！！！ 当然你认为分离头 ac47b9946759e的内容没用就没问题，否则问题就玩完了！！！








# Git分支管理
---
#### 【查看分支】

	命令|注释
	----|----
	git branch -l| 						//查看当前在哪个本地分支上
	git branch -lv| 						//查看当前在哪个本地分支上 + 提交信息
	git branch -a| 						//查看所有分支(包括本地和远程)
	git branch -av|						//查看所有分支(包括本地和远程) + 提交信息


---
#### 【创建分支】
		 git checkout -b 分支名			//创建分支
	
	如： git checkout -b test			//这是创建一个名为test的分支。

> 每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。

一开始的时候，master分支是一条线，Git用master指向最新的提交，再用HEAD指向master，就能确定当前分支以及当前分支的提交点：


> 每次提交，master分支都会向前移动一步，这样，随着你不断提交，master分支的线也越来越长


当我们创建新的分支，例如dev时，Git新建了一个指针叫dev，指向master相同的提交，再把HEAD指向dev，就表示当前分支在dev上：
	
	git checkout -b dev	//加上-b参数表示创建并切换

> 不过，从现在开始，对工作区的修改和提交就是针对dev分支了，比如新提交一次后，dev指针往前移动一步，而master指针不变：
	现在的修改就是在dev上了

当修改完成dev分支的工作后，我们就可以切换回master分支：
	git checkout master


假如我们在dev上的工作完成了，就可以把dev合并到master上。Git怎么合并呢？最简单的方法，就是直接把master指向dev的当前提交，就完成了合并：

>	git merge dev					//git merge命令用于合并指定分支到当前分支。
或者：	
	git merge --no-ff -m "合并的描述" dev		//并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

例如：
	git merge --no-ff -m '从master主分支合并到dev分支' master   //将master主分支合并到dev分支


> 合并后，将本地的master同步到远程
	
	git push origin master


就可以看到，master和dev分支的最新提交是完全一样的。

> 学习网址：https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424

---
#### 【删除分支】
	git branch -d 分支名             	//删除分支
	git branch -D 分支名             	//强行删除分支   -d 是删除， -D 是强制删除。
	
例如：
	git branch -D dev
	
注意：
	不能删除当前的分支！！！
	
---
#### 【切换分支】 注：切换分支时 .git/HEAD 会发生变化，用 cat .git/HEAD 命令就可以查看了
	git checkout -b test origin/test	//首次切换到test分支
	git checkout -b master origin/master //首次切换到master 主分支
	git checkout test					//直接切换
	git checkout master



Git鼓励大量使用分支：

	查看分支：git branch
	
	创建分支：git branch <name>

	切换分支：git checkout <name>

	创建+切换分支：git checkout -b <name>

	合并某分支到当前分支：git merge <name>

	删除分支：git branch -d <name>




# 相关查看命令：

#### 【查看提交地址】

	命令|注释
	----|----
	git remote -v						|//查看提交地址
	git remote add origin 提交地址		|//[添加提交地址]，在本地创建的 git init 后为其添加提交地址， 可以 .git目录下的config文件中查看[remote "origin"]项
	git remote set-url origin 提交地址	|//[修改提交地址]， 如果是已经添加的提交地址后，想改变提交地址
	git remote rm origin 				|//[删除提交地址], 


---
#### 【相关查看】注：可以用gitk 命令 以图形化界面展示版本， 或者用 gitk --all

	命令|注释
	----|----
	git config --list|  				//检查配置信息 (按回车向下查看！)
	git status	|						//查看状态（注：只有新增了一个空的文件夹，或是重命名文件时只是改变大小写， 是没有status状态的！！！）
	git log|							//查看当前分支提交历史记录
	git log	--oneline| 					//查看当前分支提交简洁的历史记录
	git log -n3|						//查看当前分支最近3次的提交历史记录 数字可改 如：1 2 3 4 5 6......
	git log --graph|					//查看当前分支提交的历史记录以图形化详细显示
	git log --all --graph|				//查看所有分支提交的历史记录以图形化详细显示
	git log --all -n5 --graph|			//多参数组合使用。 graph图形 
	git log --all --graph 分支名|		//查看指定分支提交的历史记录以图形化详细显示

>	如： git log --all --graph test		//这是查看 test 分支提交的历史记录以图形化详细显示


---
#### 【查看 commit -> tree -> blob】 *提交 -> 树（存的就是目录或文件:html,css,img等） -> 点（存的就是:html,css文件里的内容）【在git 只要内容相同的文件，只有一个点blob】根据哈希值一层一层的向下看*

> cat 哈希值 【注：哈希值在git log 命令后的 commit 后面就是哈希值， 复制长度不定，只要能唯一标识就行】
		git cat-file -t	哈希值			//查看类型
		git cat-file -s 哈希值 			//查看大小
		git cat-file -p 哈希值 			//查看内容
		
```html
	首先如：git log
		结果如下：
			commit a2b0cc55fdc09e4e7c2dc26fef871237f009f257 (HEAD -> test)
			Author: muguilin <“muguilin@foxmail.com>
			Date:   Wed May 8 15:48:34 2019 +0800
				修改public样式文件

			commit ede5c592f6671a08b3f66a16828168f53749bdbd (master)
			Author: muguilin <“muguilin@foxmail.com>
			Date:   Wed May 8 14:30:18 2019 +0800
				添加文件

	
	然后如: git cat-file -p ede5c592f6671a08b3f66
		结果如下：
			040000 tree 22c27110dc712bd6286c3bafbefb3ce353315462    css
			040000 tree ea776a5da02f807cb654cb959e7555b50f63d8cc    img
			100644 blob 30276005913a22a0d2a17954550982dbd4fea8cb    index.html
			100644 blob bb2fed3c907d64c3a7b0295a9a0d4331cc5b7a31    style.css
		
		
	再又如： git cat-file -p 30276005913a22a0d2a17  //这是就是查看上面的index.html中的内容
		结果如下：
			<!doctype html>
			<html>
				<head>
					<meta charset="utf-8">
					<title></title>
					<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
					<link href="css/mui.css" rel="stylesheet" />
				</head>
				<body>
					<script src="js/mui.js"></script>
					<script type="text/javascript">
						mui.init()
					</script>
				</body>
			</html>
```
	

	
---
	
	




# Dos 常用操作：

#### 【Dos 常用操作】 前面不用加 git 

	命令|注释
	----|----
	ipconfig|							//查看网络状态
	Alt + F2|							//打开一个新命令窗口
	Alt + Enter|						//全屏
	Win + ↑→↓← |						//调整窗口位置，按两次箭头全屏切换
	Win + Tab| 							//切换窗口
	exit |								//退出命令工具
	clear|								//清屏
	cls|								//清屏
	pwd|  								//查看当前目录
	ls|  								//查看所有目录和文件
	ls -all|							//查看所有目录和文件(包括隐藏的)
	ll|									//查看所有目录和文件 的列表详情
	ll -all|							//查看所有目录和文件 的列表详情
	dir| 								//同上
	dir -all|							//同上
	du -sh *| 							//查看当前目录所有文件，文件夹 的大小
	du -h								//查看所有文件，文件夹 的大小
	df|									//查看存储空间信息


---
#### 【杀死进程】

	命令|注释
	----|----
	ps					|				//显示所有运行中的进程	
	kill 12345(进程号)	|				//杀死进程
	kill -KILL 123456	|				//强制杀死进程
	kill -9 123456  	|				//彻底杀死进程

---
#### 【新建目录】
	mkdir 目录名


---
#### 【新建文件】
	touch 文件名							//新建一个文件
	vi 文件名							//新建一个文件并进入编辑状态（如果文件已存在，则直接进入编辑状态）
	
	【vi中的操作】 按esc键 输入以下命令
		:w 保存
		:wq! 强制保存退出
		:q 退出
		:qa!强制退出
		
	echo '这是我要写入的内容' > 文件名    //这是向文件中写入内容，注意：写入会覆盖之前源文件中的内容。

	【.wap文件的删除】
		1、vi -r 文件名 根据提示：按 D 删除；
	 	2、打开任务管理器，结束：vim.exe 进程；

---
#### 【重命名目录、文件】
	mv 被修改的目录名或文件名 新的目录名或文件名
如：
	mv style.css base.css				//这是将style.css文件的名字改为base.css
	mv images img						//这是将images目的名字改为img
	
>	【重命名注意】文件夹名/目录名重命名：
		问题原因：在git中要修改文件夹名/目录名时 【改变 大写或小写字母】 不能直接更改，因为直接更改不会记录【不区分大小写字母】 如 mupiao 改为 MuPiao 这两个是相等的，所以在 git add . 时没有记录，可以用 git status查看，
		解决方法：先把要修改文件夹名/目录名 改为其他任意思名字，然后 git add . 再 git commit -m "描述" 之后 再改为你想改的名字，再次 git add . 再 git commit -m "描述" 再 git push 往服务器推送。


---
#### 【复制目录、文件】

	cp 被复制的路径文/件名+后缀名 目标位置/


> **注： **
如果要在目标位置中重新给文件启名字，*直接在目标位置/新文件名+后缀名*

__如：__
	cp style.css public/css         		//这是将当前目录中的style.css文件 复制到 当前目录中的public目录下的css目录中去。
	cp style.css public/css/base.css	//这是将当前目录中的style.css文件 复制到 当前目录中的public目录下的css目录中去 并重新启名为base.css。


#### 【删除目录、文件】
	命令|注释
	----|----
	rm -rf .git     	|				//删除git项目
	rm -r  目录名或文件名	|				//删除指定的目录
	rm -rf 目录名或文件名	|				//删除指定的目录









Administrator@MuGuiLin MINGW64 /d/git/test/iditor (test|MERGING)

#### 【克隆一个项目，添加一个文，完成一次提交】
git clone git@gitlab.smgtech.net:01810597/iDitor.git
cd iDitor
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master


#### 【把现有的项目提交到远程Git仓库】
命令	   |  注释
----|----
cd 目录名|		//进入项目目录
git init|		//初始化git
git remote add origin git@gitlab.smgtech.net:01810597/iDitor.git|	//添加远程仓库地址
git add |		//跟踪提交目录及文件
git commit "描述"|	//添加描述
git push -u origin master	//第一次提交到远程仓库 master 如果没有设置用户名和密码，此时会自动弹出提示框，或输入用户名和密码【密码在输入时是看不见的】

#### 【配置Git 会使用操作系统默认的文本编辑器o为Notepad++】
git config --global core.editor Notepad++


#### 【获取帮助】若你使用 Git 时需要获取帮助，有三种方法可以找到 Git 命令的使用手册：

```javascript
$ git help <verb>
$ git <verb> --help
$ man git-<verb>

例如，要想获得 config 命令的手册，执行
$ git help config
```


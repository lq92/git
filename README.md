# Recorde the knowledge of Git and how to use it
* [Git 介绍](#introduce)
	* [Git的三种状态](#status)
	* [Git的三个工作区域](#work_area)
	* [Git配置](#config)
	* [获取帮助](#help)
* [Git 基础](#base)	
	* [Git 仓库](#repository)
* [Git 文件周期](#lifestyle)	

* ## <h2 id='introduce'>Git 介绍</h2>
	* ### <h3 id='status'>Git的三种状态</h3>
		* 已提交(commited)
			* 表示文件已提交到本地的数据库
		* 已修改(modified)
			* 表示文件已经修改，但是没有暂存
		* 已暂存(staged)
			* 表示文件已暂存，但没提交到本地数据库，包含在下次提交中
	* ### <h3 id='work_area'>Git的三个工作区域</h3>: 
		* 工作目录
			* 此目录保存的是从git仓库中拉取的文件，并用于操作的文件
		* 暂存区域
			* 在工作目录中修改后并暂存文件，会处在暂存区域，git commit就是提交此区域的文件到git仓库中
		* git仓库(这里指本地仓库，下同)
			* 保存项目数据和数据库的地方
		![area](area.jpg)
		#### 在git中工作流程
		1. 在工作目录中修改文件
		2. 将修改的文件放到暂存区域
		```
			git add .(all)/filename
		```
		3. 将暂存的文件提交到git仓库
		```
			git commit -m "commit information"
		```
	* ### <h3 id='config'>Git配置</h3>	
		* #### 配置用户信息
			**git的每次提交都会使用这些信息，且会写入到每一次提交中**
			```
			 git config --global user.name "your name"
			 git config --global user.email "your email"
			```
			**如果配置用户信息使用了--global选项，那么git每次操作都会使用这些信息**
		* #### 配置编辑器
			```
			 git config --global core.editor "editor root path"
			```	
		* #### 查看配置信息
			```
			 git config --list || git config configname(checkout one of the config information )
			```	
			**Windows用户可以在c/user/administrator/.gitconfig中找到配置信息**
	* ### <h3 id='help'>获取帮助</h3>
		```
		 git help <verb>
		 git <verb> --help	
		```
		#### 例如要获得配置的帮助
			git help config || git config --help
* ## <h2 id='base'>Git 基础</h2>
	* ### <h3 id='repository'>Git 仓库</h3>	
		* 在现有项目或目录中导入文件到git中
			* 在一个空的目录中
				```
					git init
				```
				这样就可以初始化一个.git文件夹，这里包含Git仓库所有的必须文件
				![empty](src/base/empty.png)
			* 在有项目的目录中
				```
					git init
				```	
				此时原有目录中的文件是未跟踪的状态
				![has](src/base/has.png)
		* 从服务器克隆一个现有的git仓库	
			```
				git clone <remote respository>
			```	
			![clone](src/base/clone.png)
			<p>此时当前工作目录中会创建一个和远程仓库同名的文件夹，若要指定别名可以使用下面命令</p>
			```
				git clone <remote respository> dirname
			```
* ## <h2 id='lifestyle'>Git 文件周期</h2>
	* **工作目录中的每一个文件只有两个状态：已跟踪、未跟踪**
		* 已跟踪指文件已纳入版本管理，可以是已修改、未修改、已暂存
		* 工作目录中除了已跟踪的文件，其他的都是未跟踪文件
		* 从远程服务器克隆仓库后所包含的文件都是已跟踪文件
		![lifestyle](src/life/lifecycle.jpg)
	* **查看文件状态**
		* 此时表明当前文件夹中的所有文件都是已跟踪未修改文件，且当前分支是master分支
			```
				git status
			```	
			![status_clear](src/status/status_clear)
		* 新建一个文件，此时该文件的状态是未跟踪(untracked)
			![status_untracked](src/status/status_untracked)
			**此时可以使用git add filename || . || dirname命令将该文件纳入跟踪状态**
			<p>git add可以使用文件名或目录路径作为参数，若是目录路径则跟踪该目录下所有的文件</p>
			```
				git add test.txt || .
			```	
			![status_tracked](src/status/status_tracked)
		* 修改已暂存的文件
			![status_modified](src/status/status_modified)	
git的状态可以通过命令行git status查看文件的具体状态(Windows系统下通过cmd查看)	



要先进到该项目目录下，不然会提示 fatal: not a git repository \(or any of the parent directories\): .git



克隆

git.exe clone --progress -v "https://xxx.com/xxx/xxx.git" "E:\git\xxx"

添加文件

	git.exe add .

提交文件

	git.exe commit -m "小测试" -a

切换分支

        缺少分支时候

		git.exe checkout -b xxxx remotes/origin/xxxx

        已有分支

               git.exe checkout xxxx

拉取

	git.exe pull --progress -v --no-rebase "origin"

获取

	git.exe fetch -v --progress "origin"



合并

	develop 合并的分支

		git.exe merge remotes/origin/master

       release 合并的分支

               git.exe merge remotes/origin/xxxx

推送

	git.exe push --progress "origin" xxxx:xxxx


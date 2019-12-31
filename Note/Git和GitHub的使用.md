## Git和GitHub的使用

1. 安装git
2. 打开命令行
3. cd切换到要上传的目录，使用`git init`命令创建 `.git`文件夹
4. `git status`查看当前文件状态
5. `git add index.html`或者`git add --all`把工作区的单个文件或所有文件全部提交到版本区里面的暂存区
6. `git commit -m "类似备注批注"`，命令表示把暂存区的文件提交到本地仓库。
7. `git remote add origin https://github.com/name/name_cangku.git`，表示把你的本地仓库和远程仓库连接起来。
8. `git pull --rebase origin master`，在push之前先同步一下本地仓库与远程仓库的文件。
9. `git push -u origin master`,把本地仓库提交到远程仓库。

**码云同样**


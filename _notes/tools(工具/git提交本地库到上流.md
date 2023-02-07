1. git init  初始化Git可管理的仓库
2. git branch -m main  重命名刚创建的分支，建议用main
3. git remote add origin \*.git   关联本地仓库
4. git push --set-upstream origin main 为推送当前分支并建立与远程上游的跟踪
5. git pull origin main  将远程主机 origin 的 master 分支拉取过来，与本地的分支合并
6. git add .  将所有修改过的工作文件提交暂存区
7. git commit -m ""   提交项目，“”里是注释
8. git push 


tip:  git config --global credential.helper store 可以避免每次都输入密码
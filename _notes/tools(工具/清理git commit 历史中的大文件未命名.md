Step 0：==查看空间占用==
`git count-objects -v ` # 查看 git 相关文件占用的空间
`du -sh .git `# 查看 .git 文件夹占用磁盘空间
Step 1：==找到仓库记录中的大文件==
```
git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -5 | awk '{print$1}')"
```
Step 2：==重写这些大文件涉及到的所有提交==
```
git filter-branch -f --prune-empty --index-filter 'git rm -rf --cached --ignore-unmatch {your-file-name}' --tag-name-filter cat -- --all
```
Step 3：==同步远程仓库==
`git push origin --force --all`

tip:
清理和回收空间
虽然上面我们已经删除了文件, 但是我们的repo里面仍然保留了这些objects, 等待垃圾回收(GC), 所以我们要用命令彻底清除它, 并收回空间，命令如下:
```
rm -rf .git/refs/original/
git reflog expire --expire=now --all
git gc --prune=now
```
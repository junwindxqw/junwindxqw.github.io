用 a 分支创建分支  b

```sh
# 先看下当前所属分支， 带 * 号的就是 
git branch 

# 如果不是 a，则切过去
git checkout a

# 拉取 a 分支最新代码，保证本地为最新
git pull    // 或 git pull origin a

#  创建 b 分支
git checkout -b b    // 切到 b 分支，如果 b不存在，则创建

# 推送新分支 b 到远程
git push -u origin b   // 远程仓库自动生成 b 分支。   -u 将本地分支与远程分支关联（后续直接 git pull ,  git push 即可）

# 查看本地分支
git branch

# 查看远程分支
git branch -r
```

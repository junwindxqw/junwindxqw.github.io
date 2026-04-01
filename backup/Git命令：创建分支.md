从 a_com 分支创建一个新的分支 ： b_com

```shell
# 先看下当前所属分支， 带 * 号的就是 
git branch 

# 如果不是 a_com，则切过去
git checkout a_com

# 拉取 a_com 分支最新代码，保证本地为最新
git pull    // 或 git pull origin hbwx_wyaqpx_com

#  创建 b_com 分支
git checkout -b b_com    // 切到 b_com 分支，如果 b_com 不存在，则创建这个分支

# 推送新分支 b_com 到远程
git push -u origin b_com   // 远程仓库自动生成 b_com 分支。   -u 将本地分支与远程分支关联（后续直接 git pull ,  git push 即可）

# 查看本地分支
git branch

# 查看远程分支
git branch -r
```

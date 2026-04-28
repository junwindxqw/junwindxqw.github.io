> 点击链接查看和 Kimi 的对话 https://www.kimi.com/share/19dd1fa8-2442-864f-8000-000087490983

经常遇到的问题：
1. 在服务器中修改了项目的文件权限 -> 导致文件发生变更，需要提交，其实文件内容没有任何变化。 
2. 将win的项目提交到服务器中 -> 因为换行符不一致，导致文件发生变更，需要提交，其实文件内容没有任何变化。 

解决：

忽略文件权限变化
```
# 全局配置（推荐）
git config --global core.filemode false

# 当前仓库（也要执行）
git config --local core.filemode false

# 仅当前仓库配置
git config core.filemode false
```
如果已经提交了权限变更，想撤销
```
# 重置所有文件的权限变更（保留内容变更）
git diff -p -R --no-color | grep -E "^(diff|--git|+++|---)" | grep -v "old mode" | git apply

# 或者更简单地，直接重置暂存区
git reset --hard HEAD  # 注意：这会丢弃所有未提交的变更    git restore .
```

换行符不一致（LF vs CRLF）
- Windows：默认使用 CRLF（\r\n）
- Linux/macOS：默认使用 LF（\n）

推荐方案：仓库统一使用 LF
```
# 提交时自动将 CRLF 转为 LF，检出时不转换（适合服务器/Linux 环境）
git config --global core.autocrlf input

# 提交时自动将 CRLF 转为 LF，检出时自动转为 CRLF（适合 Windows 开发）
git config --global core.autocrlf true
```

更优雅的方案：使用 .gitattributes（推荐，团队协作必备）
在项目根目录创建 .gitattributes 文件，强制统一换行符：
```
# 自动处理换行符
* text=auto eol=lf

# 特定文件类型强制使用 LF
*.js text eol=lf
*.ts text eol=lf
*.json text eol=lf
*.css text eol=lf
*.html text eol=lf
*.md text eol=lf
*.sh text eol=lf
*.py text eol=lf

# 二进制文件不处理换行符
*.png binary
*.jpg binary
*.gif binary
*.ico binary
*.pdf binary
*.zip binary
*.exe binary
```
然后执行：
```
# 刷新 Git 的属性处理，重新规范化所有文件
git add --renormalize .
git commit -m "Normalize line endings to LF"
```

如果已经存在换行符混乱，想批量修复
```
# 安装 dos2unix 工具
# Ubuntu/Debian
sudo apt-get install dos2unix

# macOS
brew install dos2unix

# 批量转换项目中的所有文本文件
find . -type f -not -path "./.git/*" -exec dos2unix {} \;
```
使用 nvm 

先卸载干净之前安装的 node，安装 nvm

```
nvm install xx.xx.xx

nvm list

nvm use xx.xx.xx

node -v
npm -v
```

如果无法使用 nvm install 安装某个版本，我们可以手动安装，比如手动安装 14.21.3 

1.  下载 https://nodejs.org/dist/v14.21.3/ ， node-v14.21.3-win-x64.zip
2.  找到 nvm 的安装目录，nvm root
3.  在 nvm 目录下新建文件夹 v14.21.3（严格对应版本号）；  
4. 将下载的压缩包解压到 v14.21.3 文件夹内（确保解压后能直接看到 node.exe（Windows）或 bin 目录（macOS/Linux））。  
5. 然后切换到 14.21.3 验证

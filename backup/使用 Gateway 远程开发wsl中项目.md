安装 Toolbox -》 安装 Gateway 

使用wsl，连接到wsl中的项目， 首次会自动在服务器中安装 IDE server

然后在本地中打开一个轻量的 client。

好处： 开发环境，插件全在 Linux 中。

比如，我直接本地phpstorm使用原生模式打开wsl项目， 如果clade code安装在wsl内， 则本地phpstorm中打开claude，使用 /ide 是无法找到并连接到phpstorm的。则无法使用插件的一个快速发送代码到上下文的功能。
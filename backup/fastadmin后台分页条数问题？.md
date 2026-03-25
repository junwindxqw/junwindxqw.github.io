fastadmin管理后台，我把某一个页面的，每页显示条数调整为500条。 

然后切换到其它页面，发现默认都是500条了。

这种会导致一个问题： 某个页面的查询本来就很卡时，一下子查询太多条数据，会导致请求卡死。拖死MySQL连接，拖死php-fpm进程。

我检查了原因，在cookie中没有找到，发现是用了 localStorage 保存了每页条数。然后请求时，localStorage 中的 pagesize 会赋值给 limit 参数。

<img width="589" height="389" alt="Image" src="https://github.com/user-attachments/assets/284b9fa2-8c56-4a09-a79c-59fd417dafd7" />
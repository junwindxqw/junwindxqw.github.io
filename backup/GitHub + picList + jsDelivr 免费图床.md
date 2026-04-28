> https://linux.do/t/topic/1200827
> https://linux.do/t/topic/165821
> 仓库不要超过1G，可以继续加仓库解决
> 建议个人博客类的，低频使用，否则容易被封。


1. 创建一个public仓库
2. 创建一个token，picList中会用到（用来访问GitHub的）

   setting -> Developer settings 

   ![](http://fastly.jsdelivr.net/gh/junwinds/xqw-img/posts/20260428111631042.png)

​    我将`token`名称设为`PicList`，有效期设置为永久，勾选`Repo`给予该`token`读写仓库权限

​    此`token`仅可在生成式查看一次，请及时保存

3. 安装 piclist   https://github.com/Kuingsmile/PicList/releases

4. 图床配置

   ![image-20260428112504517](http://fastly.jsdelivr.net/gh/junwinds/xqw-img/posts/20260428112504678.png)

![image-20260428112535478](http://fastly.jsdelivr.net/gh/junwinds/xqw-img/posts/20260428112535544.png)

5. jsDelivr 加速 cdn

   第一种是不使用`jsDelivr`加速的，上传下载速度会受网络环境的影响

   ```shell
   https://raw.githubusercontent.com/B-LIPSTICK/Image-Hosting-Service/main    // 或者不填留空就行
   ```

   第二种是使用`jsDelivr`全球CDN加速，适合中国大陆用户快速访问

   ```shell
   https://cdn.jsdelivr.net/gh/B-LIPSTICK/Image-Hosting-Service@main
   ```


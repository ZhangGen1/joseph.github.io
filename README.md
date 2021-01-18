# 安装依赖
> `npm install`

# 生成博客网页文件
> `hexo g`

# 本地查看博客效果
> `hexo s`

# 上传文件到GitHub
> `hexo d`


# 写文章、发布文章

- 1.安装一个依赖
    `npm i hexo-deployer-git`
- 2.新建一篇文章
    `hexo new post "文章名称"`
- 3.文件夹.md文件
    `\source\_posts`目录下会多一个文件夹和.md文件，一个用来存放你的图片等数据，另一个就是你的文章文件啦。
- 4.编写完markdown文件后，根目录下输入hexo g生成静态网页，然后输入hexo s可以本地预览效果，最后输入hexo d上传到github上。这时打开你的github.io主页就能看到发布的文章啦
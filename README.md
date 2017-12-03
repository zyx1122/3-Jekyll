# zyx の部落格

访问请移步[zyx1122.github.io](https://zyx1122.github.io/)


## Fork说明

 *原作请至 [https://github.com/P233/3-Jekyll](https://github.com/P233/3-Jekyll)


## 使用

#### 设置 > `/_config.yml`

`_config.yml` 文件用来进行基本的网站信息,包括:_作者信息_、_站点信息_、_阅读处理_、_服务器选项_、_默认模版_、_侧边栏过滤器_、_输出url_、_评论_、_google analytics 设置_ 和 _Build settings_，可依据各注释项进行个性化修改。
`_config.yml` 除基本的站点设置外，新加入了社交链接与评论设置。将需要添加的社交帐号填入对应设置，并取消注释，会在头像下方增加一条社交帐号的链接。支持 Twitter, Weibo, Github, Codepen 以及 Dribbble。此外，填入 Disqus 的 shortname 也会启用 Disqus 评论。 `filter` 选项选择使用 `tag` 或 `category` 作为文章分类。

#### 样式 >　`/css/main.sass`

样式相关的 Sass 变量都存储在 `/css/main.sass` 文件中，修改这个文件可以满足大部分样式定制的需求。建议首先修改 `$gradient-start` 与 `$gradient-end` 两个变量，给自己的博客使用独一无二的侧边栏背景；
其他部分样式文件在`/_sass`文件夹内。

#### 文章 > `/_post`
按照 _yyyy-mm-dd-name.md_ 命名的文件会显示在侧边栏中；`/index.md`文件为主页默认展示内容。
[markdown语法说明](https://github.com/GiantZero-x/GiantZero-x.github.io/blob/master/_posts/document/2017-02-07-markdown-direction.md)

#### 资源 >　`/_assets`
站内的图片、音频、视频等静态资源可存储在这里。

#### 替换图片

请不要忘记替换 `/assets/img/` 内的图片。`avatar.jpg` 是侧边栏头像的图片，`qrcode.jpg` 会在提示浏览器不兼容时使用。[QR Code 生成器](https://www.unitag.io/qrcode)

#### 其他
`/_includes`文件夹内为页面公用模版文件,`/_layouts`文件夹内为文章布局模版文件,`/_sass-cache`和`/_site`文件夹(若有)内为缓存文件,不需理会；
部分功能，如：评论、google analytics、社交账号等功能需另外注册或开启相关服务，使用过程中需注意。



## 针对旧版的改进

* 侧边栏使用 Tag 或 Category 做为文章分类，默认 Tag。
* 自动生成侧边栏分类标签，基本不需要修改模板文件。但标签顺序由 Jekyll 根据时间顺序生成，需要手动调整顺序只能修改 `_includes/sidebar.html`，格式是 `<li class="sidebar-tag" data-filter="TAG">TAG</li>`，替换 `TAG`，大小写敏感。
* 更加全面的 Sass 变量，方便个性化主题样式。
* 暂定取消文章的标题目录。
* 取消了嵌入 Codepen。
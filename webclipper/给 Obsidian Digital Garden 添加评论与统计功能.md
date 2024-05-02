---  
title: 给 Obsidian Digital Garden 添加评论与统计功能  
summary:   
author:  
  - 雨天狂奔  
dg-publish: true  
dg-home:   
dg-pinned:   
dg-permalink: share  
dg-note-icon: "2"  
tags:  
  - obsidian  
  - 数字花园  
  - 扩展功能  
  - 博客  
dg-update: 2024-05-02T20:36:00  
share: true  
---  
  
## 评论系统的选择  
  
在之前写的《[利用Obsidian搭建自己的Digital Garden](https://blog.rahc.top/article/tech-share-mydigitalgarden.html)》中已经详细阐述了自己数字花园搭建的流程。数字花园的实现过程是采用了oleeskild开源的插件[obsidian-digital-garden](https://github.com/oleeskild/obsidian-digital-garden)。关于评论系统在它的[官方文档](https://dg-docs.ole.dev/advanced/guides-and-how-tos/adding-comments/)中，推荐了3种方案，分别是[giscus](https://giscus.app/zh-CN)、[utterances](https://utteranc.es/)和[disqus](https://disqus.com/)。前两种评论都依赖于github账号，考虑到目前数字花园的笔记主要是后端开发和人工智能，受众是程序员，基本上都有github账号，所以选择了giscus进行配置和部署。  
  
### giscus评论系统  
  
giscus是基于Github Discussions实现的评论系统，受utterances的启发。它会使用Github Discussions搜索API来搜索当前页面对应的discussions，即对于当前页面的评论。  
  
1. 在github创建新仓库。  
  
![](https://pic4.zhimg.com/80/v2-8177b83e8b8c4becda9e4e003ef9c6df_720w.webp)  
  
2. 在新建的仓库的settings->general->Discussions ，中打开Discussions功能。  
  
![](https://pic4.zhimg.com/80/v2-e79fd557cc20d5d935a8f1f9a7f965b3_720w.webp)  
  
3. 点击该链接：[https://github.com/apps/giscus](https://github.com/apps/giscus)，在github安装giscus插件。  
  
4. 点击该链接：[https://giscus.app/zh-CN](https://giscus.app/zh-CN)，对giscus进行配置，把giscus关联到步骤1创建的新仓库  
  
![](https://pic1.zhimg.com/80/v2-bdfa6bcdbdb5b5ede0c7f180be83814c_720w.webp)  
  
5. 复制以下代码，等待后续步骤的使用。  
  
![](https://pic4.zhimg.com/80/v2-8de69b5ebb57e0f49fa2e416f25f883b_720w.webp)  
  
6. 配置数字花园仓库  
  在`src/site/_includes/components/user` 目录下，我们可以给自己的数字花园添加自定义的组件。由于我们是给我们的每篇笔记页面都添加一个评论，所以在该目录下新建`notes/footer` 目录，在该目录下添加如下文件`001-comment.njk` ，文件名除了扩展名`.njk` 外，名字可以随意。文件内容为步骤5中的内容。  
```js  
<script src="https://giscus.app/client.js"  
 data-repo="github用户名/步骤1创建的仓库名"  
 data-repo-id="你的date-repo-id"  
 data-category="Announcements"  
 data-category-id="你的data-category-id"  
 data-mapping="pathname"  
 data-strict="0"  
 data-reactions-enabled="1"  
 data-emit-metadata="0"  
 data-input-position="bottom"  
 data-theme="preferred_color_scheme"  
 data-lang="zh-CN"  
 crossorigin="anonymous"  
 async>  
</script>  
```  
  
7. 修改页面布局。编辑`src/_includes/layouts/note.njk` 文件。 默认的布局是如图所示，分为左、中、右：  
  
![](https://pic3.zhimg.com/80/v2-9364b719097115ba2b1ca944a32cbd3e_720w.webp)  
  
如果不修改，它会在最底层生成一个横跨左、中、右的一个评论区域，影响美观。而我只是想在中间的底部，加上一个评论区域。在`note.njk` 文件的`<main>...</main>` 之间添加如下代码：  
  
```text  
<main>  
 // 底部添加如下代码  
 {% for imp in dynamics.notes.footer %}  
   {% include imp %}  
  {% endfor %}  
</main>  
```  
  
注释掉main之后，body内相同的代码：  
```text  
<body>  
 {# {% for imp in dynamics.notes.footer %}  
   {% include imp %}  
  {% endfor %} #}  
  {%include "components/lucideIcons.njk"%}  
</body>  
```  
  
现在的布局如图所示：  
![](https://pic4.zhimg.com/80/v2-3c22b7b51100050e1b5ad57394f0645b_720w.webp)  
  
8. 最终的效果如图所示：  
  
![](https://pic3.zhimg.com/80/v2-17d7e8aba9e3306d4c50e82e43431042_720w.webp)  
  
    
最后，欢迎您到[我的数字花园](https://garden.rahc.top/)逛逛，一起进步成长，学有所成。  
  
## 统计功能  
  
### 谷歌统计  
  
统计功能是通过 [Google Analytics](https://tagmanager.google.com/?hl=zh-cn#/home) 实现，同样也是参考 [issue](https://github.com/oleeskild/obsidian-digital-garden/discussions/195) 实现的。注册 Google Analytics，会生成一段 JS 代码，再把代码插入到博客的 head 里即可。  
  
对于 ODG，插入位置是：`src/site/_includes/components/user/index/head`。  
  
![Pasted image 20240324183343](https://github.com/Yunz93/PicRepo/raw/main/image/ODG.png)  
  
重新部署完成后，在 Google Analytics 侧测试下博客域名地址，通过即说明安装完成。  
  
然后就可以在报告页看到网站的流量统计数据了。  
  
![Pasted image 20240324183837](https://github.com/Yunz93/PicRepo/raw/main/image/Google%E5%88%86%E6%9E%90%E6%8A%A5%E5%91%8A%E9%A1%B5.png)
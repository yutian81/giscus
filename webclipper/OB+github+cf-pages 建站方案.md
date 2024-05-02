---  
title: OB+github+cf-pages 建站方案  
subtitle: 完全免费的建站方案，无需服务器，无需写代码  
summary: 完全免费的建站方案，无需服务器，无需写代码  
author:  
  - 雨天狂奔  
dg-publish: true  
dg-home: false  
category: share  
tags:  
  - obsidian  
  - github  
  - cloudflare  
  - 建站  
  - 数字花园  
dg-update: 2024-05-02T20:39:00  
share: true  
---  
## 引言  
  
能读到这篇文章说明你对Obsidian有一定了解了，双链笔记的特性已经不用赘述。该文档介绍了如何通过GitHub私有库和Cloudflare的Pages服务资源实现完美的一键发布的方法。  
  
### 能力要求  
  
1. 该方案需要懂一点点GitHub的操作  
2. 本文假定如果用户需要自定义域名,那么用户应具有添加域名解析CNAME的能力,相关知识不再赘述  
  
### 使用插件  
  
数字花园 [Digital Garden](https://github.com/oleeskild/obsidian-digital-garden#-obsidian-digital-garden)  
  
### 第三方服务  
  
[https://github.com/](https://github.com/)  
  
[https://cloudflare.com/](https://cloudflare.com/)  
  
### 参考文章  
  
[Obsidian 简明发布方式](https://forum-zh.obsidian.md/t/topic/19256)  
  
[obsidian 目前最完美的免费发布方案 - 渐进式教程](https://garden.oldwinter.top/Calendar/%E5%B7%B2%E5%8F%91%E5%B8%83%E6%96%87%E7%AB%A0/obsidian-%E7%9B%AE%E5%89%8D%E6%9C%80%E5%AE%8C%E7%BE%8E%E7%9A%84%E5%85%8D%E8%B4%B9%E5%8F%91%E5%B8%83%E6%96%B9%E6%A1%88---%E6%B8%90%E8%BF%9B%E5%BC%8F%E6%95%99%E7%A8%8B)  
  
## 参考方案和对比  
  
|功能点和限制|数字花园(digitalgarden)方案|jekyll方案1|官方收费发布方案|hugo方案(quartz)|logseq方案|  
|---|---|---|---|---|---|  
|反向链接面板|支持|支持|支持|支持|支持|  
|正向链接预览|支持|支持|支持|支持|支持|  
|支持搜索|支持|不支持，但通过google间接实现|支持|支持，但中文不兼容|支持|  
|链接稳定性|支持|只要文件名不改，链接就稳定|受文件夹和文件名同时影响|只要文件名不改，链接就稳定|只要文件名不改，链接就稳定|  
|文件夹层级显示|支持|无|支持|无|无|  
|首屏加载速度|中等，5秒内,下载资源<4M|极快，2s内，下载资源<1M|中等，5秒内，下载资源<5M|极快，2s内，下载资源<1M|超慢，10秒，下载资源<30M|  
|图谱显示|支持|支持全局图谱，但1K+笔记就很卡|完美支持|支持局部图谱，中文支持不友好|支持，稍卡|  
|横向卷动布局|不支持|不支持|支持|不支持|不支持|  
|暗色模式支持|支持|不支持|支持|支持||  
|移动端支持|支持|支持|支持|支持|支持|  
|markdown扩展语法支持|只支持基本md语法和`[[`语法|只支持基本md语法和`[[`语法|支持obsidian的callout和别名语法|只支持基本md语法|只支持基本md语法和`[[`语法|  
|其他限制|免费|必须要有YAML区|收费|必须要有YAML区；不支持`[[`wikilink格式，需妥协||  
  
## 实施方法  
  
### 安装插件  
  
##### 插件市场安装  
  
在插件市场搜索 digital garden 安装  
  
##### 手动安装  
  
如果没有科学上网可以在[Github](https://github.com/oleeskild/obsidian-digital-garden/releases)上下载zip包到本地解压    
把digitalgarden文件夹放入你的库文件夹下的.obsidian/plugins路径下    
比如我的库名是 _test_ ,那么插件文件夹路径就是_test/.obsidian/plugins/digitalgarden_    
正常情况下digitalgarden下有  
  
- main.js  
- manifest-beta.json  
- manifest.json  
- styles.css    
    等你配置好了以后会有data.json文件夹保存你的配置 这些都不用手动干涉  
  
### 克隆库  
  
1. 首先fork仓库 [https://github.com/oleeskild/digitalgarden](https://github.com/oleeskild/digitalgarden)  
2. 然后设置仓库为private  
  
### CloudFlare 构建配置  
  
1. 进入控制台 选择左侧目录 _Workers 和 Pages_  
2. 选择 _创建应用程序_  
3. tab中选择_Pages_  
4. 点击连接到git  
5. 授权github权限  
6. 点击 _从您的帐户部署站点_  
7. 选择github 账户 并选择之前fork的仓库 _digitalgarden_  
8. 点击开始设置  
9. 预设类型留空 构建命令 _npm run build_ 构建输出目录 _dist_  
10. 点击开始  
  
### 域名绑定  
  
1. 返回CloudFlare控制台,_Workers 和 Pages_面板的Workers模块中 点击你创建的 Pages  
2. tab中选择自定义域  
3. 设定 填入你想好的域名 下一步  
4. 选择_我的 DNS 提供商_  
5. 开始CNAME设置,这里会莫名其妙出错  
    1. 不管他返回控制台  
    2. 再来到这里的域名设置会看到新增的一条是停用状态  
    3. 点击展开 获取目标值 xxx.pages.dev  
6. 去你的dns服务商 把该域名增加cname  
7. 返回第5部位置 点击检查dns记录 需要稍微等待一下 等待成功后下一步  
  
### 插件配置  
  
1. 点击[https://github.com/settings/tokens/new?scopes=repo](https://github.com/settings/tokens/new?scopes=repo) 新建一个令牌  
2. 复制 令牌填充到GIthub token这栏  
3. Github repo name 那一栏填你 克隆的库名  
4. Github Username 填你的Github用户名称  
5. 下面的Base URL填你的域名 包含子域名 不带协议  
6. Slugify Note URL 置空 否则中文路径出错  
7. Features这里配置页面出现的内容  
8. Appearance这里控制站点的名称 主题样式 语言 图标等  
9. 关闭后自动保存  
  
### 尝试发布  
  
1. 写一个新文档  
2. 添加文档属性 可以通过快捷键⌘(ctrl)+p唤出快捷栏，输入tag，选中 _Digital Garden: Add publish flag_，然后文章头部出现文档属性  
3. ⌘(ctrl)+p 然后输入_publish single Note_ 回车即可看到提示栏信息发布状态  
4. 返回CloudFlare控制台,_Workers 和 Pages_面板的Workers模块中 点击你创建的 Pages 查看构建状态等待完成 如果有错误 查看报错信息  
5. 去自己的域名看看发布效果  
6. 左侧的工具栏有个按钮 可控制批量更新发布  
  
### 其他  
  
1. 网站样式、风格和标题等在插件的配置里有详细说明，可以参考[插件文档](https://dg-docs.ole.dev/getting-started/04-appearance-settings/)。  
2. GitHub账户务必做好隐私保护，将库设为 _private_ 并限制好CloudFlare授权的库，最好不要选择全部授权。  
3. 图床使用GitHub和Cloudflare，无需繁琐的额外配置，相当于白嫖了。  
4. 注意标记添加文档属性 _dg-home_ 为 ==首页==，可以通过快捷键⌘(ctrl)+p唤出快捷栏，输入tag，选中 _Digital Garden: Add publish flag_，然后文章头部出现文档属性，添加 _dg-home_，选则属性类型为复选框，然后选中即可设置当前页为首页。注意不要重复设置首页，发布构建会报错。  
5. 为什么不选择教程中的方法呢？因为 [Vercel](https://vercel.com/dashboard) 和 [Netlify](https://app.netlify.com/) 在大陆地区的访问都有点麻烦，而且速度慢。Vercel即使CNAME指向中国也是访问很慢，而Netlify则可能莫名其妙封禁用户。因此，我探索了CloudFlare方案。  
6. 每次发布构建GitHub都发邮件好烦怎么办？将GitHub的库 _watch_ 改为 _ignore_ 即可忽略邮件。但是这样你也会错过发布失败的提示，考虑到发布半分钟后你可能回去页面刷新预览，也不是不能接受。  
  
## 总结  
  
1. Cloudflare免费资源有上限，但一般情况下个人很难用完。这个资源和workers是共享的,注意有workers大量需求的用户,观察资源的余量  
2. 最后，我个人强烈建议新手看下obsidian社区`软通达`大佬的 [建议](https://publish.obsidian.md/chinesehelp/01+2021%E6%96%B0%E6%95%99%E7%A8%8B/%E6%9C%AC%E4%BA%BA%E5%AF%B9obsidian%E6%96%B0%E6%89%8B%E7%9A%84%E5%BB%BA%E8%AE%AE%EF%BC%882022%E7%89%88%E6%9C%AC%EF%BC%89+by+%E8%BD%AF%E9%80%9A%E8%BE%BE#%E4%B8%8D%E5%BB%BA%E8%AE%AE%E4%BD%A0%E7%AB%8B%E5%88%BB%E5%81%9A%E7%9A%84%E4%BA%8B%E6%83%85) ，那就是不要做那些花里胡哨的东西，笔记的本质是记录和总结。  
3. 作者主页  
    1. [类星体](https://blog.186886996.xyz/)  
    2. [掘金](https://juejin.cn/user/2506542241561223/posts)  
    3. [语雀](https://www.yuque.com/u488064)  
    4. [什么值得买](https://zhiyou.smzdm.com/member/4478692379/article/)  
    5. [bilibili](https://space.bilibili.com/1499065/article)
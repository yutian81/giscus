---  
title: Obsidian 笔记的特殊语法  
summary:   
author:  
  - 雨天狂奔  
dg-publish: true  
dg-home:   
dg-pinned:   
dg-permalink: share  
tags:  
  - obsidian  
  - MD语法  
  - 双向链接  
dg-update: 2024-05-02T20:38:00  
share: true  
---  
  
##  维基链接  
  
像往常一样在 Obisidan 中使用语法 `[[Wikilink]]` 进行链接  
  
###  标题链接  
  
链接到特定标头的工作方式与在 Obsidian 中的工作方式相同    
`[[My Note#Note header]]`  
  
###  阻止链接  
  
链接到特定块的工作方式与在 Obsidian 中相同    
`[[My Note#^123abc]]`  
  
###  自定义链接名称  
  
更改维基链接的显示文本的工作方式与黑曜石相同    
![CleanShot 2023-01-10 at 18.07.56@2x.png|250](https://dg-docs.ole.dev/img/user/img/CleanShot%202023-01-10%20at%2018.07.56@2x.png)  
  
---  
  
##  代码块  
  
![CleanShot 2022-11-13 at 15.34.22@2x.png](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-11-13%20at%2015.34.22@2x.png)  
  
```javascript  
let a = 5;  
```  
  
![CleanShot 2022-11-13 at 15.34.59@2x.png|200](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-11-13%20at%2015.34.59@2x.png)    
`Some inline code`  
  
---  
  
##  数据视图查询  
  
```(dataview)  
list from "Advanced"  
```  
  
- [添加自定义组件](https://dg-docs.ole.dev/advanced/adding-custom-components/)  
-  [CSS 定制](https://dg-docs.ole.dev/advanced/css-customization/)  
- [配置生成管道](https://dg-docs.ole.dev/advanced/configure-build-pipeline/)  
-  [内容定制](https://dg-docs.ole.dev/advanced/content-customization/)  
- [细粒度访问令牌](https://dg-docs.ole.dev/advanced/fine-grained-access-token/)  
-  [数据视图查询](https://dg-docs.ole.dev/advanced/dataview-queries/)  
-  [注意特定设置](https://dg-docs.ole.dev/advanced/note-specific-settings/)  
- [与其他解决方案的比较](https://dg-docs.ole.dev/advanced/comparison-to-other-solutions/)  
-  [托管替代方案](https://dg-docs.ole.dev/advanced/hosting-alternatives/)  
-  [路线图](https://dg-docs.ole.dev/advanced/roadmap/)  
-  [技巧和窍门](https://dg-docs.ole.dev/advanced/tips-and-tricks/)  
-  [添加注释](https://dg-docs.ole.dev/advanced/guides-and-how-tos/adding-comments/)  
-  [添加分析](https://dg-docs.ole.dev/advanced/guides-and-how-tos/adding-analytics/)  
  
{ .block-语言-数据视图}    
    
有关数据视图的更多详细信息，请参阅：数据视图查询  
  
---  
  
##  标注  
  
```  
> [!NOTE] Note title  
> Information  
```  
  
 注释标题    
  
 信息  
  
```  
> [!WARNING] A warning  
> This is a warning  
```  
  
 警告    
  
这是一个警告  
  
###  折叠标注  
  
```  
> [!NOTE]+ Open by default  
> Folding/Collapsable callout  
```  
  
 默认打开    
  
折叠/可折叠标注  
  
```  
> [!FAQ]- Closed by default  
> Folding/Collapsable callout  
```  
  
 默认关闭    
  
###  嵌套标注  
  
```  
> [!TIP] Nested callouts  
> Text inside the tip callout  
> > [!EXAMPLE] Inner callout  
> > Multiple nesting layers  
> > > [!TODO] Inner inner callout  
```  
  
 嵌套标注    
  
提示标注内的文字  
  
 内部标注    
  
 多个嵌套层  
  
 内部内部标注  
  
---  
  
## MathJax / LaTex  
  
 [MathJax 参考](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)  
  
```  
$$\frac{1}{0} = \infty$$  
```  
  
10=∞  
  
---  
  
##  标签  
  
单击下面的标签可查看具有相同标签的其他页面。  
  
#exampletag  
  
---  
  
## 嵌入/嵌入图像  
  
![CleanShot 2022-11-13 at 14.24.21@2x.png|250](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-11-13%20at%2014.24.21@2x.png)  
  
![obsidianlogo.png](https://dg-docs.ole.dev/img/user/img/obsidianlogo.png)  
  
##  包含的文档  
  
###  整个文件  
  
![CleanShot 2022-11-13 at 14.24.50@2x.png|250](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-11-13%20at%2014.24.50@2x.png)  
  
[](https://dg-docs.ole.dev/example-pages/transcluded-document/)  
  
这是一个包含的注释。  
  
这是包含的文档中的一个块  
  
### 这是一个标题  
  
 内容  
  
#### 这是一个副标题  
  
###  标头块  
  
![CleanShot 2023-01-05 at 17.22.10.png](https://dg-docs.ole.dev/img/user/img/CleanShot%202023-01-05%20at%2017.22.10.png)  
  
[](https://dg-docs.ole.dev/example-pages/transcluded-document/#this-is-a-header)  
  
### 这是一个标题  
  
 内容  
  
#### 这是一个副标题  
  
###  单块  
  
![CleanShot 2023-01-05 at 17.22.27.png](https://dg-docs.ole.dev/img/user/img/CleanShot%202023-01-05%20at%2017.22.27.png)  
  
[](https://dg-docs.ole.dev/example-pages/transcluded-document/#02502a)  
  
这是包含的文档中的一个块  
  
还值得注意的是，嵌入不需要 dg-publish 属性。它们的行为与图像相同。如果您将某些内容嵌入到文档中，并发布该文档，则其中包含的所有内容都将像该注释的一部分一样发布。  
  
（有关嵌入的更多详细信息可以在这里阅读：内容定制#Tranclusions ）  
  
---  
  
##  神剑  
  
![CleanShot 2022-11-13 at 14.25.34@2x.png|350](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-11-13%20at%2014.25.34@2x.png)  
  
 信息  
  
目前不支持黑曜石特定功能，例如链接到图形中的其他注释  
  
---  
  
##  美人鱼图  
  
![CleanShot 2022-11-13 at 14.26.47@2x.png](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-11-13%20at%2014.26.47@2x.png)  
  
![CleanShot 2022-11-13 at 14.27.14@2x.png](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-11-13%20at%2014.27.14@2x.png)  
  
2014-01-052014-01-122014-01-192014-01-262014-02-022014-02-092014-02-16A taskTask in secanother taskAnother taskSectionAnotherA Gantt Diagram  
  
---  
  
##  PlantUML 图  
  
![uml diagram](https://www.plantuml.com/plantuml/svg/jLHTRzem57tthxWAhnjBCsWx52AwJdkRLAsR-a1vkCGtmIAn8zk8TjF--wuXq9HHrZqiaHBhVfvphks9ysZzggx4PB_oobS4jwRmQxIyU7IUQdWBrqPxL9gi4wAYmeCtO5Mvy22LfTmheuLmIwKRj5Z3Jm7W5YZDMkaI2gmSiGMjDUlFNEbM_I0uYzaagS1LvR_HWx-gLAbhqXvo_f1bxzfYSwUaNq0IX-WQ7xwGSrXIMo4MluHOA4d0E2qP_zXG5qU0XhgiA4rtdBQK-f_GunmTPTa6x4VCbwKrAoslJMKiz0RlBwKSiYVWRMt5vWdHnagohJMXy-H3Y6pJBQl4U1dP4uw6XJCwJRyxiYzrZ2y7oSNyDHtZOKB3ysSDNYPwH_EhfgbKZc58_vEksBA4Q3mEFEzrwdXAexCuczviFBFqNR1a4UoLG0TXnRcCYESAqS7UkzVJ0yiif3ydsR9wakDcMwq3_4XARx1vZYNkLJYH5YJOgHuuiz3GKRfBVtzwkWhyRKuipScGm_wx7VslZJiduS-MEsSORnWKzAUzYpYyR_n2vKlDnt6SpFhPQQmmWYZDWw2ZDZtZQYuIfxDUsso7yaYRhuJIGM5D3QWbtoZAa-FRAn8Jqd9p-Mt_lm40)  
  
---  
  
##  突出显示的文本  
  
![CleanShot 2022-12-12 at 16.14.14@2x.png](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-12-12%20at%2016.14.14@2x.png)  
  
==以下是一些突出显示的文本==  
  
---  
  
##  脚注  
  
```markdown  
There is a footnote here [^1]  
```  
  
这里 [1](1.md)(https://dg-docs.ole.dev/features/#fn1) 有一个脚注  
  
---  
  
##  复选框  
  
```markdown  
- [ ] Uncheckd  
- [x] Checked  
```  
  
- [ ]  未选中  
- [x]  检查  
  
---  
  
##  网站地图  
  
该网站会自动生成一个sitemap.xml文件，可在您的网站上找到 `/sitemap.xml` 。这有助于搜索引擎正确地索引您的网站，使其更容易被发现。为了使站点地图正确格式化为所有页面的完整 URL，插件需要知道您网站的基本 URL。通过将您的 URL 添加到插件设置中，应使用该值自动生成站点地图。  
  
![CleanShot 2022-12-15 at 22.00.24@2x.png](https://dg-docs.ole.dev/img/user/img/CleanShot%202022-12-15%20at%2022.00.24@2x.png)  
  
---  
  
##  Atom/RSS 源  
  
该站点会自动生成 `/feed.xml` 一个 Atom/RSS 源，可在您的站点上使用。为了生成此内容，您需要在设置中添加基本 URL，如上图所示。    
    
要使日期正常工作，您需要在插件的外观设置下启用显示更新的时间戳设置。如果未启用此功能，则 Feed 将使用上次构建网站的日期，这实际上意味着您上次向网站发布任何内容的最后日期。  
  
---  
  
##  脚注来源  
  
```markdown  
[^1]: Here are some extra information in a footnote  
```  
  
---  
  
1. 以下是脚注↩中的一些额外信息︎
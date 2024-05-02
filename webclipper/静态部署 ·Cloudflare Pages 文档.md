# 静态部署 ·Cloudflare Pages 文档
  
Next.js 是一个开源的 React 框架，用于创建网站和应用程序。在本指南中，您将创建一个新的 Next.js 应用程序并使用 Cloudflare Pages 进行部署。

  
本指南将指导您如何部署具有静态导出的静态站点Next.js项目。

准备工作
----

  
所有框架指南都假定您已经对 Git 有了基本的了解。如果你是 Git 的新手，请参阅这本总结的 Git 手册，了解如何在本地计算机上设置 Git。

  
如果使用 SSH 进行克隆，则必须在用于从 GitHub 推送或拉取的每台计算机上生成 SSH 密钥。

  
有关详细信息，请参阅 GitHub 文档和 Git 文档。

  
选择您的Next.js项目
----------------

  
如果已有要部署的Next.js项目，请确保将其配置为静态导出，切换到其目录，然后继续下一步。否则，用于 `create-next-app` 创建新的Next.js项目。

```
$ npx create-next-app --example with-static-export my-app 
```

  
创建项目后，将使用官方 `with-static-export` 示例作为模板生成一个新 `my-app` 目录。切换到此目录以继续。

###   
创建 GitHub 存储库

  
通过访问 repo.new 创建新的 GitHub 存储库。创建新存储库后，通过在终端中运行以下命令来准备本地应用程序并将其推送到 GitHub：

```
$ git remote add origin https://github.com/<GH_USERNAME>/<REPOSITORY_NAME>.git $ git branch -M main $ git push -u origin main 
```

###   
将应用程序部署到 Cloudflare Pages

  
要将网站部署到主页，请执行以下操作：

1.    
    登录 Cloudflare 仪表板  
    ，然后选择您的帐户。
2.    
    在“帐户主页”中，选择“工作线程和页面”>“创建应用程序”>“页面”>“连接到 Git”。
3.    
    选择您创建的新 GitHub 存储库，然后在“设置生成和部署”部分中，选择“Next.js（静态 HTML 导出）”作为框架预设。您的选择将提供以下信息。

| 配置选项 | Value |
| --- | --- |
| 生产分公司 | `main` |
| 构建命令 | `npx next build` |
| 构建目录 | `out` |

  
配置站点后，可以开始首次部署。Cloudflare Pages 将在部署之前安装 `next` 您的项目依赖项并构建您的站点。

预览您的网站
------

  
部署站点后，您将在 `*.pages.dev` 上收到项目的唯一子域。

  
每次您向Next.js站点提交新代码时，Cloudflare Pages 都会自动重建您的项目并部署它。您还可以访问新拉取请求的预览部署，因此可以在将更改部署到生产环境之前预览更改在站点中的外观。

  
有关将您的第一个站点部署到 Cloudflare Pages 的完整指南，请参阅入门指南。
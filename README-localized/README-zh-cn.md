# Python 联系人示例 #

该示例是一个正在进行的项目，其主要目标有两个：演示如何轻松使用 Python 中的 [Office 365 API](http://msdn.microsoft.com/en-us/office/office365/api/api-catalog)，以及帮助我学习 Python 和 Django。需要考虑的几个事项：

- 对于 Python 和 Django，我完全是一个新手。除了作为 [Django 教程](https://docs.djangoproject.com/en/1.7/intro/tutorial01/)的一部分创建的“投票”应用之外，这是我有史以来的第一个 Python 应用。因此，从 Python 的角度来看，我可能会以一种“不太理想”的方式做事。请随时让我知道！
- 我选择设定此示例的[联系人 API](http://msdn.microsoft.com/office/office365/APi/contacts-rest-operations)。但是，此方法对任何 REST API 均适用。
- 我使用的是内置 Django 开发服务器，因此尚未在任何生产级服务器上测试过它。
- 我使用在 Django 项目中创建的 SQLite 测试数据库，因此存储的任何数据库内容都位于开发计算机上的本地文件中。

## 所需软件 ##

- [Python 3.4.2](https://www.python.org/downloads/)
- [Django 1.7.1](https://docs.djangoproject.com/en/1.7/intro/install/)
- [请求：HTTP for Humans](http://docs.python-requests.org/en/latest/)

## 运行示例 ##

在开始之前，假定你已安装了 Python 和 Django。Windows 用户应将 Python 安装目录和脚本子目录添加到其 PATH 环境变量中。

1. 下载示例项目或为其创建分支。
2. 在 `manage.py` 所在的目录中打开命令提示符或 shell。
3. 如果可以运行 BAT 文件，请运行 setup\_project.bat。如果没有，请手动运行文件中的三个命令。最后一个命令将提示你创建超级用户，稍后将使用它登录。
4. 安装请求：来自命令行的 HTTP for Humans 模块：`pip install requests`
5. [在 Azure Active Directory 中注册应用](https://github.com/jasonjoh/office365-azure-guides/blob/master/RegisterAnAppInAzure.md)。应将应用注册为具有“http://127.0.0.1:8000/contacts”登录 URL 的 Web 应用，并应授予“读取用户联系人”的权限。
6. 编辑 `.\contacts\clientreg.py` 文件。复制在应用注册期间获取的应用的客户端 ID，并将其粘贴为 `id` 变量的值。复制在应用注册期间创建的密钥，并将其粘贴为 `secret` 变量的值。保存文件。
7. 启动开发服务器：`python manage.py runserver`
8. 你应该会看到如下所示的输出：
正在执行系统检查...
    
    系统检查未发现任何问题（0 静默）。
	2014 年 12 月 18 日 - 12:36:32
	Django 版本 1.7.1，使用设置“pythoncontacts.settings”
	在 http://127.0.0.1:8000/ 上启动开发服务器
	使用 CTRL-BREAK 退出服务器。
9. 使用浏览器访问 http://127.0.0.1:8000/contacts。
10. 使用你的超级用户帐户登录。
11. 此时系统会提示你连接 Office 365 帐户。单击该链接以执行此操作并使用 Office 365 帐户登录。
12. 你将看到一个表，其中列出了 Office 365 帐户中的现有联系人。你可以单击“新建联系人”按钮来创建新联系人，或使用现有联系人上的“编辑”或“删除”按钮。
13. 如果要查看该用户存储在 Django 数据库中的内容，也请访问 http://127.0.0.1:8000/admin，然后单击 Office365 连接链接。你也可以从管理网站中删除用户的记录，以防再次经历同意流程。

## 发布历史记录 ##

若要获取特定发布版本，请访问 https://github.com/jasonjoh/pythoncontacts/releases

- **1.2：邮件和日历功能。**o365service 模块现在具有某些邮件 API 和日历 API 功能。这些功能没有 UI，但是可以通过添加到 test.py 的新测试类来调用它们。此外还添加了一个用于禁用 SSL 证书验证的标志，以便你能够使用 Fiddler 捕获请求和响应。（[博客文章](http://blogs.msdn.com/b/exchangedev/archive/2015/01/15/office-365-apis-and-python-part-3-mail-and-calendar-api.aspx)）
- **1.1：联系人功能。**现在，应用将显示联系人列表，并允许用户创建新联系人以及编辑或删除现有联系人。（[博客文章](http://blogs.msdn.com/b/exchangedev/archive/2015/01/09/office-365-apis-and-python-part-2-contacts-api.aspx)）
- **1.0：初始发行版。**应用允许用户使用本地应用帐户连接 Office 365 帐户。应用可执行 OAuth2 代码授予流程并显示用户的访问令牌。（[博客文章](http://blogs.msdn.com/b/exchangedev/archive/2015/01/05/office-365-apis-and-python-part-1-oauth2.aspx)）

## 版权信息 ##

版权所有 (c) Microsoft。保留所有权利。

----------
在 Twitter 上通过 [@JasonJohMSFT](https://twitter.com/JasonJohMSFT) 与我联系

关注 [Exchange 开发人员博客](http://blogs.msdn.com/b/exchangedev/)
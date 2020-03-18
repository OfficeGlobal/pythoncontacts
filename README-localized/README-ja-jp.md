# Python 連絡先サンプル #

このサンプルは、2 つの主な目標を持つ進行中のプロジェクトです。それは、Python から [Office 365 API](http://msdn.microsoft.com/en-us/office/office365/api/api-catalog) を簡単に利用する方法を示し、Python と Dango の学習を支援することです。注意すべきことがいくつかあります。

- 私は Python と Django の初心者です。[Django チュートリアル](https://docs.djangoproject.com/en/1.7/intro/tutorial01/)の一部として作成された「投票」アプリ以外に、これは私の初めての Python アプリです。そのため、Python の観点からして「最適ではない」方法で物事を勧めるかもしれません。その場合は、教えてください。
- このサンプルでは、[連絡先 API](http://msdn.microsoft.com/office/office365/APi/contacts-rest-operations) を対象にしています。ただし、REST API でも同じ方法を使用できます。
- 組み込みの Django 開発サーバーを使用していたので、運用レベルのサーバーではテストしていません。
- Django プロジェクトを使用して作成された SQLite テスト データベースを使用していたため、保存されたデータベースを取得するものはすべて、開発マシンのローカル ファイルにあります。

## 必要なソフトウェア ##

- [Python 3.4.2](https://www.python.org/downloads/)
- [Django 1.7.1](https://docs.djangoproject.com/en/1.7/intro/install/)
- [共有s:HTTP for Humans](http://docs.python-requests.org/en/latest/)

## サンプルの実行 ##

始める前に、Python と Django がインストールされていると仮定します。Windows ユーザーは、Python インストール ディレクトリと Scripts サブディレクトリを PATH 環境変数に追加する必要があります。

1. サンプル プロジェクトをダウンロードまたは分岐します。
2. `manage.py` が存在するディレクトリに、コマンド プロンプトまたはシェルを開きます。
3. BAT ファイルを実行できる場合は、setup\_project.bat を実行します。それ以外の場合は、手動で 3 つのコマンドを実行します。最後のコマンドでは、後でログオンするために使用するスーパーユーザーを作成するように求められます。
4. インストールを要求します。コマンド ラインからの HTTP for Humans モジュール: `pip install requests`
5. [Azure Active Directory にアプリを登録します](https://github.com/jasonjoh/office365-azure-guides/blob/master/RegisterAnAppInAzure.md)。アプリは、サインオン URL が「http://127.0.0.1:8000/contacts」の Web アプリとして登録する必要があり、「ユーザーの連絡先を読み取る」権限を付与する必要があります。
6. `.\contacts\clientreg.py` ファイルを編集します。アプリの登録時に取得したアプリのクライアント ID をコピーし、`ID` 変数の値として貼り付けます。アプリの登録時に作成したキーをコピーし、`秘密情報`変数の値として貼り付けます。ファイルを保存します。
7. 開発サーバーを起動します。`python manage.py runserver`
8. 出力は次のようになります。
システム チェックを実行します...
    
    システム チェックで問題が特定されませんでした (0 が無音)。
	2014 年 12 月 18 日 - 12:36:32
	Django バージョン 1.7.1、 設定「pythoncontacts.settings」
	を使用 http://127.0.0.1:8000/
	で開発サーバーを起動 CTRL-BREAK でサーバーを終了。
9. ブラウザーを使用して http://127.0.0.1:8000/contacts に移動します。
10. スーパーユーザー アカウントでログインします。
11. Office 365 アカウントに接続するように求められます。リンクをクリックして、Office 365 アカウントでログインします。
12. Office 365 アカウントの既存の連絡先を一覧表示した表が表示されます。\[新しい連絡先] ボタンをクリックして、新しい連絡先を作成するか、既存の連絡先の \[編集] または \[削除] ボタンを使用します。
13. ユーザーの Django データベースに保存されている内容を表示するには、http://127.0.0.1:8000/admin に移動してから、Office365 の接続リンクをクリックします。同意プロセスを再度実行する場合に備えて、管理サイトからユーザーの記録を削除することもできます。

## リリース履歴 ##

特定のリリース バージョンを取得するには、https://github.com/jasonjoh/pythoncontacts/releases にアクセスしてください。

- **1.2:メールおよび予定表の機能。**o365service モジュールには、いくつかのメール API および予定表 API 機能があります。これらの機能に UI はありませんが、test.py に追加された新しいテスト クラスを使用して呼び出すことができます。また、Fiddler を使用して要求や応答をキャプチャできるように、SSL 証明書の検証を無効にするフラグを追加しました。([ブログ投稿](http://blogs.msdn.com/b/exchangedev/archive/2015/01/15/office-365-apis-and-python-part-3-mail-and-calendar-api.aspx))
- **1.1:連絡先の機能。**これで、連絡先の一覧が表示され、ユーザーは新しい連絡先を作成したり、既存の連絡先を編集または削除したりできます。([ブログ投稿](http://blogs.msdn.com/b/exchangedev/archive/2015/01/09/office-365-apis-and-python-part-2-contacts-api.aspx))
- **1.0:最初のリリース。**アプリは、ユーザーが Office 365 アカウントをローカル アプリ アカウントに接続できるようにします。アプリは OAuth2 コード付与フローを実行し、ユーザーのアクセス トークンを表示します。([ブログ投稿](http://blogs.msdn.com/b/exchangedev/archive/2015/01/05/office-365-apis-and-python-part-1-oauth2.aspx))

## 著作権 ##

Copyright (c) Microsoft.All rights reserved.

----------
Twitter ([@JasonJohMSFT](https://twitter.com/JasonJohMSFT)) でぜひフォローしてください。

[Exchange 開発ブログ](http://blogs.msdn.com/b/exchangedev/)をフォローする
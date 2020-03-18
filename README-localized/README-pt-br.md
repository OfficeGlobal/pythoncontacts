# Exemplo de Contatos do Python #

Este exemplo é um projeto em andamento com dois objetivos principais: mostrar como usar facilmente as [APIs do Office 365](http://msdn.microsoft.com/en-us/office/office365/api/api-catalog) do Python e me ajudar a aprender o Python e Django. Alguns pontos para lembrar:

- Eu sou um iniciante em Python e Django. Além do aplicativo de "votações" criado como parte do [tutorial do Django](https://docs.djangoproject.com/en/1.7/intro/tutorial01/), esse é o meu primeiro aplicativo Python. Por isso, posso fazer as coisas de uma maneira "inadequada", de uma perspectiva do Python. Sinta-se livre para me avisar!
- Eu escolhi segmentar a [API de Contatos](http://msdn.microsoft.com/office/office365/APi/contacts-rest-operations) para este exemplo. No entanto, a mesma metodologia deve funcionar para qualquer uma das APIs REST.
- Usei o servidor de desenvolvimento interno do Django, portanto não testei isso com nenhum servidor em nível de produção.
- Usei o banco de dados de teste SQLite que é criado com o projeto Django, portanto, qualquer coisa que possua um banco de dados armazenado está em um arquivo local na sua máquina de desenvolvimento.

## Software necessário ##

- [Python 3.4.2](https://www.python.org/downloads/)
- [Django 1.7.1](https://docs.djangoproject.com/en/1.7/intro/install/)
- [Solicitações: HTTP for Humans](http://docs.python-requests.org/en/latest/)

## Execução da amostra ##

Presume-se que você tenha o Python e o Django instalados antes de começar. Os usuários do Windows devem adicionar a pasta de instalação do Python e o subdiretório Scripts à variável de ambiente PATH.

1. Baixe ou bifurque o projeto de exemplo.
2. Abra o seu prompt de comando ou o Shell no diretório onde `manage.py` está localizado.
3. Se você puder executar arquivos BAT, execute setup\_project. bat. Caso contrário, execute os três comandos automaticamente no arquivo. O último comando solicitará que você crie um superusuário, que será usado mais tarde para fazer logon.
4. Instale as Solicitações: o modulo HTTP for Humans na linha de comando: `pip install requests`
5. [Registrar o aplicativo no Azure Active Directory](https://github.com/jasonjoh/office365-azure-guides/blob/master/RegisterAnAppInAzure.md). O aplicativo deve ser registrado como um aplicativo Web com um URL de Logon "http://127.0.0.1:8000/contacts" e deve ter permissão para "Ler os contatos dos usuários".
6. Edite o arquivo `.\contacts\clientreg.py`. Copie a ID do cliente obtida durante o registro do aplicativo e cole-a como o valor da variável `id`. Copie a chave criada durante o registro do aplicativo e cole-a como o valor da variável `segredo`. Salve o arquivo.
7. Inicie o servidor de desenvolvimento: `python manage.py runserver`
8. Você deve ver um resultado como:
Executando verificações do sistema...
    
    A verificação do sistema não identificou nenhum problema (0 silenciado).
	18 de dezembro de 2014 - 12:36:32
	Django versão 1.7.1, usando as configurações 'pythoncontacts.settings'
	Iniciando servidor de desenvolvimento em http://127.0.0.1:8000/
	Encerre o servidor com CTRL-BREAK.
9. Use seu navegador para acessar http://127.0.0.1:8000/contacts.
10. Entre com sua conta de superusuário.
11. Agora você deve ser solicitado a conectar sua conta do Office 365. Clique no link para fazer isso e entre com uma conta do Office 365.
12. Você deve ver uma tabela listando os contatos existentes na sua conta do Office 365. Você pode clicar no botão "Novo Contato" para criar um novo contato ou usar os botões "Editar" ou "Excluir" nos contatos existentes.
13. Se você quiser ver o que é armazenado no banco de dados Django para o usuário, acesse também http://127.0.0.1:8000/admin e clique no link de conexões do Office365. Você também pode excluir o registro do usuário do site de administração, caso queira passar pelo processo de consentimento novamente.

## Histórico de versões ##

Para obter uma versão específica do lançamento, acesse https://github.com/jasonjoh/pythoncontacts/releases

- **1.2: Funções de Email e Calendário.** O módulo o365service agora possui algumas funcionalidades da API de Email e da API de Calendário. Não há interface do usuário para essas funções, mas elas podem ser invocadas pelas novas classes de teste adicionadas ao test.py. Também foi adicionado um sinalizador para desativar a validação do certificado SSL, para que você possa capturar solicitações e respostas com o Fiddler. ([Postagem no Blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/15/office-365-apis-and-python-part-3-mail-and-calendar-api.aspx))
- **1.1: Funções de contato.** O aplicativo agora exibe uma lista de contatos e permite ao usuário criar novos contatos e editar ou excluir os existentes. ([Postagem no Blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/09/office-365-apis-and-python-part-2-contacts-api.aspx))
- **1.0: Versão inicial.** O aplicativo permite que o usuário conecte uma conta do Office 365 a uma conta do aplicativo local. O aplicativo concede fluxo de concessão do código OAuth2 e exibe o token de acesso do usuário. ([Postagem no Blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/05/office-365-apis-and-python-part-1-oauth2.aspx))

## Direitos Autorais ##

Copyright (c) Microsoft. Todos os direitos reservados.

----------
Conecte-se comigo no Twitter [@JasonJohMSFT](https://twitter.com/JasonJohMSFT)

Siga o [Blog de desenvolvedores do Exchange](http://blogs.msdn.com/b/exchangedev/)
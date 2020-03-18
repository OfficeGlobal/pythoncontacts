# Exemple de contacts Python #

Cet exemple est un projet en cours avec deux objectifs principaux : montrer comment utiliser facilement les [API Office 365](http://msdn.microsoft.com/en-us/office/office365/api/api-catalog) depuis Python et m’assister dans ma découverte de Python et Django. Quelques points à garder à l’esprit :

- Je suis un parfait débutant en Python et Django. À part l’application « sondages » créée dans le cadre du [Tutorial Django](https://docs.djangoproject.com/en/1.7/intro/tutorial01/), ceci est ma toute première application Python. Pour cette raison, je serai peut-être amené à faire des choses de manière « moins qu’optimale » d’un point de vue Python. N’hésitez pas à me le faire savoir !
- J’ai choisi de cibler l’[API Contacts](http://msdn.microsoft.com/office/office365/APi/contacts-rest-operations) pour cet exemple. Cependant, la même méthodologie devrait fonctionner pour n’importe quelle API REST.
- J’ai utilisé le serveur de développement Django intégré, je n’ai pas testé ceci avec les serveurs de niveau de production.
- J’ai utilisé la base de données de test SQLite qui a été créée avec le projet Django, donc tout ce qui reçoit une base de données stockée se trouve dans un fichier local sur votre ordinateur de développement.

## Logiciels requis ##

- [Python 3.4.2](https://www.python.org/downloads/)
- [Django 1.7.1](https://docs.djangoproject.com/en/1.7/intro/install/)
- [Requests : HTTP for Humans](http://docs.python-requests.org/en/latest/)

## Exécution de l’exemple ##

Il est supposé que Python et Django sont installés avant de commencer. Les utilisateurs de Windows doivent ajouter le répertoire d'installation Python et le sous-répertoire Scripts à leur variable d'environnement PATH.

1. Téléchargez ou dupliquez l’exemple de projet.
2. Ouvrez votre invite de commandes ou votre shell dans le répertoire dans lequel se trouve `manage.py`.
3. Si vous pouvez exécuter des fichiers BAT, exécutez setup\_project. bat. Si ce n’est pas le cas, exécutez manuellement les trois commandes dans le fichier. La dernière commande vous invite à créer un superutilisateur que vous utiliserez par la suite pour vous connecter.
4. Installez la bibliothèque Requests : HTTP for Humans depuis la ligne de commande : `pip install requests`
5. [Inscrivez l’application dans Azure Active Directory](https://github.com/jasonjoh/office365-azure-guides/blob/master/RegisterAnAppInAzure.md). L’application doit être inscrite en tant qu’application Web avec l’URL de connexion « http://127.0.0.1:8000/contacts », et vous devez disposer de l’autorisation « Lire les contacts des utilisateurs ».
6. Modifiez le fichier `.\contacts\clientreg.py`. Copiez l’ID client de votre application obtenue durant l’inscription de l’application et collez-le à l’emplacement de la valeur correspondant à la variable `id`. Copiez la clé créée durant l’inscription de l’application et collez-la à l’emplacement de la valeur correspondant à la variable `secret`. Enregistrez le fichier.
7. Démarrez le serveur de développement : `python manage.py runserver`
8. Vous devriez voir une sortie comme celle-ci :
Exécution de vérifications système...
    
    La vérification système n’a identifié aucun problème (0 silencieux).
	18 décembre 2014 – 12:36:32 Django version 1.7.1,
	avec les paramètres « pythoncontacts.settings »
	Démarrage du serveur de développement sur http://127.0.0.1:8000/
	Quittez le serveur avec la combinaison de touches CTRL + PAUSE.
9. Utilisez votre navigateur pour accéder à http://127.0.0.1:8000/contacts.
10. Connectez-vous avec votre compte de superutilisateur.
11. Vous devez maintenant être invité à vous connecter à votre compte Office 365. Cliquez sur le lien pour le faire et connectez-vous avec un compte Office 365.
12. Un tableau répertoriant les contacts existants dans votre compte Office 365 doit s’afficher. Vous pouvez cliquer sur le bouton « Nouveau contact » pour créer un contact, ou utiliser les boutons « Modifier » ou « Supprimer » dans les contacts existants.
13. Si vous voulez voir ce qui est stocké dans la base de données Django pour l’utilisateur, accédez à http://127.0.0.1:8000/admin et cliquez sur le lien Connexions Office 365. Vous pouvez également supprimer l’enregistrement de l’utilisateur depuis le site d’administration, au cas où vous voudriez repasser le processus de consentement.

## Historique des versions ##

Pour obtenir une version spécifique, accédez à https://github.com/jasonjoh/pythoncontacts/releases

- **1.2 : Fonctions Messagerie et Calendrier.** Le module o365service inclut désormais une fonctionnalité API de messagerie et API de calendrier. Il n’y a aucune interface utilisateur pour ces fonctions, mais elles peuvent être invoquées via les nouvelles classes de test ajoutées à test.py. Également ajouté : un indicateur pour désactiver la validation de certificat SSL pour pouvoir capturer les requêtes et les réponses avec Fiddler. ([Billet de blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/15/office-365-apis-and-python-part-3-mail-and-calendar-api.aspx))
- **1.1 : Fonctions de contact.** L’application affiche désormais une liste de contacts et autorise l’utilisateur à créer de nouveaux contacts ainsi que de modifier ou supprimer des contacts existants. ([Billet de blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/09/office-365-apis-and-python-part-2-contacts-api.aspx))
- **1.0 : Version initiale.** L’application permet à l’utilisateur de se connecter à un compte Office 365 avec un compte d’application local. L’application effectue un flux d’octroi de code Oauth2 et affiche le jeton d’accès de l’utilisateur. ([Billet de blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/05/office-365-apis-and-python-part-1-oauth2.aspx))

## Copyright ##

Copyright (c) Microsoft. Tous droits réservés.

----------
Suivez-moi sur Twitter [@JasonJohMSFT](https://twitter.com/JasonJohMSFT)

Suivez le [blog de développement Exchange](http://blogs.msdn.com/b/exchangedev/)
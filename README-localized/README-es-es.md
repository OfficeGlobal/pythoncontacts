# Muestras de los contactos de Python #

Esta muestra es un proyecto en curso con dos objetivos principales: mostrarme cómo usar fácilmente la [API de Office 365](http://msdn.microsoft.com/en-us/office/office365/api/api-catalog) desde Python, y ayudarme a aprender sobre Python y Django. Puntos a tener en cuenta:

- Soy un principiante con respecto a Python y Django. Aparte de la aplicación de "encuestas" creada como parte del [tutorial de Django](https://docs.djangoproject.com/en/1.7/intro/tutorial01/), esta es la primera aplicación en Python que hago. Por este motivo, puedo hacer cosas en un método de una manera "no del todo óptimo" desde la perspectiva de Python. No dude en hacerme saber.
- Decidí elegir como objetivo la [API de contactos](http://msdn.microsoft.com/office/office365/APi/contacts-rest-operations) para esta muestra. Sin embargo, la misma metodología debería funcionar con cualquiera de las API de REST.
- He usado el servidor de desarrollo de Django,así que no he probado esto en los servidores del nivel de producción.
- He usado la base de datos de prueba SQLite que fue creada con el proyecto de Django, así que todo lo almacenado en la base de datos está en un archivo local en el equipo de desarrollo.

## Software necesario ##

- [Python 3.4.2](https://www.python.org/downloads/)
- [Django 1.7.1](https://docs.djangoproject.com/en/1.7/intro/install/)
- [Requests: HTTP for Humans](http://docs.python-requests.org/en/latest/)

## Ejecutar la muestra ##

Antes de empezar, se presupone que tiene Python y Django instalados. Los usuarios de Windows deben agregar el directorio de instalación de Python y el subdirectorio Scripts a su variable de entorno PATH.

1. Descargue o bifurque el proyecto de ejemplo.
2. Abra el símbolo del sistema o el Shell en el directorio donde se encuentra `manage.py`.
3. Si puede ejecutar archivos BAT, ejecute setup\_project.bat. Si no es así, ejecute los tres comandos en el archivo manualmente. El último comando le pedirá que cree un superusuario, que usará más tarde para iniciar sesión.
4. Instale el módulo de Requests: HTTP for Humans desde la línea de comandos: `pip install requests`
5. [Registre la aplicación en Azure Active Directory](https://github.com/jasonjoh/office365-azure-guides/blob/master/RegisterAnAppInAzure.md). La aplicación tiene que registrarse como una aplicación web con la dirección URL de inicio de sesión de "http://127.0.0.1:8000/contacts", y se le deben conceder los permiso para "leer los contactos de los usuarios".
6. Edite el archivo `.\contacts\clientreg.py`. Copie la Id. de cliente de la aplicación obtenido durante el registro de la misma y péguelo como valor de la variable `Id`. Copie la clave creada durante el registro de la aplicación y péguela como valor de la variable `secreta`. Guarde el archivo.
7. Inicie el servidor de desarrollo: `python manage.py runserver`
8. Debe ver un resultado como el siguiente:
Realizando las comprobaciones del sistema...
    
    La comprobación del sistema no encontró ningún problema (0 silenciados).
	18 de diciembre de 2014 - 12:36:32 versión de Django 1.7.1,
	usando la configuración 'pythoncontacts.settings'
	iniciando el servidor de desarrollo en http://127.0.0.1:8000/
	Salga del servidor con Ctrl+Interrumpir.
9. Use el explorador para ir a http://127.0.0.1:8000/contacts.
10. Inicie sesión con su cuenta de superusuario.
11. Ahora, se le pedirá que conecte su cuenta de Office 365. Haga clic en el vínculo para hacer esto e inicie sesión con una cuenta de Office 365.
12. Debería ver una tabla que enumera los contactos existentes en su cuenta de Office 365. Puede hacer clic en el botón "contacto nuevo" para realizar esta acción o usar los botones "editar" o "eliminar" en los contactos existentes.
13. Si quiere ver la información que se almacena en la base de datos para el usuario de Django, también puede ir a http://127.0.0.1:8000/admin y hacer clic en el vínculo de conexiones de Office365. En caso de que quiera volver a pasar por el proceso de consentimiento también puede eliminar el registro del usuario del sitio de administración.

## Historial de publicaciones ##

Para obtener una versión de lanzamiento específica, vaya a https://github.com/jasonjoh/pythoncontacts/releases

- **1.2: Funciones de correo y calendario.** El módulo o365service ahora tiene algunas funcionalidades de API del correo y el calendario. Sin interfaz de usuario para estas funciones, pero pueden ser llamadas a través de las nuevas clases de prueba agregadas a test.py. También se agregó una marca para deshabilitar la validación de certificados SSL para que pueda capturar solicitudes y respuestas con Fiddler. ([Entrada del blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/15/office-365-apis-and-python-part-3-mail-and-calendar-api.aspx))
- **1.1: Funciones de contacto.** La aplicación ahora muestra una lista de contactos y permite al usuario crear nuevos contactos y editar o eliminar los existentes. ([Entrada del blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/09/office-365-apis-and-python-part-2-contacts-api.aspx))
- **1.0: Versión inicial.** La aplicación permite que el usuario conecte una cuenta de Office 365 con una cuenta de aplicación local. La aplicación utiliza el código OAuth2 para garantizar el flujo y mostrar el token de acceso del usuario. ([Entrada del blog](http://blogs.msdn.com/b/exchangedev/archive/2015/01/05/office-365-apis-and-python-part-1-oauth2.aspx))

## Derechos de autor ##

Copyright (c) Microsoft. Todos los derechos reservados.

----------
Conectar conmigo en Twitter [@JasonJohMSFT](https://twitter.com/JasonJohMSFT)

Seguir el [blog de desarrollo de Exchange](http://blogs.msdn.com/b/exchangedev/)
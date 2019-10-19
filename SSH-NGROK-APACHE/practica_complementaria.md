# Espacio de Definición Institucional

### Introducción (Definiciones)

#### Servidor SSH en Ubuntu

SSH o también conocido como Secure Shell, es un protocolo y el nombre del programa que lo implementa. SSH es ampliamente conocido por ser el protocolo seguro para la administración remota de servidores, routers, switches y un largo etcétera de equipos. El protocolo SSH permite manejar por completo el servidor o dispositivo de red mediante un intérprete de órdenes, además, también podemos redirigir el tráfico para ejecutar programas gráficos a través de la propia sesión SSH.

Otras características fundamentales de SSH son que nos va a permitir copiar datos de manera segura, tanto archivos como carpetas, a través del protocolo SFTP (SSH FTP), un protocolo hecho desde cero y que no tiene nada que ver con FTPS o FTPES (FTP sobre SSL/TLS). El protocolo SSH es fundamental en el ámbito de las redes y sistemas, además, podremos configurarlo en detalle para dotar a nuestro sistema de la máxima seguridad posible.

El protocolo SSH proporciona confidencialidad (los datos van cifrados punto a punto), autenticación (podremos autenticarnos frente al servidor SSH de múltiples maneras, con usuario/clave, criptografía de clave pública e incluso podremos configurar un segundo factor de autenticación), integridad (si los datos se modifican o los modifica un usuario malintencionado se podrá detectar, ya que usa HMAC para comprobar la integridad de todos y cada uno de los datos).

Existen dos versiones de SSH, la versión 1 no se recomienda hoy en día usarla, de hecho, por defecto siempre se utiliza ya la versión SSHv2. Por defecto SSH utiliza el protocolo TCP de la capa de transporte, y el número de puerto es el 22, no obstante, podremos cambiar el número de puerto para mitigar posibles escaneos de bots al servicio SSH.


#### NGROK : Abrir nuestro servidor local a internet

Ngrok es una herramienta que permite acceder a nuestro servidor local a cualquier persona en internet con la que compartamos una url generada dinámicamente, esto es muy útil por ejemplo cuando necesitamos mostrar avances constantemente en sitios que se encuentran en etapa de desarrollo o cuando trabajamos con un equipo de desarrolladores de forma remota .

Ngrok nos permite realizar esto sin hacer ninguna configuración extra en el router o firewall simplemente basta con bajar la pequeña aplicación y ejecutar un comando :

	$ngrok http 80

La aplicación creará un tunel mediante una la url dinámica mostrando lo que se tenga en nuestro servidor previamente instalado MAMP , LAMP o WAMP dentro de la carpeta principal de este :

	http://92832de0.ngrok.io -&gt; localhost:80

En la versión gratuita esta url se genera cada que ejecutemos ngrok , sin embargo con la opción de pago podemos configurar subdominios permanentes y otras opciones más avanzadas que harán más fácil nuestro trabajo.


#### Apache en Ubuntu

Apache es un servidor web HTTP de código abierto y multiplataforma que implementa el protocolo HTTP/1.12​ y la noción de sitio virtual. El objetivo de este proyecto es proporcionar un servidor seguro, eficiente y extensible que proporcione servicios HTTP en sincronización con los estándares HTTP actuales.

El servidor web Apache a menudo es usado en combinación con el motor de bases de datos MySQL, el lenguaje de scripting PHP, y otros lenguajes de scripting populares como Python y Perl. Esta configuración se denomina LAMP (Linux, Apache, MySQL y Perl/Python/PHP) y conforma una potente y robusta plataforma para el desarrollo y distribución de aplicaciones basadas en la web.


### Guía práctica básica

Debemos tener presente que en esta guía, el servidor ssh ya está corriendo en un ordenador y solo tiene un usuario previamente creado. También tiene previamente instalado Tmux y GPG.

1. Ingresamos al servidor utilizando el comando:
		
		$ssh username@ip_server
Una vez que coloquemos el username existente y la ip del servidor nos pedirá que escribamos "yes" para ingresar al servidor. Una vez dentro nos solicitará la clave del usuario preexistente.

2. Crear nuestro propio usuario

		$sudo adduser usuario_nuevo
		
	Al realizar este paso, nos solicitará la contraseña por defecto del servidor y posteriormente la contraseña del usuario que estamos agregando actualmente. Una vez ingresada la clave, nos pedirá que la verifiquemos una segunda vez y finalmente nos pedirá completar unos datos personales que pueden o no omitirse.

3. Ingresar al servidor desde nuestro usuario creado en el paso 2

	Debemos finalizar sesión ssh o podemos cerrar la ventana. Luego de ello, abrimos un nuevo terminal y tipeamos el paso 1 pero esta vez con nuestro usuario nuevo.

		$ssh usuario_nuevo@ip_server

	> **Note:** Si ingresamos al servidor desde el usuario principal podemos cambiar a nuestro usuario escribiendo el siguiente comando:

		$su nuevo_usuario

4. Para ver si otros usuarios están conectados en ese momento al servidor podemos escribir el comando:

		$who
		
5. Dentro de nuestra carpeta home perteneciente al usuario nuevo creado, debemos generar nuestra clave gpg pública y privada. Para esto [citaremos el comando de la siguiente guía](https://github.com/matiaslawwliet/EDI/blob/master/GPG/tutorial_basico_gpg.md) sin dar mayores explicaciones.

		$gpg --gen-key

6. Ahora debemos ir a la carpeta del usuario principal y buscar en su carpeta de Descargas el archivo de nombre ngrok y copiarlo en nuestro home. Recordando que estamos actualmente en nuestro home, debemos escribir los siguientes comandos:

		$cd ..
	> **Note:** Salimos de nuestro home

		$cd username
	> **Note:** Ingresamos al home del usuario principal

		$cd Descargas
	> **Note:** Ingresamos a la carpeta Descargas del usuario principal

		$cp ngrok /home/usuario_nuevo
	> **Note:** Copiamos el archivo ngrok del usuario principal al home del usuario que creamos

7. Ahora debemos crear una cuenta en [Ngrok](https://ngrok.com)

8. Una vez creada debemos realizar una autenticación por token. La cual nos será brindada por la website de Ngrok al logear en la web.

		`./ngrok authtoken`token_asignado_por_la_web







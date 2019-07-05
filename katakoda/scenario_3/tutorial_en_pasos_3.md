# **Espacio de definición institucional - ISFDyT210**
### Ejercicios para Git de [KataKoda](https://www.katacoda.com/courses/git) (Scenario 3 de 5)
#### Scenario 2 - Comitiando cambios
#
##### **Paso 1 - Git Remote**

Los repositorios remotos le permiten compartir cambios desde o hacia su repositorio. Las ubicaciones remotas son generalmente un servidor de compilación, una máquina de miembros del equipo o una tienda centralizada como Github.com. Los controles remotos se agregan utilizando el comando git remote con un nombre descriptivo y la ubicación remota, generalmente una URL HTTPS o una conexión SSH, por ejemplo, https://github.com/OcelotUproar/ocelite.git o git@github.com: / OcelotUproar / ocelite.git.

El nombre descriptivo le permite referirse a la ubicación en otros comandos. Su repositorio local puede hacer referencia a varios repositorios remotos diferentes dependiendo de su escenario.

##### **Tarea**
En mi caso particular ya tenía configurado mi repositorio local con el remoto por lo que solo debo verificar mediante git remote -v para saber a que escritorio remoto se sube mis archivos y desde donde se descargan para actualizarse.

```sh
$ git remote -v
```
Mi consola arrojó el siguiente resultado:

```sh
origin  https://github.com/matiaslawwliet/EDI.git (fetch)
origin  https://github.com/matiaslawwliet/EDI.git (push)
```

En caso de que no arrojara ningun valor podría haber tipeado:

```sh
$ git remote https://github.com/matiaslawwliet/EDI.git
```

##### **Protip**
Si utiliza git clone, que se analiza en un escenario futuro, entonces la ubicación desde la que está clonando se agregará automáticamente como un control remoto con el origen del nombre.

En particular debería colocar:
```sh
$ git clone https://github.com/matiaslawwliet/EDI.git
```

#
##### **Paso 2 - Git Push**

Cuando esté listo para compartir sus archivos, debe enviarlos a un repositorio remoto a través de git push. Un flujo de trabajo típico de Git sería realizar múltiples confirmaciones pequeñas a medida que completa una tarea y lo empuja hacia un punto remoto en puntos relevantes, como cuando se completa la tarea, para garantizar la sincronización del código dentro del equipo.

El comando git push es seguido por dos parámetros. El primer parámetro es el nombre descriptivo del repositorio remoto que definimos en el primer paso. El segundo parámetro es el nombre de la rama. Por defecto, todos los repositorios de git tienen una rama maestra donde se trabaja el código.

##### **Tarea**
Empuje las confirmaciones en la rama maestra al control remoto de origen.

```sh
$ git push
```

La primera vez que se pushea en github pedira usuario y contraseña para verificar que es el dueño del repositor señalado en git remote.

#
##### **Paso 3 - Git Pull

Donde git push le permite enviar sus cambios a un repositorio remoto, git pull funciona a la inversa. git pull le permite sincronizar los cambios de un repositorio remoto en su versión local.

Los cambios del repositorio remoto se fusionan automáticamente en la rama en la que está trabajando actualmente.

##### **Tarea**
Tire de los cambios desde el control remoto a su rama maestra.

```sh
$ git pull
```

#
##### **Paso 4 - Git Log**

Como se describe en el escenario anterior, puede usar el comando git log para ver el historial del repositorio. El comando git show le permitirá ver los cambios realizados en cada confirmación. La salida de git show resalta las nuevas líneas agregadas al archivo en verde.

```sh
$ git log
$ git show
```

#
##### **Step 5 - Git Fetch**

El comando git pull es una combinación de dos comandos diferentes, git fetch y git merge. Fetch descarga los cambios del repositorio remoto en una rama separada llamada remotes / <remote-name> / <remote-branch-name>. Se puede acceder a la sucursal usando git checkout.

Usar git fetch es una excelente manera de revisar los cambios sin afectar tu rama actual. El formato de nomenclatura de las sucursales es lo suficientemente flexible como para que pueda tener varios controles remotos y sucursales con el mismo nombre y cambiar fácilmente entre ellas.

El siguiente comando fusionará los cambios recuperados en el maestro.

git merge remotes / <remote-name> / <remote-branch-name> master

Cubriremos la fusión con más detalle en un escenario futuro.

##### **Tarea**
Se han realizado cambios adicionales en el repositorio de origen. Use git fetch para descargar los cambios y luego verifique la rama para verlos.

```sh
$ git fetch
```

##### **Protip**
Puede ver una lista de todas las ramas remotas usando el comando git branch -r

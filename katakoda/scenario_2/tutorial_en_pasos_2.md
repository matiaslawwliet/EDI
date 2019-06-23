# **Espacio de definición institucional - ISFDyT210**
### Ejercicios para Git de [KataKoda](https://www.katacoda.com/courses/git) (Scenario 1 a 5)
#### Scenario 2 - Comitiando cambios
#
##### **Paso 1 - Estado Git**

Como se discutió en el escenario anterior, el estado de git nos permite ver los cambios en el directorio de trabajo y el área de preparación en comparación con el repositorio.

Dado el repositorio actual, las pantallas de estado de git que se han realizado en nuestro directorio de trabajo para el archivo confirmado, commit.js, pero aún no se han movido al área de preparación.

```sh
$ nano committed.js
```

Dentro del documento agregamos el texto "archivo sin modificaciones". Luego añadimos el archivo al area de seguimiento

```sh
$ git add committed.js
```

Ahora creamos un archivo untracked.js y modificamos el contenido de committed.js

```sh
$ touch untracked.js
```

```sh
$ nano committed.js
```

Dentro del archivo committed borramos " archivo sin modificaciones" y lo reeemplazamos por "modificacion 1"

Finalmente colocamos el comando status para verificar que el archivo untracked no tiene seguimiento y el archivo committed tiene modificaciones

```sh
$ git status
```

#
##### **Paso 2 - Git Diff**

El comando git diff le permite comparar los cambios en el directorio de trabajo con una versión previamente confirmada. Por defecto, el comando compara el directorio de trabajo y la confirmación HEAD.

Si desea comparar con la versión anterior, proporcione el hash de confirmación y el parámetro, por ejemplo, git diff <commit>. Comparando con las confirmaciones serán los cambios para todos los archivos modificados. Si desea comparar los cambios con un solo archivo, proporcione el nombre como un argumento como git diff committed.js.

```sh
$ git diff
$ git diff committed.js
```

Ambos comandos son válidos. Uno muestra las diferencias en todos los archivos en el area de seguimiento mientras el otro muestra solo las diferencias de un archivo específico.

##### **Protip**
Por defecto, la salida está en el formato diff combinado. El comando git difftool cargará una herramienta externa de su elección para ver las diferencias.

```sh
$ git difftool
```

#
##### **Paso 3 - Git Add**

Al igual que en el escenario anterior, para confirmar y cambiarlo, primero debe usar el comando git add.

##### **Tarea**
Para proceder a la primera etapa tus cambios usando git add. Podemos agregarlos uno a uno, usar "*" o "."

```sh
$ git add .
```

##### **Protip**
Si cambia el nombre o elimina archivos, deberá especificar estos archivos en el comando Agregar para que se puedan rastrear. Alternativas puede usar git mv y git rm para que git realice la acción e incluya la actualización del área de preparación.

#
##### **Paso 4 - Staged Differences**

Una vez que los cambios están en el área de preparación, no se mostrarán en la salida de git diff. Por defecto, git diff solo comparará el directorio de trabajo y no el área de preparación.

Para comparar los cambios en el área de preparación con el parámetro git diff --staged. Esto le permite asegurarse de que ha gestionado correctamente todos sus cambios.

```sh
$ git diff --staged
```

#
##### **Paso 5 - Git Log**

El comando git log le permite ver el historial del repositorio y el registro de confirmación.

```sh
$ git log
```

Mantenemos presionado "q" para salir de git log.

##### **Protip**
El formato de la salida del registro es muy flexible. Por ejemplo, para generar cada confirmación en una sola línea, el comando es git log --pretty = format: "% h% an% ar -% s". Se pueden encontrar más detalles en la página de registro de git a la que se accede mediante el registro de git --help.

# **Espacio de definición institucional - ISFDyT210**
### Ejercicios para Git de [KataKoda](https://www.katacoda.com/courses/git) (Scenario 4 de 5)
#### Scenario 2 - Comitiando cambios
#
##### **Paso 1 - Git Checkout**

Al trabajar con Git, un escenario común es deshacer los cambios en su directorio de trabajo. El comando git checkout reemplazará todo en el directorio de trabajo a la última versión confirmada.

Si desea reemplazar todos los archivos, use un punto (.) Para indicar el directorio actual; de lo contrario, enumere los directorios / archivos separados por espacios.

##### **Tarea**
Use git checkout para borrar cualquier cambio en el directorio de trabajo.

Se creara la carpeta scenario_4 y un archivo de nombre 'actualizable' dentro de ella. Luego será subida a github la nueva versión. Finalmente se le agregará un texto cualquiera y se realizara un git checkout para que vuelva a estar vacio, tal cual la versión mas reciente en github.

Usaremos para actualziar todo
```sh
$ git checkout .
```

o en específico
```sh
$ git checkout actualizable.txt
```

#
##### **Paso 2 - Git Reset**

Si está en medio de un compromiso y ha agregado archivos al área de preparación pero luego cambió de idea, deberá usar el comando git reset. git reset moverá los archivos desde el área de preparación al directorio de trabajo. Si desea restablecer todos los archivos, utilice un archivo. para indicar el directorio actual, de lo contrario listar los archivos separados por espacios.

Esto es muy útil cuando trata de mantener sus compromisos pequeños y enfocados, ya que puede mover los archivos de regreso fuera del área de preparación si ha agregado demasiados.

##### **Tarea**
Mueva los cambios de la puesta en escena nuevamente al directorio de trabajo usando git reset.

Agregaremos texto al archivo actualizable.txt, lo enviaremos al área de preparación  con 

```sh
$ git add actualizable.txt
```
y luego utilizamos git reset

```sh
$ git reset actualizable.txt
```

#
##### **Paso 3 - Git Reset Hard**

Un git reset - hard combinará tanto git reset como git checkout en un solo comando. El resultado serán los archivos eliminados del área de preparación y el directorio de trabajo volverá al estado de la última confirmación.

##### **Tarea**
Elimine los cambios tanto del área de preparación como del directorio de trabajo usando git reset

Haremos el paso 1 y 2 para luego utilizar 

```sh
$ git reset --hard
```

##### **Protip**
El uso de HEAD borrará el estado hasta la última confirmación, usando git reset --hard <commit-hash> le permite volver a cualquier estado de confirmación. Recuerde, HEAD es un alias para el último hash de confirmación de la rama.

#
##### **Paso 4 - Git Revert**
Si ya ha confirmado archivos pero se dio cuenta de que cometió un error, entonces el comando git revert le permite deshacer los errores. El comando creará una nueva confirmación que tiene el efecto inverso de la confirmación que se está revertiendo.

Si no ha presionado sus cambios, entonces git reset HEAD ~ 1 tiene el mismo efecto y eliminará el último compromiso.

##### **Tarea**
Use git revert para revertir los cambios en la última confirmación.

Tenga en cuenta que esto abrirá una sesión del editor Vim para crear un mensaje de confirmación para cada confirmación. Para guardar el mensaje de confirmación y salir de vim, escriba el comando: wq para cada sesión de Vim.

Realizaremos el paso 1 y 2 luego comitearemos y pushearemos el resultado final. A continuación tipearemos git revert Head y nos abrira el editor, presionaremos Ctrl+O para guardar cambios y Ctrl+X para salir.

```sh
$ git revert HEAD
```

##### **Protip**
La motivación detrás de la creación de nuevos compromisos es que volver a escribir la historia en Git es un anti-patrón. Si ha presionado sus confirmaciones, debe crear nuevas confirmaciones para deshacer los cambios, ya que otras personas podrían haber realizado confirmaciones mientras tanto.

#
##### **Paso 5 - Git Revert**
Para revertir múltiples confirmaciones a la vez usamos el carácter ~ para significar menos. Por ejemplo, HEAD ~ 2 son dos confirmaciones de la cabeza. Esto se puede combinar con los caracteres ... para decir entre dos confirmaciones.

##### **Tarea**
Utilice el comando git revert HEAD ... HEAD ~ 2 para revertir las confirmaciones entre HEAD y HEAD ~ 2.

```sh
 git revert HEAD...HEAD~2
```

Finalmente, crearemos el archivo tutorial en pasos 4 con todo este texto y pushearemos el contenido final de la carpeta scenario 4.

##### **Protip**
Puede usar el comando git log --oneline para obtener una visión general rápida del historial de confirmaciones.


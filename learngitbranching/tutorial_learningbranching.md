# **Espacio de definición institucional - ISFDyT210**
### Ejercicio Complementario sobre [LearningBranching](https://learngitbranching.js.org)
#### Tutorial
#
##### **Paso**

Este trabajo es un ejercicio complementario a imaginación del alumno. En mi caso particular realizaré una rama nueva en la que se corregiré los errores de tipeo de los tutoriales de katakoda. Una vez finalizado se realizará un git merge sobre la rama master para unificar ambas ramas y lograr las correcciones necesarias.

##### **Tarea**
Crear una rama nueva de nombre "correciones" y moverse a ella.
```sh
$ git checkout -b correcciones
```

Editar archivos md y luego agregarlos a la zona de seguimiento. Para ello haremos uso del atajo "git add ." de esta forma agregaremos todos los archivos a la vez.

```sh
$ git add .
```

Finalmente volveremos a la rama master y unificaremos ambas ramas.

```sh
$ git checkout master
$ git merge correcciones
```

Para saber si las correcciones se aplicaron correctamente, agregaremos un mensaje al final de este archivo md indicando que las correcciones se realizaron de forma satisfactoria.



#### **Las modificaciones de la rama correcciones se agregaron satisfactoriamente a la rama master**


Adjunto captura de git log donde se ve claramente la rama correciones mergeada a master:

![captura_ramas](https://i.imgur.com/UgvXD4W.png)

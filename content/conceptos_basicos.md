## Conceptos básicos 🕶
Se puede decir que un **repositorio** de GIT, es un "historial" (que inicialmente se guarda en tu equipo local) de determinados momentos en que decides que un cambio/proceso/actualización de tu proyecto debe estar disponible para su posterior consulta/modificación/eliminación. Es como tener una "cámara" que tomará una "foto instantánea" (un *commit*) de tu proceso de desarrollo cuando tú así lo consideres necesario y cada uno de estos *commits* son puntos de referencia que posteriormente te servirá para saber lo que sucedió hasta ese preciso momento. Esto lo puedes hacer las veces que consideres necesario hasta finalizar con tu proyecto.

Para que comprendas el proceso de creación de un repositorio en GIT, es necesario que conozcas las "*etapas*" que conforman el procceso de creación de un "*commit*" o "confirmación". De forma general, en GIT existen 3 etapas (+1) que conforman el proceso de creación de un *commit* (el conjunto de todos tus *commits* formarán tu historial):
1. ### **Working Directory**
   El *Working Directory* o *Directorio de Trabajo*, es el directorio en el que GIT detecta las actualizaciones/cambios/procesos que aún no están consideradas como parte de tu historial y GIT las coloca de forma automática en esta etapa. Para indicarle a GIT que quieres que  considere dichos cambios en tu historial, debes utilizar el comando `git add` (y combinaciones de sus opciones).
2. ### **Staging Area (index)**
   Ahora nuestras actualizaciones/cambios/procesos se ecuentran dentro del *Staging Area* o *Área de preparación* (también llamado *index*), que es donde le indicas a GIT que quieres que dichos procesos se encuentren disponibles para su posterior confirmación e inclusión dentro del historial de tu proyecto, es decir: crear un punto de referencia o *commit*. Para tal efecto, le indicarás a GIT que realice este proceso mediante el comando `git commit` (y combinaciones de sus opciones).
3. ### **Repository (local)**
   En esta etapa, todos los cambios confirmados mediante `git commit ...` ya forman parte de tu repositorio local, es decir, que ya tienes en tu equipo, las "instantáneas" de tu proceso de desarrollo. Dentro de tu repositorio, ahora existen *puntos de control* que te ayudarán a "viajar" en el tiempo y poder verificar el estado en el que se encontraba tu proyecto en determinado momento y si es necesario, modificarlo de acuerdo a tus necesidades (recomendable hacer uso de ramas [**branchs**]).

![Los tres estados de GIT](../assets/images/index1%402x.png)

Como ves, hasta cierto punto es sencillo entender la forma en la que se compone un repositorio creado con GIT, pero a lo largo de tus proyectos, te darás cuenta que van a surgir diversos detalles y que deberás conocer a mayor profundidad los comandos que GIT te ofrece para darles solución.  
Por otro lado, ¿qué pasará si por alguna razón, tu equipo/ordenador falla y no tienes acceso a todo el historial de uno o varios de tus proyectos? Para tener un respaldo de nuestro historial, existen servicios/plataformas como GitHub, GitLab, GitBucket, etc., en los que puedes "subir" y almacenar tu repositorio con todo el historial que tenías de forma local y de esta forma, ya seas tú mismo u otro usuario, puede *clonar* dicho repositorio y tenerlo disponible en su equipo y con ello, poder continuar con tu trabajo desde el último estado en que lo dejaste.

### MarkDown

Un aspecto importante a considerar es que cuando estamos haciendo uso de Git y decidimos "respaldar" nuestro repositorio con el uso de un servicio externo como GitHub, es necesadio tener creado un archivo de "**presentación**" donde podamos dar detalles de lo más relevante que queramos dar conocer a los usuarios que visiten nuestro repositorio.  

Esto se hace mediante el uso de una archivo estándarizado: `README.md`. Este archivo es un archivo "*MarkDown*", el cual sirve como la presentación inicial de todo repositorio, en el cual se pueden detallar lo que queramos. Este tipo de archivos sigue el estándar de "*MarkDown*" y hace uso de un lenguaje de marcado, similar a las etiquetas de `HTML`. Por lo que su uso es bastante intuitivo.  

Para mejor referencia puedes consultar la documentacion oficial [aquí](https://markdown.es/ "¿Qué es Markdown?") y también la sintáxis Markdown en este [enlace](https://markdown.es/sintaxis-markdown/ "Sintaxis Markdown")
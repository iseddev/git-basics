## Comandos básicos de visualización de los estados del proyecto

En esta ocasión vamos a ver los comandos básicos que nos ayudan a "*revisar*" algunos estados de nuestro proyecto.  

### Mostrar detalles simplificados de las etapas en las que se encuentran nuestros procesos
```powershell
git status -s
```
* `M`  -> Modified  
   *red* = Fuera de la etapa *staging*, listo para ser agregado a la etapa de *staging*  
   *green* = Dentro de la etapa *staging*, listo para ser confirmado(committed)
* `??` -> Archivo sin seguimiento(untracked), usar `git add <untrackedFileName>` para incluir el archivo a la etapa de *staging*
* `A`  -> Archivo agregado a la etapa de *staging* antes de tener algun commit
* `AM` -> Archivo agregado y modificado, a la espera de su gestión (considerar los colores anteriores)
* `D` -> Archivo eliminado  
   *red* = Eliminado de nuestro directorio y de la etapa *committed*, dicho proceso pasa a la etapa de *working*  
   *green* = Eliminado sólo del estado *committed* y pasa a la etapa de *working* como "untracked"  

*Al estar todas las flags en verde, ahora podemos hacer el(los) commit(s) necesario(s)*  

Para más detalles del comando `git status`, haz click [aquí](https://git-scm.com/docs/git-status "Documentación git status")

<br><hr>

### Visualizar las diferencias de los cambios realizados en los archivos que aún no se encuentren en la etapa de *staging*.
```powershell
git diff
```
En caso de que se hayan agregado alguna linea de código en nuestro archivo, lo observaremos con un `+` seguido de la información incorporada, todo en color verde, ejemplo:  

<code style="color: green; font-weight: bold; font-family: consolas">+  &lt;p&gt;This paragraph was added to our HTML file&lt;/p&gt;
</code><br>
En caso de que hayamos eliminado o modificado una línea de código, observaremos el cambio con un `-` seguido de la información que se eliminó, todo en color rojo, ejemplo:  

<code style="color: green; font-weight: bold; font-family: consolas">+  &lt;p&gt;This paragraph was modified in our HTML file&lt;/p&gt;
</code><br>
<code style="color: red; font-weight: bold; font-family: consolas">-  &lt;p&gt;This paragraph was added to our HTML file&lt;/p&gt;
</code><br>

En este último ejemplo, modificamos la linea de código que confirmamos en el primer ejemplo y al ejecutar `git diff`, git nos muestra que se eliminó una linea de código y que se agregó otra, pero en realidad lo que Git detecta es que al modificarse una línea de código, esta ya no existe y en su lugar se creó una nueva línea de código.  

<br><hr>

### Visualizar las diferencias entre los cambios realizados en los archivos que *YA* se encuentren en la etapa de *staging*.

El despliegue de información funciona igual que con `git diff`
```powershell
git diff --staged
```
<hr>

### Visualizar las diferencias de los cambios realizados entre dos commits
```powershell
git diff <hashCommitValueOne> <hashCommitValueTwo>
```
Otra forma de realizar este proceso de una forma mas sencilla es mediante el acceso al "puntero" en el que nos encontramos, es decir, en donde se localiza apuntando `HEAD`, si no nos hemos "movido" a un commit diferente al último commit realizado, `HEAD` estará apuntando a ese commit.  
Ahora bien, podemos utilizar la siguiente nomenclatura para referirnos a la posición en la que se encuentra `HEAD`:
```powershell
git diff HEAD~1
```
Lo anterior le indica a Git que nos muestre las diferencias entre el commit en el que se encuentra actualmente `HEAD` y un commit "menos" o anterior a él. Esto lo podemos establecer con el uso de `~`, y el `1` posterior indica cuántos commits anteriores a la posición actual de comparar. Es como especificar que: **muestre las diferencias entre el commit en el que `HEAD` está actualmente "apuntando" y "un" (o el anterior definido) commit anterior a él**.  

Esto quiere decir que si queremos comparar el commit en el que `HEAD` está apuntando y "dos" commits anteriores a él, se debe ejecura lo siguiente: `git diff HEAD~2` y así sucesivamente.  

<br><hr>

### Visualizar el historial de commits realizados en nuestro proyecto en diversos formatos
```powershell
git log | git log --oneline | git log --oneline --graph | git log --oneline --graph --decorate
```
La secuencia de comandos que da un detalle mas compacto es `git log --oneline --graph --decorate`, dando como resultado algo como esto:
```powershell
userName@PC-Name MINGW64 ~/Desktop/ProjectDirectoryName (main)
git log --oneline --graph --decorate
* 026e197 (HEAD -> main) Last commit message goes here
* 40da396 Commit message goes here
* 81f1b94 Commit message goes here
* ba6eb76 Initial commit
```
Esto despliega los commits dentro de nuestro repositorio. Observa que despues de cada `*` hay una especie de "*código*" formado por letras y números, estos son los identificadores/hashes (acortados - 7 posiciones) asignados a cada commit, con estos valores podemos realizar determinadas operaciones permitidas dentro de Git. Podemos desplegar una forma más detallada con el uso del comando `git log`, obteniendo algo como esto:
```powershell
userName@PC-Name MINGW64 ~/Desktop/ProjectDirectoryName (main)
git log
commit 026e1972a2877aa453d5d8fa0f8b8ba1d637c1a3 (HEAD -> main)
Author: Full User Name <user.email@mail.com>
Date:   Mon Jul 11 20:06:23 2022 -0500

    Last commit message goes here

commit 40da3961bbc496b5790d1f5181d3e119a362413b
Author: Full User Name <user.email@mail.com>
Date:   Mon Jul 11 19:50:35 2022 -0500

    Commit message goes here

commit 81f1b94624f0ffda64fd8f5ea8862a20338ebb60
Author: Full User Name <user.email@mail.com>
Date:   Mon Jul 11 19:44:26 2022 -0500

    Commit message goes here

commit ba6eb76583babe64e88cee081d6c8f5e43bfd7b8
Author: Full User Name <user.email@mail.com>
Date:   Mon Jul 11 19:03:46 2022 -0500

    Initial commit
```
Como podrás observar, el detalle de cada commit es más amplio, ya que despliega el identificador/Hash completo, información del autor (nombre y correo electrónico), la fecha de creación y el mensaje del commit.
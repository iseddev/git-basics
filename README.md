# 💻 Material de apoyo básico de Git 💻

Repositorio con el objetivo de ofrecerte información básica para que puedas implementar en tus proyectos éste potente Sistema de Control de Versiones (*VCS* "Version Control Systems").  
Para poder tener acceso a los conceptos generales más detallados, puedes consultar la documentación oficial de GIT, disponible en la siguiente [página](https://git-scm.com/docs "Documentación oficial de GIT")<br><br>

### *Observaciones* 🕵️‍♀️
✍ En este repositorio, se utiliza la notación `< >` para indicar que un comando/valor/nombre debe detallarse de acuerdo a las indicaciones dentro de `< >` y de las condiciones de tu proyecto. Por ejemplo: `<fileName.ext>` se refiere a que debes ingresar un nombre de archivo y su extensión.  
✍ La notación `" "` es utilizada para indicar que un fragmento de texto debe detallarse de acuerdo a las indicaciones dentro de los `" "` y de las condiciones de tu proyecto. Por ejemplo: `"Your Real Name"` quiere decir que "escribas" tu nombre real.<br><br>

## Índice

- [Uso básico de la terminal de comandos (consola)](./content/terminal.md)
- [Compatibilidad entre Sistemas Operativos](./content/compatibilidad.md)
- [Conceptos básicos](./content/conceptos_basicos.md)
- [Antes de iniciar](./content/antes_de_iniciar.md)
- [Iniciar Git en tu proyecto](./content/iniciar_git.md)
- [Primeros pasos](./content/primeros_pasos.md)
- [Metiendo las manos al código](./content/comandos_git.md)
- [Creando y modificando "commits"](./content/creando_commmits.md)

***Contenido pendiente de agregar...***
<!-- 
>Mostrar detalles simplificados de las etapas en las que se encuentran nuestros procesos
```powershell
git status -s
```
* `M`  -> Modified  
   *red* = Fuera de la etapa *staging*, listo para ser agregado a la etapa de *staging*  
   *green* = Dentro de la etapa *staging*, listo para ser confirmado(committed)
* `??` -> Archivo sin seguimiento(untracked), usar `git add <untrackedFileName>` para incluir el archivo a la etapa de *staging*
* `A`  -> Archivo agregado a la etapa de *staging* antes de tener algun commit
* `A`M -> Archivo agregado y modificado, a la espera de su gestión (considerar los colores anteriores)
* `D` -> Archivo eliminado  
   *red* = Eliminado de nuestro directorio y de la etapa *committed*, dicho proceso pasa a la etapa de *working*  
   *green* = Eliminado sólo del estado *committed* y pasa a la etapa de *working* como "untracked"  

*Al estar todas las flags en verde, ahora podemos hacer el(los) commit(s) necesario(s)*  

Para más detalles del comando `git status`, haz click [aquí](https://git-scm.com/docs/git-status "Documentación git status")<br><br>
<hr>

>Visualizar las diferencias de los cambios realizados en los archivos que aún no se encuentren en la etapa de *staging*.
```powershell
git diff
```
En caso de que se hayan agregado alguna linea de código en nuestro archivo, lo observaremos con un `+` seguido de la información incorporada, todo en color verde, ejemplo:  
<code style="color: green; font-weight: bold; font-family: consolas">+  &lt;p&gt;This paragraph was added to our HTML file&lt;/p&gt;
</code><br><br>
En caso de que hayamos eliminado o modificado una línea de código, observaremos el cambio con un `-` seguido de la información que se eliminó, todo en color rojo, ejemplo:  
<code style="color: green; font-weight: bold; font-family: consolas">+  &lt;p&gt;This paragraph was modified in our HTML file&lt;/p&gt;
</code><br>
<code style="color: red; font-weight: bold; font-family: consolas">-  &lt;p&gt;This paragraph was added to our HTML file&lt;/p&gt;
</code><br>  
En este último ejemplo, modificamos la linea de código que confirmamos en el primer ejemplo y al ejecutar `git diff`, git nos muestra que se eliminó una linea de código y que se agregó otra, pero en realidad lo que Git detecta es que al modificarse una línea de código, esta ya no existe y en su lugar se creó una nueva línea de código.<br><br>
<hr>

>Visualizar las diferencias entre los cambios realizados en los archivos que *YA* se encuentren en la etapa de *staging*. El despliegue de información funciona igual que con `git diff`
```powershell
git diff --staged
```
<hr>

> Visualizar las diferencias de los cambios realizados entre dos commits
```powershell
git diff <hashCommitValueOne> <hashCommitValueTwo>
```
Otra forma de realizar este proceso de una forma mas sencilla es mediante el acceso el "puntero" en el que nos encontramos, es decir, en donde se localiza apuntando `HEAD`, si no nos hemos "movido" a un commit diferente al último commit realizado, `HEAD` estará apuntando a ese commit.  
Ahor bien, podemos utilizar la siguiente nomenclatura para referirnos a la posición en la que se encuentra `HEAD`:
```
git diff HEAD~1
```
Lo anterior le indica a Git que nos muestre las diferencias entre el commit en el que se encuentra actualmente `HEAD` y un commit "menos" o anterior a él. Esto lo podemos establecer con el uso de `~` y el `1` posteror indica cuántos commits anteriores a la posición actual comparará. Es como especificar que: **muestre las diferencias entre el commit en el que `HEAD` está actualmente "apuntando" y "un" commit anterior a él**.  

Esto quiere decir que si queremos comparar el commit en el que `HEAD` está apuntando y "dos" commits anteriores a él, se debe ejecura lo siguiente: `git diff HEAD~2` y así sucesivamente.<br><br>
<hr>

>Visualizar el historial de commits realizados en nuestro proyecto en diversos formatos
```powershell
git log | git log --oneline | git log --oneline --graph | git log --oneline --graph --decorate
```
La secuencia de comandos que da un detalle mas compacto es `git log --oneline --graph --decorate`, dando como resultado algo como esto:
```
userName@PC-Name MINGW64 ~/Desktop/ProjectDirectoryName (main)
git log --oneline --graph --decorate
* 026e197 (HEAD -> main) Last commit message goes here
* 40da396 Commit message goes here
* 81f1b94 Commit message goes here
* ba6eb76 Initial commit
```
Esto despliega los commits dentro de nuestro repositorio. Observa que despues de cada `*` hay una especie de "*código*" formado por letras y números, estos son los identificadores/hashes (acortados - 7 posiciones) asignados a cada commit, con estos valores podemos realizar determinadas operaciones permitidas dentro de Git. Podemos desplegar una forma más detallada con el uso del comando `git log`, obteniendo algo como esto:
```
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
Como podrás observar, el detalle de cada commit es más amplio, ya que despliega el identificador/Hash completo, información del autor (nombre y correo electrónico), la fecha de creación y el mensaje del commit.<br><br>
<hr>

>Posicionarse en el estado en que se encontraba nuestro proyecto cuando confirmamos el commit especificado en &lt;hashCommitValue&gt;.
```powershell
git checkout <hashCommitValue>
```
<hr>

>Deshacer los últimos cambios realizados en un archivo que se encuentra en la etapa de *working*, para que el archivo quede en su estado original antes de la modificación que se le aplicó
```powershell
git checkout -- <filename.ext>
```
<hr>

>Renombrar un archivo y pasarlo directamente a la etapa de *staging*
```powershell
git mv <oldFileName.ext> <newFileName.ext>
```
<hr>

>Eliminar de nuestro directorio el archivo especificado. Al ser una modificación en nuestro flujo de trabajo, ahora tendremos esta acción en la etapa de *staging*, lista para ser confirmada y dar detalles de esta acción.
```powershell
git rm <fileName>
```
<hr>

>Eliminar de nuestro directorio el archivo especificado en modo FORZADO. Esto eliminará de forma definitiva el archivo sin posibilidades de recuperarlo ya que esta acción ***NO*** se registra en nuestro historial.
```powershell
git rm -f <fileName>
```
<hr>

>Recuperar un archivo eliminado inmediatamente después de haber utilizado `git rm <fileName>`
  1. Utilizar: `git restore --staged <filename>`
  2. Utilizar: `git restore <filename>`
<hr>

>Eliminar todos los commits posteriores realizados a `<hashCommitValue>` y pasa los archivos/procesos a la etapa de *working* sin perder los cambios realizados hasta ese momento
```powershell
git reset <hashCommitValue>
```
*Podemos complementar con el comando `git checkout -- <fileName>` para eliminar algún cambio no deseado dentro de nuestro archivo en cuestión*.<br><br>
<hr>

>Elimina el(los) commit(s) **POSTERIOR(ES)** al especificado en `<hashCommitValue>` y pasa todo a la etapa de *staging* (listo para confirmar) sin borrar los cambios realizados hasta ese momento.
```powershell
git reset --soft <hashCommitValue>
```
<hr>

>Elimina **TODOS** los commits **POSTERIORES** al `<hashCommitValue>` incluyendo las modificaciones de nuestro proyecto, posicionandonos en el estado original en el que se econtraba nuestro proyecto en `<hashcommitValue>`
```
git reset --hard <hashCommitValue>
```
<hr>

>Elimina el(los) commit(s) **POSTERIOR(ES)** al especificado en `<hashCommitValue>` y pasa todo a la etapa de *working* sin borrar los cambios realizados hasta ese momento.
```powershell
git reset --mixed <hashcommitValue>

```
<hr>

>"Revertir" un commit y evitar posible conflictos entre usuarios que intervienen en el mismo proyecto, contrario a lo que puede ocurrir con `git reset --flag <hashCommitValue>`
```powershell
git revert <hashCommitValue>
```
Adicionalmente, podemos utilizar la notación que vimos anteriormente, en la que se utiliza `HEAD` como puntero posicionado en el commit que se "revertirá" (o a los anteriores con `HEAD~value`) y utilizarlo en lugar de escribir el hash del commit involucrado
```powershell
git revert HEAD | git revert HEAD~1 | git revert HEAD~2 | ...
```
`git revert HEAD` es equivalente a `git revert <hashCommitValue>` (suponemos que `HEAD` se encuentra apuntando al último commit creado y que `<hashCommitValue>` es ese último commit creado.  
<br><br>

---
## Gestión de ramas (***branches***) 🔃
<br>

Cuando nuestro proyecto es robusto, cuenta con la colaboración de varios desarrolladores o por simple organización, se vuelve un poco complicado que se trabaje sobre una misma rama, pero, ¿qué es una rama? Bueno, lo primero a tener en cuenta es que en el momento en que creamos un repositorio en nuestro proyecto, por defecto se crea la rama principal ***main*** y podemos a comenzar a trabajar en nuestro desarrollo sin mayor contratiempo. Pero como se dijo anteriormente, si el proyecto lo requiere, es bueno pensar "*dividir*" el flujo de trabajo en varios "*micro entornos de desarrollo*", donde cada integrante del equipo realizará sus aportaciones al proyecto.  

Una manera secilla de poder conceptualizar una rama es pensar en "*caminos*" o "*rutas*" de desarrollo *independientes*, pero que se mantienen en conexión al proyecto en general. Después de que en cada rama se llega un punto en el que el resultado es lo que se esperaba, se procede a la "fusión" a la rama principal.  

Es por ello que en la gran mayoría de los Sistemas de Control de Versiones (incluyendo a Git), existen las ramas ("*branches*"). Esto ofrece una gran flexibilidad para no manipular directamente nuestro proyecto un sólo flujo (o rama), sino que tenemos la posibilidad de crear "ramificaciones" paralelas a nuestro proyecto y de esta manera podemos mantener un flujo de trabajo limpio y ordenado. Veamos los comando más utilizados en la gestión de ramas en Git:
<hr>

>Enlistar las ramas que existen dentro de nuestro proyecto
```powershell
git branch | git branch -l
```
<hr>

>Crear una nueva rama desde el punto donde estamos actualmente con el nombre especificado en `<branchName>`
```powershell
git branch <branchName>
```
**Notas:**  
*Para poder crear una rama, es necesario haber confirmado por lo menos un commit dentro de nuestro proyecto*.  
*La rama principal por defecto es **`main`**.*
<hr>

>Crea una nueva rama desde el punto donde estamos actualmente con el nombre especificado en `<branchName>` y se mueve a esta rama
```powershell
git checkout -b <branchName>
```
***ACTUALIZACIÓN***  
Hoy en día Git ha implementado el comando `switch`, por lo que la ejecución anterior se actualiza a:
```powershell
git switch -c <branchName>
```
<hr>

> Crea una nueva rama desde el punto donde estamos actualmente con el nombre especificado en `<branchName>`, en el commit especificado en `<hashCommitValue>` y se mueve a esta rama
```powershell
git checkout -b <branchName> <hashCommitValue>
```
***ACTUALIZACIÓN***  
Hoy en día Git ha implementado el comando `switch`, por lo que la ejecución anterior se actualiza a:
```powershell
git switch -c <branchName> <hashCommitValue>
```
<hr>

>Eliminar la rama especificada en `<oldBranchName>` y se crea una nueva rama en su lugar con el nombre especificado en `<newBranchName>`
```powershell
git branch -m <oldBranchName> <newbranchName>
```
<hr>

>Moverse a la rama especificada en `<branchName>` y se pasan las modificaciones pendientes a esta rama, ahora se podran confirmar y dichas confirmaciones quedarán establecidas en la rama a la que nos cambiamos
```powershell
git checkout <branchName>
```
***Actualización***  
Hoy en día Git ha implementado el comando `switch`, por lo que la ejecucuón anterior se actualiza a:
```powershell
git switch <branchName>
```
<hr>

>Eliminar la rama especificada en `<branchName>`
```powershell
git branch -d <branchName>
```
<hr>

>Eliminar la rama especificada en `<branchName>` de forma "forzada"
```powershell
git branch -D <branchName>
```
<hr>

>Crear/recuperar una rama eliminada (con sus estados y confirmaciones) con el nombre especificado en `<deletedBranchName>` y con el HASH especificado en `<hashCommitValue>`
```powershell
git branch -b <deletedBranchName> <hashCommitValue>
```
*Para recuperar una rama que se eliminó por alguna razón y no contamos con su numbre y el hash del commit en donde se creó, podemos hacer uso del comando `git reflog`, esto nos desplegará "**todo**" el historial de confirmaciones dentro de nuestro proyecto, por lo que ahora podremos obtener tanto el nombre de la rama eliminada como el commit en la que se creó. Ahora seremos capaces de recuperar nuestra rama y el estado en el que se encontraba mediante la ejecución del comando anterior: `git branch -b <deletedBranchName> <hashCommitValue>`, esto debe reestablecer nuevamente la rama en cuestión, incluyendo todos los cambios y confirmaciones que contenía*  
<br>
Una vez que en tu rama trabajo haz terminado de confirmar todos tus cambios y deseas agregar todos estos cambios al flujo de trabajo principal de "*main*", lo que tienes que hacer es una "**fusión**" de ramas. Pero antes de todo, lo que tienes que tomar en cuenta, es que debes estar posicionado en la rama principal (***main***) para que en esta rrama se agreguen los cambios deseados.  

Ahora verás como "*fusionar*" o unir una rama específicada a la rama principal.
> Fusionar la rama especificada en `<branchNameToMerge>` a la rama principal (tienes que estar posicionado en la rama principal) con un mensaje descriptivo de soporte para esta acción
```powershell
git merge <branchNameToMerge> -m "A descriptive message goes here..."
```
### Algunos problemas en el manejo de ramas
En ocasiones te enfrentarás a algunos "*problemas*" al fusionar ramas, como por ejemplo, supongamos que creaste la rama `feat-index-02`, realizas un cambio en el archivo `style.css` (por ejemplo) que involucarn las líneas `11, 12 y 13`, confirmas los cambios, te cambias a la rama `main` y sin darte cuenta (o por la razon que sea), realizas un cambio en el mismo archivo `styles.css` en las mismas líneas `11, 12 y 13`, confirmas este cambio y despues de un tiempo, procedes a fusionar la rama `feat-index-02` con la rama `main`, esto creará un "*confilcto*" al momento de realizar la fusión.  

Para ello Git, te desplegará en el archivo involucrado, los cambios que realizaste en una rama y los cambios que realizaste en la rama `main` para que decidas los cambios que quieres que se confirmen, los que quieras que se ignoren, ignorar todos los cambios o aceptar todos lo cambios, tú lo decides, un ejemplo de este *conflicto* lo verás a continuación:
```powershell
h1 {
<<<<<<< HEAD (Current change)
  text-transform: uppercase;
=======
  font-size: 2.4rem;
>>>>>>> feat-index-02 (Incomming change)
}
```
La línea `<<<<<<< HEAD (Current change)` te indica que el cambio actual es `text-transform: uppercase;`, posteriormente, la linea con `=======` es una especie de separador, seguido de los cambios provenientes de la rama que se intenta fusionar, en este ejemplo `font-size: 2.4rem;`, por útlimo se finaliza con `>>>>>>> feat-index-02 (Incomming change)`, detallando de que rama proviene el cambio que provoca el conflicto en nuestra fusión.  

Ahora en tu archivo con el conflicto, debes decidir que cambios deseas conservar y posteriormente confirmar. Si deseas conservar ambos cambios, simplemnete elimina las lineas:  
```powershell
<<<<<<< HEAD (Current change)
=======
>>>>>>> feat-index-02 (Incomming change)
```
Quedando tu archivo de la siguiente forma:
```powershell
h1 {
  text-transform: uppercase;
  font-size: 2.4rem;
}
```
Procedes a guardar cambios, añadir el cambio al `staging area` (comando `git add`) y por último confirmar dicho proceso (comando `git commit`). Esto confirmará dichos cambios y actualizará tu archivo y tendrás tu flujo de trabajo limpio y sin conflictos.  

Si deseas omitir un cambio y aplicar otro, simplemente elimina las líneas de código que deseas borrar, guarda, cambios, agrega el proceso al `staging area`, finaliza con la confirmación de tu proceso (`git commit`) y listo.  

Por último, en caso de que te "arrepientas" y decidas que no quieres realizar la fusión de ramas, puedes ejecutar el siguiente comando:
```powershell
git merge --abort
```
O si decides que siempre sí vas a continuar con la fusión, ejecuta el siguiente comando:
```powershell
git merge --continue
```
<br>

---
## 🔖 Gestion de etiquetas (tags) 🔖

Una etiqueta en Git, es útil cuando necesitas dejar alguna "*marca*" en tu código en un commit en especial, ya sea que en un futuro quieras regresar a un estado en el que se encontraba tu código, para tener un punto de referencia de tu avance o simplemente para cualquier otro motivo que amerite que pongas un "**tag**" en tu proyecto. El tipo de etiquetes que puedes utilizar para este fin, son las llamadas "*lightweight*" o *ligeras*, que simplemente se establece el nombre de la etiqueta en el commit deseado y listo.  

Por otro lado, a medida que un proyecto va evolucionando y se llega a un punto en el que el resultado final se puede considerar como una version estable, también puedes hacer uso de las "**tags**". Las etiquetas utilizadas para definir una "versión" pueden nombrarse como desees, pero una forma de hacerlo es la siguiente: ***v0.0.1***. Para este tipo de etiquetas se hace uso las llamadas "*tags*" **anotadas**, las cuales contiene información más detallada y se les define un mensaje que describa el motivo de dicha etiqueta.  
<br>

> Crear una "*etiqueta ligera*" con el nombre v0.0.1 (el nombre de la etiqueta lo defines a tu gusto) en el úlimo commit que realizamos, en el commit en donde nos hayamos movido (por ejemplo con el uso de `git checkout <hashCommitValue>`) ó el commit en donde `HEAD` este posicionado, sin considerar alguna descripción o mensaje definido
```powershell
git tag v0.0.1
```

> Crear una "*etiqueta anotada*" con el nombre v0.0.1 (el nombre de la etiqueta lo defines a tu gusto) en el úlimo commit que realizamos, en el commit en donde nos hayamos movido (por ejemplo con el uso de `git checkout <hashCommitValue>`) ó el commit en donde `HEAD` este posicionado, añadiendo una descripción o mensaje específicos
```powershell
git tag -a v0.0.1 -m "Descriptive message for the tag"
```

> Crear la etiqueta v0.0.1 en el commit especificado en `<hashCommitValue>`
```powershell
git tag v0.0.1 <hashCommitValue>
```

> Crear la etiqueta "v0.0.1" en el commit especificado en `<hashCommitValue>` y añade un mensaje a dicha etiqueta
```powershell
git tag v0.0.1 <hashCommitValue> -m "Descriptive message for the tag"
```

> Modificar el mensaje o descripción definida en la etiqueta v0.0.1
```powershell
git tag -f v0.0.1 -m "New descriptive message for the tag"
```

> Reemplazar la etiqueta existente en el commit especificado en `<hashCommitValue>` con el nombre v0.0.5 y añadir un mensaje a dicha etiqueta
```powershell
git tag -f v0.0.5 -m "Descriptive message for the tag" <hashCommitValue>
```
*Si el nombre del **tag** es el mismo, simplemente se modifica el mensaje de dicha etiqueta, pero si hay diferencia en el nombre de la etiqueta, entonces se **crea** una nueva etiqueta en el commit especificado y se sigue conservando la etiqueta ya existente, es decir, ahora tendremos dos etiquetas en el mismo commit, por lo que se recomienda eliminar la etiqueta que ya no se desea conservar, esto se puede hacer mediante el comando `git tag -d <tagName>`*  
<br>

> Enlistar las etiquetas de nuestro proyecto
```powershell
git tag | git tag -l
```

> Verificar el contenido/mensaje de la etiqueta v0.0.1
```powershell
git tag -v v0.0.1
```

> Verificar los "**detalles completos**" de la etiqueta v0.0.1
```powershell
git show v0.0.1
```

> Moverse hacia un commit en específico pero mediante el uso de la etiqueta que se le creó, por ejemplo v.0.0.1
```powershell
git checkout v0.0.1
```

> Eliminar la etiqueta v0.0.1
```powershell
git tag -d v0.0.1
```
 -->
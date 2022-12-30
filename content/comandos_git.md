## Aplicando Git en nuestro proyecto

Continuando con el ejercicio anterior y considerando que nuestra terminal esta posicionada en la carpeta `pagina_web`, vamos a:

<br><hr>

### **Verificar el "estado" en el que se encuentra el seguimiento de nuestro proyecto.**

```powershell
git status
```
Esto debería arrojar algo como esto:
```powershell
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
        index.html
        styles.css

nothing added to commit but untracked files present (use "git add" to track)
```

Lo anterior indica que Git ha detectado tres archivos, los cuales se encuentran en estado ***untracked*** (*sin seguimiento*). En este punto, estos archivos se encuentran en la etapa de **Working Directory** o *Directorio de Trabajo* pero aun no forman parte del "*historial de seguimiento*" de Git.

<br><hr>

### **Agregar un proceso a la etapa de *staging*.**

```powershell
git add <fileName.ext>
```

<br><hr>

### **Agregar "todos" los procesos/archivos a la etapa de *staging*.**
```powershell
git add . | git add -A
```
Si ejecutamos lo siguiente: `git add index.html`, se agregará al *staging area* sólamente el archivo `index.html` y si posteriormente ejecutamos `git status`, podriamos ver algo como esto:
```powershell
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
        styles.css

```
Al observar lo anterior, notaremos que ahora `index.html` está "listo" para ser "*commiteado*" o confirmado, es decir, ahora podremos tomar la foto "instantánea" para captura el estado actual y sus cambios para que posteriormente se pueda consultar dicho estado en cualquier otro momento.  

Por otro lado, seguimos viendo que `README.md` y `styles.css` aún se encuentran fuera del seguimiento de Git (siguen en el *Working Directory*), por lo que es necesario pasarlos al *Staging Area* para que Git pueda llevar el seguimiento de estos archivos.  
Pero en este caso son sólo dos archivos, que pasaría si tuviéramos que agregar 10 o 15 o más archivos, esto sería un poco laborioso al tener que agregar archivo por archivo. Para ello exiten los comandos `git add .` y `git add -A`, ambos comandos agregarán todos los archivos que se encuentran en el *Working Directory* al *Staging Area*, vamos a verlo:  

Ejecutemos:

```powershell
git add .
```
Esto agregará nuestros dos archivos restantes al *Staging Area*:
```powershell
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
        new file:   index.html
        new file:   styles.css

```

Ahora, nuestros tres archivos están listos para ser "*commiteados*" o "*confirmados*" para ser agregados al historial de cambios dentro de Git. Es **importante** notar que en cada interacción con los comandos de Git, se nos mostraran algunas acciones a considerar en caso de quere revertir la ejecución del comando aplicado en el momento.  

Para este ejemplo podemos observar la línea: `(use "git rm --cached <file>..." to unstage)`, que nos da la ejecución a realizar en caso de querer revertir el proceso de "*staging*" que acabamos de aplicar. Por ejemplo, consideremos revertir el proceso de *staging* aplicado al archivo `index.html`:  

<br><hr>

### Eliminar un proceso de la etapa de *staging* y regresarlo al *Working Directory*

```powershell
git rm --cached <fileName.ext>
```
Para nuestro ejemplo, ejecutaremos lo siguiente: `git rm --cached index.html`, esto nos debería arrojar algo como esto:
```powershell
$ git rm --cached index.html
rm 'index.html'
```
Ejecutamos ahora `git status` para verificar el estado de nuestro proyecto:
```powershell
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
        new file:   styles.css

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html

```
Podemos observar como ahora `index.html` regresó a la etapa de *Working Directory* con el estado de `untracked`, es decir, sin seguimiento por parte de Git.  

💣 ***RETO*** 💣 - Ejecuta el comando que te ayude pasar el archivo `index.html` al *Staging Area*.  

Ahora volvamos a ejecutar `git status`:
```powershell
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
        new file:   index.html
        new file:   styles.css

```
**IMPORTANTE**  
La ejecución del comando `git rm --cached <file>` tiene la particularidad que además de pasar el archivo indicado al *Working Directory*, ***también*** eliminará cualquier cambio realizado en el archivo hasta el último punto en que se realizó un *commit* o confirmación previo.  

Si lo único que queremos es sacar el archivo del *Staging Area* y pasarlo al *Working Directory* ***sin*** perder los cambios realizados hasta el momento, entonces debemos hacer uso de:  

<br><hr>

### Pasar archivo/proceso del *Staging Area* al *Working Directory* sin perder cambios
```powershell
git restore --staged <fileName>
```

**OTROS COMANDOS DE MODIFICACIÓN DE ESTADOS**  
<hr>

### Eliminar los últimos *cambios* en un archivo que ya tuvo al menos una confirmación(commit) previa y que se ha modificado y ***NO*** se ha pasado a la etapa de *staging*, es decir, que no se ha utilizado el comando `git add <fileName> | git add . | git add -A` y su estado es "*M - modified*".
```powershell
git restore <filename>
```
<hr>

### Sacar el último proceso que está en la etapa de *staging* y pasarlos a la etapa de *working* sin perder los cambios realizados hasta el momento.
```powershell
git reset
```
***Excelente!!!*** Ahora es tiempo de hacer nuestro primer *commit* o confirmación. En nuestra consola de comandos podemos ejecutar lo siguiente:  
<br><hr>

### Realizar confirmación (*commit*) detallando el mensaje del *commit* en el editor de texto configurado.
```powershell
git commit
```
**Nota**: Este comando abrirá el archivo `COMMIT_EDITMSG` (el nombre puede variar) en el editor de texto configurado para que auí se detalle el mensaje del commit, se debe detallar lo mas corto posible pero muy descriptivo el motivo por el que se está realizando dicha confirmación. Posteriormente se debe guardar el archivo y cerrar la venta que se abrió para este proceso.

<br><hr>

### Realizar confirmación (*commit*) detallando el mensaje correspondiente en la misma terminal.
```powershell
git commit -m "Write a descriptive message here"
```
*En ambas ejecuciones, cada *commit* creado contará con un **identificador** (hash) con el que posteriormente podremos acceder a él para realizar las acciones permitidas en un *commit*.*

<br><hr>

### "Alterar/modificar" el último *commit* realizado, agregándole "nuevos" cambios y definir un nuevo mensaje en el editor de texto configurado.
```powershell
git commit --amend
```
<hr>

### "Alterar/modificar" el último *commit* realizado, agregándole "nuevos" cambios y definir un nuevo mensaje en la misma terminal.
```powershell
git commit --amend -m "Message that will replace the previous one"
```
***Nota***: *En ambas ejecuciones, lo que sucede en realidad es que se elimina el último *commit*, se crea uno nuevo(con su propio hash) y éste último conserva los cambios de ambas confirmaciones junto con el mensaje establecido*.  

*Para validar lo anterior, podemos ejecutar el comando `git reflog`, lo que te ayudara a desplegar en terminal **todos** y cada uno de los commits generados, incluso los que por la razón que sea, se hayan eliminado*.  

<br><hr>

### Verificar los cambios realizados desde el útlimo commit
```powershell
git diff
```
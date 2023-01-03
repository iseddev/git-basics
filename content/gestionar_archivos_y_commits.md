## Gestión de archivos y commits con Git

Ahora vanos a ver los comandos básicos para la gestión de archivos y commits dentro de Git.

### Deshacer los últimos cambios realizados en un archivo que se encuentra en la etapa de *working*, para que el archivo quede en su estado original antes de la modificación que se le aplicó.
```powershell
git checkout -- <filename.ext>
```
<hr>

### Renombrar un archivo y pasarlo directamente a la etapa de *Staging Area*
```powershell
git mv <oldFileName.ext> <newFileName.ext>
```
<hr>

### Eliminar de nuestro directorio el archivo especificado.
Al ser una modificación en nuestro flujo de trabajo, ahora tendremos esta acción en la etapa de *staging*, lista para ser confirmada y dar detalles de esta acción.
```powershell
git rm <fileName.ext>
```
<hr>

### Recuperar un archivo eliminado inmediatamente después de haber utilizado `git rm <fileName.ext>`
  1. Utilizar: `git restore --staged <fileName.ext>`
  2. Utilizar: `git restore <filename.ext>`

<hr>

### Eliminar de nuestro directorio el archivo especificado en modo **FORZADO**.
Esto eliminará de forma definitiva el archivo sin posibilidades de recuperarlo ya que esta acción ***NO*** se registra en nuestro historial.
```powershell
git rm -f <fileName.ext>
```
<hr>

### Eliminar todos los commits posteriores realizados a `<hashCommitValue>` y pasa los archivos/procesos a la etapa de *working* sin perder los cambios realizados hasta ese momento
```powershell
git reset <hashCommitValue>
```
*Podemos complementar con el comando `git checkout -- <fileName.ext>` para eliminar algún cambio no deseado dentro de nuestro archivo en cuestión*.

<br><hr>

### Elimina el(los) commit(s) **POSTERIOR(ES)** al especificado en `<hashCommitValue>` y pasa todo a la etapa de *staging* (listo para confirmar) **sin** borrar los cambios realizados hasta ese momento.
```powershell
git reset --soft <hashCommitValue>
```
<hr>

### Elimina **TODOS** los commits **POSTERIORES** al `<hashCommitValue>`
Esta acción eliminará todos los commits que existan después del `<hashCommitValue>` contemplado incluyendo las modificaciones actuales y regresando todo al estado original en el que se encontraba el proyecto hasta dicho punto de eliminación
```
git reset --hard <hashCommitValue>
```
<hr>

### Elimina el(los) commit(s) **POSTERIOR(ES)** al especificado en `<hashCommitValue>`
En este proceso se eliminarán los commits posteriores al `<hashCommitValue>` especificado y pasará todo a la etapa de *Working Area* sin borrar los cambios realizados hasta ese momento.
```powershell
git reset --mixed <hashcommitValue>

```
<hr>

### "*Revertir*" un commit
Este comando es más recomendado de utilizar ya que nos puede ayudar a evitar posible conflictos entre usuarios que intervienen en el mismo proyecto, contrario a lo que puede ocurrir con `git reset --flag <hashCommitValue>`
```powershell
git revert <hashCommitValue>
```
Adicionalmente, podemos utilizar la notación que vimos anteriormente, en la que se utiliza `HEAD` como puntero posicionado en el commit que se "revertirá" (o a los anteriores con `HEAD~value`) y utilizarlo en lugar de escribir el hash del commit involucrado:
```powershell
git revert HEAD | git revert HEAD~1 | git revert HEAD~2 | ...
```
`git revert HEAD` es equivalente a `git revert <hashCommitValue>`
En este caso, en la primera instrucción, `HEAD` se refiere al último commit creado y en la segunda instrucción,`<hashCommitValue>` debe ser el último *hash* creado.
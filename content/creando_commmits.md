## Creando nuestros primeros ***commits***

Ahora vamos a validar los conceptos de la confirmación de cambios en nuestro proyecto.  

Recapitulando, en nuestra carpeta de `pagina_web` habíamos creado tres archivos:
1. `index.html`
2. `styles.css`
3. `README.md`
Ahora vamos a nuestra terminal y ejecutemos `git status` y deberiamos tener algo como esto:
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
Ahora vamos a generar nuestro primer ***commit*** o **confimración** para pasar nuestros archivos a la etapa de *Repository*, esto creará un identificador del *commit* creado y pasará a formar parte de nuestro historial de cambios dentro de nuestro repositorio local (posteriormente podremos *subirlo* a internet usando el servicio de Github).  

Entonces, crearemos nuestro *commit* y el mensaje de dicho *commit* en la misma terminal de comandos: `git commit -m "Este es el primer commit del proyecto pagina_web"`.  

***Nota***: El mensaje lo puedes determinar de acuerdo a tus necesidades.  

Si todo esta bien, lo anterior debe arrojarnos algo como esto:
```powershell
$ git commit -m "Este es el primer commit del proyecto pagina_web"
[main (root-commit) b727b52] Este es el primer commit del proyecto pagina_web
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
 create mode 100644 index.html
 create mode 100644 styles.css
```
Esto ha creado nuestra primera confirmación dentro de nuestro historial con su proio identificador (*hash*) para su posterior manejo.  

Hasta este punto, los archivos generados están vacíos, es decir, no hemos agregado nada de contenido, entonces vamos a VS Code y abriremos la carpeta `pagina_web`, podremos ver los tres archivos creados. Abriremos el `index.html` y vamos a crear la estrusctura básica de una página web con HTML y guardamos los cambios:
```powershell
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  
</body>
</html>
```
Ahora, en nuestra terminal ejecutamos el comando `git status`, lo que nos debería arrojar algo como esto:
```powershell
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
Esto quiere decir que nuestro archivo `index.hmtl` ha sufrido cambioos y Git lo tiene en la etapa de *Working Directory* y listo para que sea agregado a la etapa de *Staging Area*.  

💣 ***Reto*** 💣 Agrega el archivo `index.html` a la etapa de "Staging Area"  

Ahora revisemos el estado de nuestro proyecto: `git status`, obtendremos algo similar a esto:
```powershell
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   index.html

```
Es tiempo de agregar una confirmación (*commit*).  

💣 ***Reto*** 💣 Realiza el *commit* correspondiente ***pero*** usando el editor de código, es decir, no agregues el comentario en la linea de comandos.  

Verificamos nuevamente el estado de nuestro proyecto, `git status`:
```powershell
$ git status
On branch main
nothing to commit, working tree clean

```
💣 ***Reto*** 💣 Agrega contenido a los archivos restantes: `styles.css` y `README.md`. Al finalizar la modificación de cada archivo, realiza lo siguiente (esto debes hacerlo por cada archivo):
1. Verifica el estado actual del proyecto.
2. Agrega el archivo modificado al *Staging Area*.
3. Verifica el estado actual del proyecto (*puedes hacer uso del comando `git diff`, observa el resultado*).
4. Realiza la confirmación (*commit*) de los cambios realizados junto con su mensaje correspondiente.
5. Verifica el estado actual del proyecto.

***Excelente*** Hasta este punto hemos podido crear un proyecto básico para la creación de una página web y llevar un control de los cambios realizados en nuestros archivos. Ahora veremos algunos de los comandos más utilizados para una gestión de nuestro proyecto más afondo.
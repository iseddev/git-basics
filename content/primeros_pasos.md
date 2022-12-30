## Primeros pasos 🚶‍♂️

Vamos a considerar que crearemos una página web sencilla. Para ello, el ejemplo siguiente considera un equipo con SO Windows, la terminal GitBash y el uso de VS Code  

Entonces lo primero será crear una carpeta para contener nuestro proyecto, en este caso la llamaremos `pagina_web`. Para ello, vamos a hacer uso de GitBash.

1. Estando en el escritorio de Windows, haremos *click* derecho con el "mouse" (debe ser sobre un espacio vacío) y del menú desplegable, seleccionaremos `Git Bash Here` , esto deberá abrir GitBash *posicionado* en el escritorio (`Desktop`).
2. Ahora ejecutaremos el siguiente comando: `git init pagina_web`. Esto creará la carpeta `pagina_web` e inicializará Git en dicha carpeta.
3. GitBash seguirá posicionado en `Desktop`, por  lo que ejecutaremos lo siguiente: `cd pagina_web`. Esto deberá posicionar GitBash en la carpeta `pagina_web` y tendriamos que ver algo como esto: `pcName@Sony-VAIO MINGW64 ~/Desktop/pagina_web (main)`.
4. Vamos a listar "*todos*" los archivos que existen dentro de `pagina_web`, para ello vamos a ejecutar lo siguiente: `ls -a`, esto nos debería poder listar la carpeta *oculta* `.git`
5. Limpiamos la pantalla de GitBash ejecutando: `clear` (*otra opción: `cls`*).
6. Ahora vanos a crear el archivo `index.html` ejecutando: `touch index.html`. ***Nota***: Para el caso de usar Windows Terminal, se puede utilizar: `New-Item index.html`
7. Volvemos a listar los archivos dentro de `pagina web`, pero ahora ejecutando solamente: `ls`, deberíamos poder ver el archivo creado `index.html`.
8. Ahora vamos a crear la carpeta/directorio `styles` ejecutando: `mkdir styles`.
9. Ejecutamos nuevamente `ls`, ahora deberiamos poder ver el listado con `index.html` y `styles/`
10. Ahora vamos a movernos dentro de `styles` con `cd styles`.
11. Ahora, ya dentro de la carpeta `styles` vamos a crear el archivo `index.css` con `touch index.css`.
12. Ejecutamos `ls` y deberíamos poder ver únicamente el listado con el archivo `index.css` ya que `index.html` no forma parte de la carpeta `styles`
13. Vamos a "*subir un nivel*" para posicionarnos nuevamente en `pagina_web` ejecutando: `cd ..`
14. Ahora vamos a eliminar la carpeta `styles` porque no queremos utilizar esta carpeta sino más bien queremos hacer uso del archivo `styles.css` directamente, para ello ejecutaremos el comando: `rm -r styles`, esto eliminará la carpeta `styles` y todos los archivos contenidos dentro de ella.
15. ***RETO*** Crea el archivo `styles.css`. Recuerda verificar que la terminal debe estar posicionada en la carpeta `pagina_web`
16. Ejecutamos el comando `ls` para validar nuestra estructura de archivos dentro de `pagina_web`. Hasta este punto deberiamos poder ver solamente: `index.html` y `styles.css`, ambos archivos forman parte de nuestra carpeta `pagina_web`
17. Ahora vamos a crear el archivo `README.md` con: `touch README.md`
18. ***RETO*** Lista los archivos dentro de `página_web`. Deberiamos poder ver los archivos siguientes: `README.md`, `index.html` y `styles.css`

Ahora pasemos a la acción directa con el uso de Git dentro de nuestro trabajo.
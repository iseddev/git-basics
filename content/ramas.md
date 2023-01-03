## Gestión de ramas o "**branches**" 🔃

En este apartado, vamos a ver lo relacionado al manejo básico de las ramas, o mejor conocidas como "***branches***".  

Cuando nuestro proyecto es robusto, cuenta con la colaboración de varios desarrolladores o por simple organización, se vuelve un poco complicado que se trabaje sobre una misma rama, pero, ¿qué es una rama? Bueno, lo primero a tener en cuenta es que en el momento en que creamos un repositorio en nuestro proyecto, por defecto se crea la rama principal ***main*** y podemos a comenzar a trabajar en nuestro desarrollo sin mayor contratiempo. Pero como se dijo anteriormente, si el proyecto lo requiere, es bueno pensar en "*dividir*" el flujo de trabajo en varios "*micro entornos de desarrollo*", donde cada integrante del equipo realizará sus aportaciones al proyecto.  

Por ejemplo, vamos a suponer que en nuestro proyecto hay un desarrollador frontend y un desarrollador backend, entonces para una mejor experiencia de trabajo, lo recomendable es que cada desarrollador haga uso de las ramas para que su trabajo no se vea afectado por el trabajo del compañero.  

Como ya hemos visto, al momento de crear un repositorio `git` en nuestro proyecto, por defecto se crea la rama ***principal*** `main`, esta rama es en la que se verá reflejado nuestro proyecto final y funcional. Por tanto y de forma práctica, es recomendable crear ramas alternas que no interfieran directamente con la rama `main`. Por ejemplo, para el frontend se podrían crear las ramas: `estructura` (para el proceso de la estructura del HTML), `estilos` (para la gestión de los estilos CSS) y `scripts` (para la gestión de la programación en JavaScript u otro lenguaje). Para el backend, se pueden crear las ramas: `formulario` (para la gestión del formulario de contacto), `login` (para la gestión del login de la página) y cualquier otra rama que nos sirva para trabajar en una característica o funcionalidad específica.  

Ahora bien, cuando creamos estas ramas y verificamos que lo realizado en cada rama esta funcionando como se espera, no se aplicarán los cambios a la rama `main` hasta que así lo especifiquemos.  

Una manera secilla de poder conceptualizar una rama es pensar en "*caminos*" o "*rutas*" de desarrollo *independientes*, pero que se mantienen en conexión al proyecto en general. Después de que en cada rama se llega un punto en el que el resultado es lo que se esperaba, se procede a la "fusión" a la rama principal. Esto ofrece una gran flexibilidad para no manipular directamente nuestro proyecto un sólo flujo (o rama), sino que tenemos la posibilidad de crear "ramificaciones" paralelas a nuestro proyecto y de esta manera podemos mantener un flujo de trabajo limpio y ordenado. Veamos los comando más utilizados en la gestión de ramas en Git:  

### Enlistar las ramas que existen dentro de nuestro proyecto
```powershell
git branch | git branch -l
```
<hr>

### Crear una nueva rama desde el punto donde estamos actualmente con el nombre especificado en `<branchName>`
Es importante tomar en cuenta que la creación de una rama se realizará desde el punto de la ultima confirmación creada. Esto se podrá visualizar posteriormente al solicitar el detalle de nuestro flujo de confirmaciones.
```powershell
git branch <branchName>
```
**Notas**:  
* *Para poder crear una rama, es necesario haber confirmado por lo menos un commit dentro de nuestro proyecto*.  
* *La creación de una rama no nos "posiciona" en ella*.  
* *La rama principal por defecto es **`main`**.*  

<br><hr>

### Crear una nueva rama desde el punto donde estamos actualmente con el nombre especificado en `<branchName>` y posicionarse en esta rama

```powershell
git switch -c <branchName>
```
<hr>

### Crear una nueva rama con el nombre especificado en `<branchName>`, en el commit especificado en `<hashCommitValue>` y posicionarse en esta rama

```powershell
git switch -c <branchName> <hashCommitValue>
```
<hr>

### Eliminar la rama especificada en `<oldBranchName>` y se crea una nueva rama en su lugar con el nombre especificado en `<newBranchName>`
```powershell
git branch -m <oldBranchName> <newbranchName>
```
<hr>

### Moverse a la rama especificada en `<branchName>` y se pasan las modificaciones pendientes a esta rama
En este caso, si no hemos confirmado los cambios realizados hasta el momento en nuestra rama actual, ahora se podran confirmar dichos cambios pero quedarán establecidas en la rama a la que nos cambiamos

```powershell
git switch <branchName>
```
<hr>

### Eliminar la rama especificada en `<branchName>`
```powershell
git branch -d <branchName>
```
<hr>

### Eliminar la rama especificada en `<branchName>` de forma "forzada"
```powershell
git branch -D <branchName>
```
<hr>

### Crear/recuperar una rama eliminada (con sus estados y confirmaciones) con el nombre especificado en `<deletedBranchName>` y con el *hash* especificado en `<hashCommitValue>`
```powershell
git branch -b <deletedBranchName> <hashCommitValue>
```
*IMPORTANTE*  
*Para recuperar una rama que se eliminó por alguna razón y no contamos con su numbre y/o el hash del commit en donde se creó, podemos hacer uso del comando `git reflog`, esto nos desplegará "**todo**" el historial de confirmaciones dentro de nuestro proyecto, por lo que ahora podremos obtener tanto el nombre de la rama eliminada como el commit en la que se creó. Ahora seremos capaces de recuperar nuestra rama y el estado en el que se encontraba mediante la ejecución del comando anterior: `git branch -b <deletedBranchName> <hashCommitValue>`, esto debe reestablecer nuevamente la rama en cuestión, incluyendo todos los cambios y confirmaciones que contenía*  
<br>

### **Fusionar ramas**

Una vez que haz terminado de confirmar todos tus cambios en tu rama trabajo y deseas agregar todos estos cambios al flujo de trabajo principal de la rama "*main*", lo que tienes que hacer es una "**fusión**" de ramas. Pero antes de todo, lo que tienes que tomar en cuenta, es que debes estar posicionado en la rama principal (***main***) para que se agreguen los cambios deseados en esta rama (*main*).  

Ahora verás como "*fusionar*" o unir una rama específicada a la rama principal.  

<br><hr>

### Fusionar la rama especificada en `<branchNameToMerge>` a la rama principal
Para este proceso, es importante tomar en cuenta la rama en la que estamos posicionados, ya que la rama actual será la que ***reciba*** todos los cambios y confirmaciones creados en la rama a fusionar. Por otro lado, es recomendable definir un mensaje descriptivo que de soporte a esta acción
```powershell
git merge <branchNameToMerge> -m "A descriptive message goes here..."
```
### Algunos problemas en el manejo de ramas
En ocasiones te enfrentarás algunos "*problemas*" al fusionar ramas, como por ejemplo, supongamos que creaste la rama `estilos`, realizas un cambio en el archivo `style.css` (por ejemplo) que involucarn las líneas `11, 12 y 13` de tu código, confirmas los cambios, te cambias a la rama `main` y sin darte cuenta (o por la razon que sea), realizas un cambio en el mismo archivo `styles.css` en las mismas líneas `11, 12 y 13`, confirmas este cambio y despues de un tiempo, procedes a fusionar la rama `estilos` con la rama `main`, esto creará un "*confilcto*" al momento de realizar la fusión.  

Para ello Git, te desplegará en el archivo involucrado (en este caso `styles.css`) los cambios que realizaste en una rama `estilos` y los cambios que realizaste en la rama `main` para que decidas los cambios que quieres que se confirmen, los que quieras que se ignoren, ignorar todos los cambios o aceptar todos lo cambios, tú lo decides, un ejemplo de este *conflicto* lo verás a continuación:
```powershell
h1 {
<<<<<<< HEAD (Current change)
  text-transform: uppercase;
=======
  font-size: 2.4rem;
>>>>>>> estilos (Incomming change)
}
```
La línea `<<<<<<< HEAD (Current change)` te indica que el cambio actual en la rama `main` (`HEAD` está apuntando a main) es `text-transform: uppercase;`, posteriormente, la linea con `=======` es una especie de separador, seguido de los cambios provenientes de la rama que se intenta fusionar (`estilos`), en este ejemplo `font-size: 2.4rem;`, por útlimo se finaliza con `>>>>>>> estilos (Incomming change)`, detallando de que rama proviene el cambio que provoca el conflicto en nuestra fusión.  

Ahora en tu archivo con el conflicto, debes decidir que cambios deseas conservar y posteriormente confirmar. Si deseas conservar ambos cambios, simplemnete elimina las lineas:  
```powershell
<<<<<<< HEAD (Current change)
=======
>>>>>>> estilos (Incomming change)
```
Quedando tu archivo de la siguiente forma:
```powershell
h1 {
  text-transform: uppercase;
  font-size: 2.4rem;
}
```
Procedes a guardar cambios, añadir el cambio al `staging area` (comando `git add`) y por último confirmar dicho proceso (comando `git commit`). Esto confirmará dichos cambios y actualizará tu archivo y tendrás tu flujo de trabajo limpio y sin conflictos.  

Si deseas omitir un cambio y aplicar otro, simplemente elimina las líneas de código que deseas borrar, guarda cambios, agrega el proceso al `staging area`, finaliza con la confirmación de tu proceso (`git commit`) y listo.  

Por último, en caso de que te "arrepientas" y decidas que no quieres realizar la fusión de ramas, puedes ejecutar el siguiente comando:
```powershell
git merge --abort
```
O si decides que siempre sí vas a continuar con la fusión, ejecuta el siguiente comando:
```powershell
git merge --continue
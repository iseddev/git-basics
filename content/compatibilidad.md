## **Compatibilidad entre SO's 📳**

Cuando te toque trabajar en un equipo con diversos desarrolladores, vas a encontrar que utilizan diversos sistemas operativos (SO's), tales como Windows, Linux, MacOS, etc. Esta diversidad hará que existan diferencias en el "*formato*" en el que se desarrollan y guardan los cambios en cada proyecto, es decir, cada SO utiliza una forma para considerar los caracteres de formateo, específicamente, al momento de dar `ENTER` para generar una nueva línea.

En Windows se agregan 2 caracteres especiales cuando creamos un "salto de línea":
* `CR` - Carriage Return
* `LF` -  Line Feed

Para el caso de Linux/MacOS, se agrega solo un caracter:  
* `LF` - Line Feed

Entonces lo recomendable es mantener un estándar de formateo (para este salto de línea) independientemente del SO en el que estés trabajando. A continuación se presenta una serie de pasos a seguir para poder estandarizar estos formateos y evitar en la mayor medida posible diferencias entre un SO y otro.  

> Configuración en Windows:
```powershell
git config --global core.autocrlf true
```
> Configuración en Linux/MacOS:
```powershell
git config --global core.autocrlf input
```
> Listar las configuraciones "**globales**" que Git tiene definidas por defecto y las que estableciste anteriormente.
```powershell
git config --global -e
```
Lo anterior debería arrojarte algo come esto (si estas usando Windows):
```powershell
[core]
	autocrlf = true
```
*Para más detalles del comando `git config` consulta [aquí](https://git-scm.com/docs/git-config "Documentación oficial")*.
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
- [Verificando estados del proyecto](./content/seguimiento_commits.md)
- [Gestionar archivos y commits](./content/gestionar_archivos_y_commits.md)
- [Gestión de ramas => **branches**](./content/ramas.md)

***Contenido pendiente de agregar...***

<!--
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
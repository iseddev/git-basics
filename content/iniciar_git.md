## Iniciar Git en tu proyecto 📲

Ahora que ya te aseguraste que tienes GIT en tu equipo y has establecido las configuraciones globales básicas, puedes empezar a utilizar Git en tus proyectos.  

Como ya vimos anteriormente, al iniciar un repositorio dentro de tu proyecto, serás capaz de "moverte" entre cada "confirmación" (commit) que hayas establecido.  

La primera opción es haber creado la carpeta de tu proyecto y posteriormente inciializar la consola de comandos en esta carpeta.
> Inicializar un repositorio dentro de la carpeta actual.
```powershell
git init
```
Con este simple comando habrás inicializado Git en la carpeta de tu proyecto, con lo que generará una carpeta "*oculta*" con las configuraciones propias de Git.

Otra opción es generar la carpeta de tu proyecto y el repositorio Git al mismo tiempo.

> Crear una carpeta de proyecto con el nombre `<directoryName>` e inicializar un repositorio dentro de este mismo directorio.
```powershell
git init <directoryName>
```

Una vez ejecutado de formacorrecta cualquiera de los comandos anteriores, podrás ver en tu terminal algo parecido a esto:
```powershell
userName@pcNAme MINGW64 ~/Desktop/ProjectDirectoryName (main)
$
```
*`(main)` se refiere a la "**rama principal**" de tu proyecto*. Más adelante se abordará el concepto de rama (***branch***).
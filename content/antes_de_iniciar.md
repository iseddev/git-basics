## Antes de iniciar con Git 馃П

Ahora es momento de empezar a trabajar con GIT.

Para ello, lo primero que tienes que hacer es verificar si tienes Git instalado en tu equipo, por lo que basta con que ejecutes en tu terminal el comando: `git`, si lo tienes instalado, se desplegaran las opciones de comandos con las que Git cuenta.  

Si no lo tienes instalado, dependiendo de tu SO, puedes instalarlo desde la terminal o puedes descargar GIT desde [aqu铆](https://git-scm.com/ "Descarga Git desde sitio oficial") y seguir las instrucciones para instalarlo en tu equipo. Regularmente, durante la instalaci贸n de Git, tienes la opci贸n de instalar la terminal ***GitBash***, que para efectos de una experiencia de manejo de una terminal, es recomendable que la instales para que la puedas utilizar como tu terminal predeterminada. Una vez instalaste Git o verificaste que ya estaba instalado, puedes verificar la versi贸n que tienes instalad.

> Validar la version de GIT instalada en tu equipo.
```powershell
git --version
```

## Configuraciones Globales 馃摑
Ya que has validado que tienes Git instalado en tu equipo, es tiempo de definir las configuraciones "***globales***" iniciales que GIT utilizar谩 en cada uno de los repositorios creados. "**globales**", quiere decir que estas configuraciones se aplicaran a cada proyecto gestionado con Git desde tu equipo/ordenador. Existe la opci贸nde realizar configuraciones locales, es decir, que dichas configuraciones ser谩n 煤nicamente aplicadas al proyecto actual en el que estas trabajando. Pero como se detall贸 anterioremente, es necesario que tu terminal est茅 posicionada en la carpeta de tu proyecto.  

> Establecer el nombre de usuario
```powershell
git config --global user.name "Your Real Name"
```
>Establecer tu correo electr贸nico
```powershell
git config --global user.email youremail@mail.com
```

> Establecer editor de texto por defecto. *En algunos casos GIT abrir谩 el editor de texto configurado para ingresar informaci贸n. En este caso, se configura VS Code.  Para ver las configuraciones m谩s utilizadas, consulta [aqu铆](https://github.com/israUni/curso-basico-git/blob/main/editors-config.md "Configuracion editores de texto")*.
```powershell
git config --global core.editor "code --wait"
```

El editor de texto que utilices es indiferente, pero debido a su gran dinamismo y plugins (extensiones), es recomendable (m谩s no obligatorio) hacer uso de Visual Studio Code, el cual lo puedes descargar desde [aqu铆](https://code.visualstudio.com/download "Descargar Visual Studio Code")

### Configuraciones extras
> Activar el uso de colores en la interfaz del usuario
```powershell
git config --global color.ui true
```
---
title: "PRIMEROS PASOS EN UNA SHELL UNIX"
date: 2022-04-25
description: "La shell de unix es una herramienta poderosa para desarrolladores y administradores de sistemas, este post es introductorio para quienes tienen su primer acercamiento a ella."
image: basic_shell/linux-laptop.png
---

Si son tus primeros pasos en Sistemas Operativos basados en Unix la línea de comandos podría parecer algo intimidante. Sin embargo no es tan dificil de usar. Todo lo que necesita para comenzar a utilizar la shell es aprender un par de comandos básicos y, además, útiles para su día a día.

Si bien la mayoria de sistemas operativos actuales basados en Unix vienen con una interfaz gráfica integrada y que además es fácil de usar, la línea de comandos es una herramienta que es de mucha utilidad que nos brinda más poder sobre nuestro Sistema operativo y acceso a funciones que de otra manera no serian posibles de usar mediante la interfaz gráfica.

En este post repasaremos algunos de los comandos de Unix más comunes con el fin de ayudar a que la introducción a su uso sea más ameno.

---

## Obtener información acerca de un comando. 👁‍🗨

Casi todos los comandos cuentan con más de una opción para su uso. Intentar memorizar todos los comandos y además, todas sus opciones sería una locura.
Por lo que Unix nos ofrece un par de comandos para ver todas las opciones de un comando en especifico.

### Comando **--help**
El comando **--help** nos devuelve una lista de los argunmentos de un determinado comando.

```bash
command_name --help
```

Si necesitamos saber las opciones de un comando primero escribiremos el nombre de dicho commando seguido de **--help** y se nos listarán las opciones mas importantes.

![help cat](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/cat%20help.jpg?raw=true)

### Comando **man**
Casi todos los comandos de Unix se distribuyen con una archivo man o "manual", es una forma de documentación que explica qué funciones realiza el comando, ejemplos de cómo utilizar el comando y además los argumentos que este acepta.

El comando man se utiliza para mostrar la página del manual de un comando determinado.

```bash
man command_name
```
![man cat](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/man%20cat.jpg?raw=true)

![man cat 2](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/man%20cat%202.jpg?raw=true)

---

## Navegando por el sistema de archivos. 📂

En linux cada archivo o directorio se encuentra debajo del directorio **root**, que es el primer directorio en el árbol de directorios. Se hace referencia al directorio **root** con una sola barra inclinada **/**.

En esta sección veremos los comandos utilizados para movernos entre directorios.

### Comando **pwd** (Print Working Directory)

Cada vez que trabajamos con una shell estamos trabajando dentro de un directorio.

**pwd** nos ayuda a saber en qué directorio nos encontramos actualmente.

![pwd](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/pwd.jpg?raw=true)

El comando muestra la ruta completa del directorío en el que nos encontramos.

### Comando **cd** ("change directory")

Este comando nos sirve para cambiar(movernos) de directorio en los sistemas basados en Unix.

Cuando no utilizamos ningún argumento **cd** nos lleva al directorio de inicio.

Supongamos que queremos movernos al directorio "prácticas" que se encuentra en mi sistema.

Para cambiar a un directorio podemos usar el nombre de la ruta absoluta o relativa.

Ruta absoluta(completa): Comienza desde el directorio **root**  

```bash
cd /home/washiprah/practicas
```

Ruta relativa: Relativo a un directorio actual.

```bash
cd practicas
```

Dos puntos (**..** ) uno seguido de otro representa al directorio principal, o viendolo de otra manera, al directorio inmediatamente superior al actual.

Retomando el ejemplo anterior: nos encontramos en el directorio

```bash
/home/washiprah/practicas
```

Para cambiar al directorio

```bash
/home/washiprah
```
que se encuentra un nivel por encima de nuestro directorio actual, debemos escribir

```bash
cd ..
```

![cd dos puntos](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/cd%20punto.jpg?raw=true)

Para subir dos niveles podemos poner

```bash
cd ../../
```
Lo cuál nos dejaria en el directorio de

```bash
/home/
```

Para poder volver al directorio del cual recien salimos con los dos puntos (**..**) podemos usar

```bash
cd -
```

En caso de que un directorio tenga espacios en su nombre,debemos utilizar una barra invertida por cada espacio \ para "escaparlos".

```bash
cd practicas\ blog
cd practics\ blog\ con\ espacios
```

![escape de espacios](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/nombre%20con%20espacios.jpg?raw=true)

---

## Trabajando con archivos y directorios. 📁📝

### Comando **ls** 
El comando **ls** posiblemente sea uno de los que más utilizarás ya que nos permite listar todos los archivos y directorios que se encuentran dentro de un directorio dado.

Cuando lo utilizamos sin argumentos ni opciones **ls** nos muestra una lista en orden alfabético de los nombres de todos los archivos que se encuentran en el directorio de trabajo actual: 

```bash
ls
```

![imagen ls](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/ls%20sin%20args.jpg?raw=true)

Para listar los archivos de un directorio especifico sin la necesidad de entrar a el debemos pasar la ruta al directorio como argumento:

```bash
ls weekly_mission_1
```
Por defecto **ls** muestra solo los nombres de los archivos y directorios, utilizando **ls -l** podemos imprimir una lista larga que nos muestra más información , como el tipo de archivo, los permisos, el propietario, el grupo, el tamaño, la fecha y el nombre del archivo.

>Sobre el tema de permisos,grupos y propietarios hablaré en otro post 👀👀

```bash
ls -l weekly_mission_1
```
Para tener un resultado similar podemos utilizar **ll**
```bash
ll weekly_mission_1
```
![ls l](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/ls%20l.jpg?raw=true)

El comando **ls** no enumera los archivos "ocultos" de manera predeterminada. Con archivo oculto me refiero a un archivo que comienza con **.** (.gitignore, .git, etc).

Para mostrar todos los archivos incluidos los ocultos podemos utilizar **ls -a**  y si lo queremos en manera de lista general podemos utilizar **ll -a** (podemos sustituir ls casi siempre por ll, lo unico que cambiará será la manera en la que se nos muestra en pantalla el listado de archivos y directorios, en lo personal utilizo más **ll** porque encuentro mas legible los archivos de arriba hacia abajo).

```bash
ls -a
o
ll -a
```

![ll a](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/lla.jpg?raw=true)

>recuerda que para ver el resto de opciones del comando ls puedes ejecutar **ls --help**

---

## Visualización del contenido de un archivo. 📑👀

### Comando **cat** 

Este comando nos permite imprimir en consola el contenido de uno o más archivos y fusiona (concatena) archivos agregando el contenido de un archivo al final del otro.

Para mostrar el contenido pase el nombre del archivo y/o archivos como argumentos.

Ejemplo con archivos **hola** y **mundo** previamente creados:
```bash
cat hola mundo
```
![cat hola mundo](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/cat%20hola%20mundo.jpg?raw=true)

![cat pokemon](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/cat%20pokemon.jpg?raw=true)

Es de gran utilidad el poder ver el contenido de un archivo sin siquiera abrirlo para tener una idea de su contenido o hacer una busqueda rápida en él.

> En un próximo post hablaré sobre una herramienta que nos ayuda a ponerle esteroides a nuestro comando cat para hacerlo mas legible aún **batcat** 👀

---

## Creación de archivos. 🖌📝

Existen direferentes maneras de crear archivos desde la linea de comandos, aquí te muestro un par de ellas.

### Comando **touch** 

Con este comando podemos crear uno o varios archivos vacíos de la siguiente manera. **touch <nombre del archivo\>**. 
Si el archivo que deseamos crear es para utilizarlo para una tecnología en especifico debemos agregar la terminación que nos indica la documentación de dicha tecnologia como pueden ser python: .py, javascript: .js, markdown: .md, etc...

En el siguiente ejemplo la primer linea crea solo un archivo javascript y en la segunda línea varios archivos de diferente extensión.

```bash
touch archivo1.js
touch archivo1.js archivo2.md archivo3.py
```

Si queremos crear archivos dentro de carpetas ya existentes debemos utilizar la siguiente nomenclatura.

```bash
touch carpeta1/subcarpeta1/pokemon.js carpeta2/subcarpeta2/pokemon.test.js
```

![touch sub](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/touch%20sub.jpg?raw=true)

Ahora bien,si lo que deseamos es crear más de un archivo en una dirección especifica que no es nuestro directorio de trabajo actual, tendremos que utilizar llaves (**{}**) y los nombres de los archivos separados con comas (**,**) para separar los nombres ya que de lo contrario el primer archivo si lo crearía en la ruta que pusimos, pero si el segundo lo ponemos con espacio lo crearia en el directorio de trabajo actual.

**❌NO HACER ESTO❌**

![no hacer esto](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/no%20hacer%20esto.jpg?raw=true)

**✅HACER ESTO✅**

![hacer esto touch](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/hacer%20esto.jpg?raw=true)

### Comando **echo** para creación de archivos.

El comando además de ser un tipo de **print** para consola nos permite crear archivos con contenido.

Para su uso debemos utilizar la siguiente nomenclatura:

```bash
echo "contenido aquí" > archivo
```

![echo](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/echo.jpg?raw=true)

Es especialmente util para crear archivos con información de una manera rápida sin tener que abrir un editor de texto.

---

## Creación de directorios. 🖌📁

### Comando **mkdir** (make a directory)

Podemos crear nuevos directorios (carpetas) usando este comando, para crear un nuevo directorio debemos pasar como argumento el nombre o si queremos crear varios directorios debemos pasar los nombres de cada directorio separados por espacio.

```bash
mkdir carpeta1
mkdir carpeta1 carpeta2 carpeta3
```

![mkdir](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/mkdir.jpg?raw=true)

**mkdir** también nos permite crear directorios dentro de directorios, con la condición de que al direcotorio al que le querramos crear una subcarpeta ya exista.

```bash
 mkdir carpeta1/subcarpeta1 carpeta2/subcarpeta2 carpeta3/subcarpeta3
```

![sub mkdir](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/mkdir%20sub.jpg?raw=true)

---
## Eliminación de archivos y directorios. ✂📑📂

### Comando **rm** 

Por defecto este comando no elimina directorios que no elimina directorios. Tampoco pregunta al usuario si desea continuar con la eliminarción de un archivo por lo que debemos estar atentos al utilizarlo.


### Eliminar archivos.

Para eliminar un archivo debemos poner el comando seguido del nombre del archivo.

```bash
rm hello.py
```

![rm py](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/rm%20py.jpg?raw=true)

rm acepta uno o más nombres de archivos o directorios(carpetas) como argumentos.

Si colocamos la opción **-i** al utilizar rm, este nos preguntará si deseamos eliminar el archivo.

![rm i](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/rm%20i.jpg?raw=true)

Recuerda que si tienes mas de un archivo los puedes eliminar todos utilizando el simbolo de asterisco (*) por ejemplo si tienes mas de un archivo js puedes poner:

```bash
rm *.js
```

Con lo cual eliminaria todos los archivos .py del directorio de trabajo actual o si lo deseamos podemos especificar una ruta.

```bash
rm projects/archivos/*.py
```

![archivos eliminados asterisco](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/eliminar%20asterisco.jpg?raw=true)

### Eliminar directorios(carpetas).
Para eliminar directorios es necesario utilizar la opción **-r** para que se haga una eliminación de maner recursiva

![rm r](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/rm%20r.jpg?raw=true)

De esta manera eliminarmos una carpeta y todos los archivos y directorios que está tenia dentro.

>❌CUIDADO❌ al utilizar el comando rm ya que puedes eliminar por accidente archivos o directorios importantes, cerciorate de que los nombres que pasas como argumentos para eliminar sean los correctos!


---

## Copiar archivos y directorios. 📝➡📃

### Comando **cp** (Copy a file)

Este comando nos permite copiar tanto archivos como directorios.

Para copiar un archivo dentro del directorio de trabajo actual, se debe usar el archivo fuente (lo que se quiere copiar) como primer argumento y el nuevo archivo como segundo argumento:

```bash
cp file file_copy
```

![file copy](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/copy.jpg?raw=true)

Para copiar un archivo a otro directorio, se debe especificar la ruta absoluta o relativa según sea el caso. Cuando solo se especifica el nombre del directorio como destino, el archivo copiado tendrá el mismo nombre que el archivo original.


```bash
cp pokemon.test.js ../../carpeta1
```

![moviendo a carpeta](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/cp%20to%20carpeta.jpg?raw=true)

De forma predeterminada si el archivo de destino existe solo se sobreescribirá.

Para copiar directorios, incluidos todos sus archivos y subdirectorios, debe utilizarse la opción **-R** o **:-r**

```bash
cp -R carpeta2/ carpeta3/
```

![carpeta 3](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/carpeta3.jpg?raw=true)

Si la carpeta a la que se mandará la copia no existe, puede nombrarla en este momento, se creará y dentro de ella se meterá la copia.

---

## Mover y renombrar archivos y directorios. 📝➡📂

### Comando **mv**

Este comando puede ser utilizado tanto para mover archivos y directorios(carpetas) como para renombrarlos.

Por ejemplo para mover un archivo a un directorio se utilizaria.

```bash
mv archivo_a_mover.js carpeta1
```

![moviendo archivo](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/mover%20archivo.jpg?raw=true)

El punto(**.**) al utilizar el comando mv hace referencia al directorio de trabajo actual. (me gusta decirle "traer" xd) de la siguiente manera podemos mover archivos o carpetas que se encuentren en otro directorio hasta el directorio en el que nos encontremos.

```bash
mv carpeta1/archivo_a_mover.js .
```
![moviendo archivo aqui](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/aqui%20punto.jpg?raw=true)

Para mover varios archivos y directorios a la vez recuerda que el último directorio que pongamos es el directorio destino (al que le enviaremos lo que querramos)

```bash
mv archivo1 archivo2 carpeta1 /<carpeta-destino> 
```

### Renombrando 

Para cambiar el nombre de un archivo o carpeta solo hace falta recordar que el primer argumento es el archivo/directorio al que queremos cambiar el nombre, y el segundo argumento es el nombre que queremos ponerle.

```bash
mv archivo_a_mover.js archivo_renombrado.js 

mv carpeta1 carpeta_renombrada
```
![archivo renombrado](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/basic_shell/renombrado.jpg?raw=true)

![carpeta renombrada](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/carpeta%20renombrada.jpg?raw=true)

No solo puedes cambiar el nombre del archivo sino también su extensión, este comando es útil cuando nos equivocamos en el nombre de archivo o directorio.

---

## Elevar privilegios. 🚀

### Comando **sudo**

Este posiblemente sea uno de los comandos que más vas a utilizar cuando estés en la shell unix. Permite ejecutar programas como otro usuario, que por defecto es el usuario **root**, el usuario con mayor privilegio en nuestro sistema operativo.

Usar **sudo** en lugar de iniciar sesión como **root** es más seguro porque otorga privilegios limitados a usuarios individuales sin que conozcan la contraseña de usuario **root**.

>Esto será extendido en el post de privilegios.

Para usar **sudo** basta con que sea colocado como prefijo...

Como pudiste ver en capturas de pantallas anteriores utilizo un comando **tree** para que se me muestren los archivos y directorios como un arbol, si lo ejecutas posiblemente te marque error, este es buen momento para usar el comando **sudo** , para instalar el comando tree (y casi todos los programas o comandos se instalan así en linux).

```bash
$ sudo pacman -S tree # Arch Linux
$ sudo apt-get install tree # Ubuntu  
$ sudo aptitude install tree # Debian
``` 
(el comando apt-get cambiará dependiendo de tu distribución unix)

En este ejemplo instalamos un comando con privilegios de root sin ser root, solo proporcionando la contraseña del propio usuario.

---

## Conclusión 🚀🤖

En este post hemos cubierto alguno de los comandos mas utilizados de Unix.

Si bien se pueden realizar estas tareas desde una interfaz gráfica... realizarlos desde una línea de comandos te puede hacer más productivo y puedes hacer más en menos tiempo. Aunque no se cubre en este post, la terminal te da la posibilidad de automatizar tareas repetitivas creando tus propios comandos, con lo que podrias aumentar aún mas tu productividad y agilidad.

Recomiendo encarecidamente que practiques los comandos creando tus carpetas, archivos, renombrandolos.... y basicamente repitiendo lo que plasmo aquí, esto para que te acostumbres a trabajar en la terminal y pronto verás que te sentirás como pez en el agua.

Por mi parte es todo y como mencioné en algunos puntos, crearé otros posts referentes a este tema ya que considero requieren su propio post.

Hasta los próximos! 👽 ah sí, siganme en twitter que tengo twitter :D.

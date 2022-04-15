---
title: "Tuneando tu WSL con ZSH,OH-MY-ZSH, Y POWERLEVEL10k"
date: 2022-04-13
description: 'Recientemente descubrí WSL y me encantó la idea de fusionar linux con windows.'
---

Recientemente conocí WSL ( Windows Subsystem for Linux) y se me hizo interesante tener una shell linux dentro de windows ya que ciertos programas no los soporta Linux y los suelo usar a menudo, pero me gusta bastante ese entorno de trabajo para desarrollo por lo que decidí darme la oportunidad de probarlo. Pero como trabajar en una bash default no es tan divertido.

![bash](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/ubuntu_view.jpg?raw=true)

Decidí configurar la shell para dejarla como la tengo en los sistemas Linux que suelo utilizar.

![zsh](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/washi_config_colors.jpg?raw=true)

Lo cual me llevó a escribir este post para aquellos que también quieran personalizar su WSL.

---


En este post encontrarás los pasos para poder tunear tu WSL (versión 1 o 2), instalaremos la "Terminal de windows" que es un proyecto de código abierto de Microsoft. Instalaremos la "zsh" para sustituir la "bash" que WSL instala por defecto. Con estos cambios seremos capaces de cambiar el look de  nuestra terminal y ponerle todo el estilo que querramos, y adicionalmente la zsh nos permite instalar plugins para agregarle funcionalidades de manera fácil. Para seguir este tutorial se presupone ya se tiene instalada la WSL,  si no es así aquí un [link](https://docs.microsoft.com/en-us/windows/wsl/install) que te llevará a la documentación oficial de Microsoft (es fácil pero es bueno saber más cosas de esta tecnología ;))


___


## INSTALANDO LA WINDOWS TERMINAL

1. Para instalar la windows terminal basta con ir a la microsoft store, para esto presionaremos la tecla windows en nuestro teclado y escribiremos "microsoft store" e ingresaremos a la app. Una vez cargada desde el buscador teclearemos "windows terminal" y clickearemos al botón de "Obtener" y ¡listo! ya tenemos la windows terminal instalada.

    ![download windows terminal](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/download_windows_terminal.jpg?raw=true)

2. Para abrirla  basta con presionar la tecla windows, teclear "terminal" y posteriormente dar enter.

    ![open windows terminal](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/search_windows_terminal.jpg?raw=true)

3. Una vez se abra la terminal nos aparecerá por defecto una powershell (esto podemos cambiarlo despúes), para acceder a nuestra shell bash de ubuntu daremos click en el simbolo 'v' (número 1 en la imagen) y en la lista desplegada seleccionaremos ubuntu (número 2 en la imagen) o la distribución linux que usted haya descargado.

    ![open ubuntu shell](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/open_ubuntu_shell.jpg?raw=true)

4. y tadaaan,he aquí nuestra no tan llamativa bash.

    ![ubuntu view](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/ubuntu_view.jpg?raw=true)


----


## INSTALANDO LAS NERD-FONTS EN WINDOWS.

Para poder hacer que la windows terminal pueda renderear los íconos que utilizaremos en la shell zsh necesitamos instalar alguna nerd-font, en este punto dejémoslo como una mauskeherramienta que nos ayudará mas tarde.

1. Nos dirigiremos a la web de [nerd-fonts](https://www.nerdfonts.com/), dentro de la web clickearemos en "FONTS DONWLOADS" para que nos lleve a las fuentes disponibles para descargar.

    ![nerdfonts downloads](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/nerdfonts_downloads.jpg?raw=true)

2. Para fines del tutorial y por gusto personal descargaré la fuente "Caskaydia Cove Nerd Font" ya que es la misma fuente que utilizo en vscode, para descargar la fuente basta con dar click en el botón de descargar, lo cual nos guarda un archivo .zip  .

    ![download font](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/donwload_font.jpg?raw=true)

3.  Una vez terminada la descarga nos dirigiremos a la carpeta donde guardamos el archivo, al descomprimirlo nos mostrará 4 archivos de fuente, para instalar la fuente que queremos (en nuestro caso la "Caskaydia Cove Nerd Font Complete Mono") daremos doble click en el archivo y después a instalar.

    ![install nerdfont](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/install_nerdfont.jpg?raw=true)


---


## INSTALANDO LA SHELL ZSH EN WSL / WSL2.

Ahora necesitaremos instalar la shell zsh en nuestro wsl o wsl2, es algo fácil de hacer con un par de líneas de comando, esto ejecutandolo dentro de nuestro Ubuntu wsl que abrimos al finalizar la parte de instalacion de windows terminal. Si instalaron una distribución de linux diferente puede consultar la documentación de zsh o la documentación de su administrador de paquetes.

1. Ejecutaremos primero 2 lineas de comando, la primera para actualizar los paquetes disponibles y sus versiones, y el segundo para instalar o actualizar los paquetes que el comando anterior encontró y listó (cuando lo ejecutemos nos pedirá la contraseña sudo, es la que configuramos una vez se instaló WSL).

    ```console
    sudo apt-get update
    sudo apt-get upgrade```

2. Una vez se haya terminado de realizar el upgrade instalaremos la zsh con la siguiente línea .
    
    `
    sudo apt install zsh -y
    `

### INSTALANDO OH-MY-ZSH.
Es una extension de configuración para la shell zsh. Con ella podremos personalizar fácilmente cualquier cosa en la shell, instalar un tema y poder agregar pluggins.

1. Para su instalación simplemente debemos ejecutar el siguiente comando (puede copiarlo y pegarlo directamente en su shell).

    ```
    sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    ```

    Una vez instalado nos preguntará si deseamos cambiar la shell por defecto a zsh y debemos presionar la tecla "Y" para confirmar.

Si desea puede consultar la documentación de [zsh](https://zsh.sourceforge.io/) y [oh-my-zsh](https://ohmyz.sh/).


---


## INSTALANDO EL TEMA POWERLEVEL10K.
A continuación instalaremos el tema "powerlevel10k" que nos permite personalizarlo a nuestro gusto de una manera sencilla. Y cuenta con un asistente de configuración el cual es el que hace que sea fácil instalar y personalizar el tema.

1. Para instalarlo ejecutaremos el siguiente comando en la terminal (puede copiarlo y pegarlo en su shell).

    `
    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k`

2. Para activar el tema debemos editar el archivo "~./zshrc" que se encuentra en nuestra carpeta de usuario. Para acceder a dicho archivo teclearemos el siguiente comando en la terminal, sientase libre de utilizar el editor vim o nano, en este tutorial utilizaré el editor nano.

    ` nano ~/.zshrc `
    
    Este comando nos abrirá el siguiente archivo, en el cuál debermos cambiar **ZSH_THEME=”robbyrussel”** por **ZSH_THEME=”powerlevel10k/powerlevel10k”** , para guardar cambios en el editor nano basta con presionar "ctrl S" y para salir del editor debemos presionar "ctrl x".
    
    ![changue theme](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/zsh_theme_change.jpg?raw=true)

    Si decidió utilizar el editor vim, para editar el archivo primero debe presionar la tecla "i" para que pueda editar el documento, una vez realizado el cambio debe guardar y salir del edito, esto lo logrará presionando la tecla de escape para salir del modo de inserción, después teclar lo siguiente ":wq" (dos puntos, wq) para que se escriban los cambios y salga del editor (ATENCION: despues de precionar la tecla de escape "Esc" todo lo que escriba se reflejara en la parte inferior de la pantalla como se muestra a continuación).

    ![vim changue theme](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/change_zsh_path_vim.jpg?raw=true)
    
    Listo, tema activado pero para ver los cambios debemos reiniciar la terminal (cerrarla y abrir una nueva shell ubuntu)

Si desea puede consultar la documentación del tema [powerlevel10k](https://github.com/romkatv/powerlevel10k)


---


## CONFIGURACION DE FUENTES EN WINDOWS TERMINAL.

En cuanto se abre la terminal nos muestra la siguiente pantalla preguntando si podemos ver algo que parece... ¿¿un diamante..?? 

![start p10k configure](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/start_configure_p10k.jpg?raw=true)

¿Cuáles diamantes? si solo tenemos 2 cuadros con signos de interrogación en la pantalla. Bien, en pasos anteriores descargamos una fuente de Nerd-fonts y sí, ha llegado el momento de utilizar esa mauskeherramienta secreta.

1. Primero nos dirigiremos a la sección de configuración de la windows terminal, como se muestra en la siguiente captura de pantalla.

    ![open configuration](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/open_config.jpg?raw=true)

2. Ya dentro de las configuraciones buscaremos la opción de "Ubuntu" (o la distribución de linux que haya instalado) dentro de los perfiles, y le daremos click,dentro de los valores predeterminados nos moveremos al apartado de apariencia donde se encuentra la opción de cambiar fuente.

    ![Select font](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/select_font.jpg?raw=true)

3. Seleccionamos la fuente que instalamos y guardamos los cambios.

    ![save font](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/select_save_font.jpg?raw=true)

4. Volvemos a nuestra shell y ¡EURECA! al fin vemos el diamante.

    ![eureca](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/diamont.jpg?raw=true)

> Si no le aparece la fuente es posible que su sistema operativo aún no la detecte, si despues de presionar en mostrar todas las fuentes sigue sin aparecerle, sugiero que reinicien su sistema operativo y vuelva a abrir la windows terminal para seleccionar la fuente.

> Si despues del reinicio no le aparece la pantalla de la powerlevel10k donde pregunta por el diamante no se preocupe, solo escriba en su temrinal `p10k configure` y podrá acceder a dicha pantalla.


---


## CONFIGURACION DE LA POWERLEVEL10K.

Ahora que podemos ver el diamante estamos listos para inicar con la configuracion de la powerlevel10k.
>¡IMPORTANTE!: Los pasos que describiré a continuación son para dejar la shell con la configuración que a mi me gusta y con la que me siento cómodo, sientase libre de experimentar las dierentes opciones que nos ofrece la powerlevel10k que como verá, es fácil de configurar.

> Si en un futuro desea cambiar su configuración para probar nuevas opciones basta con ejecutar `p10k configure` en su shell para poder iniciar el proceso de configuración.

1. A la pregunta de si podemos ver el diamante responderemos con sí presionando la tecla "y" (si es que lo vemos, sino, revisar los pasos anteriores.)

    ![diamont](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/diamont.jpg?raw=true)

2. A la pregunta de si podemos ver el candado respondemos sí presionando la tecla "y".

    ![lock](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/lock.jpg?raw=true)

3. A la pregunta de si podemos ver el logo de Debian respondemos sí presionando la tecla "y".

    ![debian](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/debian.jpg?raw=true)

4. A la pregunta de si podemos ver los iconos sin que se solapen con las X  respondemos sí con y, si a usted le aparecen algunos iconos solapados pero en los anteriores 3 pasos pudo ver sin problemas los iconos no se preocupe, puede dar sí presionando la "y"

    ![overlap](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/icons_overlap.jpg?raw=true)

5. De la lista de prompt style seleccionaré la Classic, esto presionando la tecla número 2.

    ![prompt](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/promp_style.jpg?raw=true)

6. Del character set elegiré el Unicode (tecla 1).

    ![character](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/character_set.jpg?raw=true)

7. Del prompt color elegiré el Darck (tecla 3).


8. Como no deseo mostrar la hora actual elegiré la opción 1 presionando la tecla número 1.

    ![current time](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/current_time.jpg?raw=true)

9. El separador que me gusta es el de ángulo por lo que presiono la tecla número 1.



10. Para el prompt head me gusta el difumidado (la opción Blurred) por lo que presiono la tecla 2.

    ![prompt head](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/prompt_head.jpg?raw=true)

11. Para la prompt tail elijo el difuminado también, presionando la tecla 2.

    ![prompt tail](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/prompt_tail.jpg?raw=true)

12. El prompt height me gusta que sea de una sola línea, así que elijo la opción 1.

    ![prompt height](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/prompt_height.jpg?raw=true)

13. El prompt spacing lo selecciono sparce, presionando la tecla 2.

    aqui va la imagen


14. Para los íconos selecciono  la opción 2 para así poder ver mas detalladamente algunas cosas como git. Presionando la tecla 2.

    ![icons](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/icons.jpg?raw=true)

15. El prompt flow lo dejaré en Fluent, presionando la tecla 2.

    ![prompt flow](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/prompt_flow.jpg?raw=true)

16. Activaré el aviso transitorio, presionando la tecla "y", esto para que el resultado de los comandos me aparezcan en la parte de arriba y no por abajo.

    ![prompt transient](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/transient_prompt.jpg?raw=true)

17. En el prompt mode seleccionaré la opción Quiet, presionando la tecla 2.

    ![prompt mode](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/prompt_mode.jpg?raw=true)

18. Seleccionamos la opción de sí para aplicar y guardar los cambios ( en mi caso como ya tenia una instalación previa me pregunta si quiero sobreescribir el archivo, también daré que sí) esto presionando la tecla "y".

    ![accept](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/last_confirm.jpg?raw=true)

19. Listo! hemos configurado la powerlevel10k y este es el resultado final.

    ![final 1](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/final_prompt.jpg?raw=true)
    ![final 2](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/final_final_prompt.jpg?raw=true)


Hasta aquí nuestra shell ya está configurada y puede ser utilizada tal cual, pero, a pesar de eso hay algunas modificaciones adicionales que se le pueden hacer ya que la p10k nos lo permite, esto como dije ya es a gusto personal y pueden o no seguir con el tutorial a partir de aquí, si aún hay alguien que quiera seguir pues adelante! vamos a darle esos últimos retoques a nuestra shell. Si decides no continuar con esta parte puedes dirigirte a la sección de más abajo **POWERLEVEL10K PARA EL SUPER USUARIO**


---


Bien, comencemos quitando ese componente de la derecha del todo ya que a mí no termina de convencerme, para eso nos dirigiremos al archivo editable de la p10k. 

`nano ~/.p10k.zsh `

Donde como dije, quitaremos los elemento de la derecha.
Para ello comentaremos todas las líneas de la lista de elementos de la derecha, desde "status" hasta "example".

![right bar](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/right_bar1.jpg?raw=true)
![right bar end](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/end_right_bar.jpg?raw=true)

y con esto hemos quitado ese elemento, pero hay algunas caracteristicas visuales útiles que quisiera conservar, las cuales las agregaré al segmento de la izquierda, los cuales son status,command_execution_time y context.

![left bar](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/left_bar.jpg?raw=true)

Guardamos y para ver los cambios es necesario reiniciar la shell, basta con cerrar la actual y abrir una nueva de shell de ubuntu

![final shell](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/shell_final1.jpg?raw=true)

Como se puede observar ya no existe la columna con elementos a la derecha.

En el archivo ~/p10k.zsh puedes configurar absolutamente todo del tema, desde íconos hasta colores pero eso excede al alcance de este pequeño tutorial. 


---


## POWERLEVEL10K PARA EL SUPER USUARIO

Si nos colocamos como SUPER USUARIO `sudo su` veremos que nuestra shell tuneada no está igual y eso es un poco triste, pero basta con realizar los mismos pasos que hicimos como usuarios normales. Solo la instalación de la powerlevel10k y la configuración de la misma (lo del diamante).

![sudo su](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/root.jpg?raw=true)

Para instalar la powerlevel10k en el super usuario primero debemos instalarla, para ello ejecutaremos el siguiente comando.

`git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc`

Despues de ejecutar el comando de arriba debemos teclear `zsh` para acceder a la pantalla que nos muestra el diamante y a partir de aquí puede ejecutar exactamente los mismos pasos que en el apartado de **CONFIGURACION DE LA POWERLEVEL10K** y obtendremos el siguiente resultado. 

![after root](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/after_root.jpg?raw=true)

Para realizar la configuración de quitar los elementos de la derecha es el mismo procedimiento, entramos al archivo.

`nano ~/.p10k.zsh`

Y comentamos todos los elementos de la derecha, desde "status" hasta "example".

Y agregaremos los mismos 3 elementos a la izquierda, status,command_execution_time y context.

Reiniciamos la shell una vez mas (cerrarla y abrir una nueva), nos ponemos como super usuario una vez mas `sudo su` y tecleamos `zsh` para ver nuestros cambios Pero... no tenemos un identificador que usuario somos, si normal o super usuario por lo que debemos hacer unos ajustes.

Como sabemos el identificador de super usuario suele ser el simbolo gato "#", por lo que es lo que agregaremos a continuación, para sustituir todo el texto de "with root@desktop..".


![root with](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/root_with.jpg?raw=true)

Nuevamente ingresamos a `nano ~/.p10k.zsh` y realizaremos los siguientes cambios. Ya dentro del archivo si lo abrimos con el editor nano presionaremos la combinación "ctrl w" para abrir el buscador del editor y escribiremos "root_template" para que nos lleve al apartado que nos interesa.

![root template](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/root_template.jpg?raw=true)

Y comentaremos la línea que dice " typeset -g POWERLEVEL9K_CONTEXT_PREFIX='%246Fwith ' ".

![root template commet](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/root_template_comment.jpg?raw=true)

Para poner el simbolo de "#" lo tomaremos de la página de [Nerd-fonts](https://www.nerdfonts.com/cheat-sheet), nos dirigiremos a la sección de íconos donde buscaremos "hashtag" y copiaremos el ícono que nos muestra.

![icon font](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/copy_icon.jpg?raw=true)

Ahora volvemos a nuestro archivo `.p10k.zsh` y en la línea

 "  # Context format when running with privileges: bold user@hostname.
  typeset -g POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE=''" "

pegamos nuestro hashtag despues del igual.

![hashtag](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/hashtag_changing.jpg?raw=true)

Reiniciamos la shell una vez mas (cerrarla y abrir una nueva), nos ponemos como super usuario una vez mas `sudo su` y tecleamos `zsh` para ver nuestros cambios, sé que hacer estos pasos pueden ser algo redundantes y es por eso que en el siguiente punto lo que haremos será establecer la zsh como la shell predeterminada para todos los usuarios.


----

## ESTABLECIENDO ZSH COMO SHELL DEFAULT PARA TODOS LOS USUARIOS DEL SISTEMA

Si ejecutamos el comando 
```
cat /etc/passwd | grep -E "^root|^washiprah" 
``` 
sin miedo, solo es para listar la shell de estos dos usuarios uwu (donde washiprah lo sustituirá por su usuario)
nos daremos cuenta que solo el usuario del sistema tiene la zsh como default, pero el root(super usuario) y los demás usuarios que agreguemos tendrán por defecto la bash.

![default bash](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/default_bash.jpg?raw=true)

Para realizar esto debemos ejecutar la siguiente línea de código en la shell pero estando como super usuario `sudo su` y despues tecleamos `zsh`. 

`usermod --shell /usr/bin/zsh root`

Volvemos a ejecutar el comando `cat /etc/passwd | grep -E "^root|^washiprah"` y podemos observar que ahora tanto el usuario normal como el super usuario tienen por defecto una shell zsh y se verá así.

![zsh default](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/zsh_both.jpg?raw=true)

Ahora si ejecutamos `sudo su` veremos que nuestra shell para usuario y super usuario es una zsh (nota, para salir de super usuario debemos teclear "exit"). :D al fin!

Hemos terminado este pequeño tutorial donde tuneamos nuestra shell, como dije, powerlevel10k nos permite personalizar tanto como querramos nuestra shell, desde colores, íconos, fuentes, y adicional con zsh podemos tener pluggins que nos ayudan en cuanto a productividad pero esto se encuentra en su documentación en [github](https://github.com/romkatv/powerlevel10k).

![sell](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/washiprah.jpg?raw=true)


---

## CONFIGURACIONES EXTRAS Y OPCIONALES EN WINDOWS Terminal

Bien, es el fin no fin jaja, no queria irme sin mostrarles 
algunas configuraciones extras que tengo en mi windows terminal, para este pundo asumo que sabemos como llegar a la configuración de apariencia de Ubuntu en la windows terminal.

### Apariencia 

Comenzaremos modificando algunos puntos dentro del apartado de apariencia.

1. Windos terminal nos permite elegir los colores para nuestra terminal, esto en el apartado "combinacion de colores", añadimos uno nuevo y elegimos a nuestro gusto, yo tengo esta combinacion de colores.

    ![color](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/colores_sistema.jpg?raw=true)

2. Para poner la combinacion de colores que queremos nos dirigimos a Ubuntu/Apariencia, dentro de esta sección encontramos el apartado de "Combinacion de colores" donde buscaremos la combinacion de colores creada por nosotros y la seleccionamos.

    ![colors ubuntu](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/washi_colors.jpg?raw=true)

3. Adicionalmente windows terminal nos permite poner una imagen de fondo en la terminal, podemos poner la imagen que tenemos en nuestro desktop o tambien podemos elegir una imagen diferente buscando la ruta. Yo tengo la imagen de mi fondo de pantalla seleccionada con una transpariencia de 35% 

    ![image](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/background_image.jpg?raw=true)

4. Al final de todo el apartado de apariencia viene la opción de "Visibilidad de la barra de desplazamiento", la cual desactivo para que no me aparezca en la shell.


5. Guardamos los cambios dando click en el botón de guardar y ya se reflejan en nuestra shell. 

    ![mi shell](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/washi_config_colors.jpg?raw=true)


### Avanzado

En este punto ya estamos a unos pasos de terminar!! solo haremos un par de cambios en el apartado avanzado dentro de la ruta "Ubuntu/avanzado.

- Cambiaremos solo 2 cosas más
    
    1. El tamaño del historial, esto es personal, yo solo dejo el tamaño en 50.
    2. Desactivo la notificación de campana para que deje de estar sonando cuando sucede algo inesperado.

    ![last configurations](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/zsh/final_washi_config.jpg?raw=true)


---


Windows Terminal nos permite crear diferentes combinaciones de configuración, personalizandolo a nuestras preferencias y sería bueno explorarlo para llegar a nuestra propia combinación ganadora.

Por mi parte es todo en este post y espero les haya sido de ayuda, nos vemos en los siguientes que tengo en mente. 

Hasta los próximos!.

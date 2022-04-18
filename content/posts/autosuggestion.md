---
title: "INSTALACIÓN DEL PLUGGIN AUTOSUGGESTION PARA OH-MY-ZSH"
date: 2022-04-18
description: 'En este post mostraré los pasos necesarios para instalar un pluggin que predice comandos para zsh y nos ayuda a aumentar la ágilidad en la shell'
---
En un post anterior mostraba cómo instalar zsh y oh-my-zsh y en él hablaba un póco de cómo esta shell nos ayudaba a ser más productivos gracias a la posibilidad de instalar plugins que nos facilitaran tareas repetitivas.

En esta ocasión estaré mostrando los pasos necesarios para instalar un pluggin de sugerencia de palabras en la terminal para no tener que escribir 2 veces comandos largos.

Al final del post nuestra terminal podrá sugerirnos palabras o comandos completos a partir de las letras que vayamos escribiendo.

![root autosugges](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/autosuggest/sudo_autosuggestion.jpg?raw=true)

1. 1.Primero nos dirigiremos a nuestro directorio dónde pondremos nuestros plugins dentro de oh-my-zsh, con el siguiente comando de consola.

    ```bash
    cd ~/.oh-my-zsh/custom/plugins/
    ```

2. 2.Una vez dentro del directorio "pluggins" clonaremos el repositorio de "autosuggestion" con **git clone** [Link al repositorio](https://github.com/zsh-users/zsh-autosuggestions.git)
    ```bash
    git clone https://github.com/zsh-users/zsh-autosuggestions.git
    ```
    y esperaremos a que termine de clonar el repositorio.

3. 3.Ya clonado el repositorio agregaremos el plugin al archivo de **zshrc** , para ello nos introduciremos en él.
    ```bash
    nano ~/.zshrc
    ```
    Presionaremos la combinación de teclas (en el editor nano) **ctrl w** para que nos abra el buscador y buscaremos "plugins".
    
    ![search plugins](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/autosuggest/search_plugins.jpg?raw=true)

    agregaremos la línea **zsh-autosuggestions**
    
    ![add line](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/autosuggest/plugin_add.jpg?raw=true)

    Guardaremos **ctrl s** y saldremos del editor **ctrl x**

4. 4.Ya en la línea de consola escribiremos
    ```bash
    source ~/.zshrc
    ```
    Esto para ejecturar el archivo y una vez termine cargará los cambios que hicimos en él.

5. 5.Listo! si todo ha salido bien veremos que si escribimos una letra automaticamente nos aparecerá una sugerencia de comando.

    ![example](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/autosuggest/suggestion.jpg?raw=true)

    Y para que nos autocomplete el comando sugerido presionaremos la tecla direccional derecha " > "

    ![autosuggest](https://github.com/MarcosSilvaG/my_launchx_blog/blob/master/static/autosuggest/suggestion_done.jpg?raw=true)

Estos pasos sólo instalarán el autocompletado en el contexto del usuario actual, esto quiere decir que si estás como usuario normal deberás ponerte en modo super usuario (root) 
```bash
sudo su
```
E iniciar desde el paso uno para también tenerlo ahí.
Y si estás como super usuario (root) deberás salir de ese contexto tecleando
```bash
exit
```
Para volver como usuario normal y ejercutar desde el paso 1 nuevamente.

---


Si bien el tab es nuestro amigo incondicional para autocompletar comandos en la línea de comandos, una herramienta que nos permita ver un comando un tanto complejo y largo, nos permita escribirlo de manera tan rápida nunca viene tan mal. 

Este es solo un ejemplo de lo que zsh es capáz, podemos instalarle los plugins que querramos y que nos hagan el ambiente de desarrollo mas ágil.

Por mi parte es todo en este pequeño post, aún tengo un par más en mente que iré desarrollando de a poco. Un saludo a todos y hasta los próximos!!

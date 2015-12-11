---
layout: post
title: "Unificar con Vagrant"
date: 2015-12-11
backgrounds:
    - https://www.dropbox.com/s/mkhyvtgj1xz717e/captain_bridge_by_real_sonkes-d64exop.jpg?dl=1
thumb: https://www.dropbox.com/s/krnfe4v3lixrhee/mecanism_ii_by_butterflywings2151.jpg?dl=1
category: nodejs
tags: nodejs vagrant puppet linux windows mac vm
---

De los **problemas comunes** que me encuentro al trabajar con **Node.JS**, me resultan especialmente molestos los derivados de las diferentes **configuraciones de entorno de trabajo**.  
El que *no se pueda trabajar* porque la configuración del entorno del programador de problemas, me parece inaceptable. Es el tipo de escusa que me pone de muy mal humor. Esta en la misma lista que *"es que no suelo hacer backups"*, o el problema que hace poco ha tenido mi colega *Ghetto* trabajando con *PHP* y 1&1 *(¡cómo odio esta compañía! entre 1&1 y Logitech tengo para un futuro post-enrage)*: 
> Resulta que el colega no trabaja en offline...todo lo hace *sobre la marcha* en el servidor. Cuando ha salido este tema *(sin ir mas lejos el día que le enseñé a usar Vagrant)* siempre me ha dicho que **"él nunca ha tenido ningún problema trabajando así"**. Claro, **eso depende de la suerte que tenga cada uno**. Y al final, ~~como no podía ser de otra manera~~, la suerte se acabó.  
Cuando peor, se perdió una conexión con el servidor, y **todo el css de la web de turno acabó corrupta**.  
Por suerte *Ghetto* está acostumbrado a sacarse las castañas del fuego, y rehízo el trabajo en tiempo récord. Por desgracia eso también significa que es probable que siga haciendo las cosas igual de mal; **Menos mal que para *mecenarte* van a usar git** *como si no existiese el mañana*. 

Como decía, estos temas *me matan*. **Y si encima me pasan a mi, ya el mosqueo es cósmico.** Porque son problemas que se pueden prever, y para los que hay que tener planes de contingencia. Esto no es como que tu ISP te corte el Internet en medio de un proyecto, o que justo la impresora decida *tener un infarto* el día antes de imprimir el trabajo de la universidad, que tienes que entregar mañana. Estas cosas son previsibles. Y además puedes servirte de la experiencia de otros programadores *(cuando las barbas de tu vecino veas cortar)*.

## De entornos de trabajo, sistemas poco operativos, y odio eterno al CMD de Windows
> A- "Hey, has probado la ultima versión de la app"  
B- "Sí, pero no me carga, y me da un error rarísimo"  
A- "¡Pero si a mi me funcionaba perfectamente"

**No es aceptable que porque distintos programadores tengan distintas configuraciones de entorno, se pierdan horas, o días de trabajo.** Y punto.  
Y para que esto no suceda, o al menos no sea una *excusa recurrente*, **hay que tomar una decisión que unifique los entornos de trabajo entre los trabajadores de un mismo equipo**.  
Por ejemplo a *Nomo*, en su *trabajo de ensueño en empresa puntera*, le dieron un portátil nuevo nada mas entrar por la puerta. Con su linux, y su nota que avisaba: *"Usa lo que quieras"*; Traduzco: *"Si quieres usar tu mac, adelante, **pero no hay excusas si no funciona, que para eso te damos un portátil de empresa**"*. ¡Así da gusto! ¡Viva el dinero, copón!  
Pero, ¿que sucede si tu empresa, o tu economía, no te da para tomar una decisión salomónica *salamanca-hood style*? Bueno, pues **la respuesta que yo he encontrado es Vagrant**

No puedo obligar a mis compañeros a comprarse un mac *(aunque me gustaría)*, ni siquiera a usar Linux en sus máquinas. Windows, por mucho [Chocolatey](https://chocolatey.org/) y [CMDer](http://cmder.net/) que instales *(si usas Node con el CMD por defecto, o eres masoquista, o no lo entiendo)*, sigue siendo Windows. Pero bueno, no voy a entrar en detalles, que me conozco.  
**Lo que sí puedo hacer es obligarles a instalar una máquina virtual sencilla de usar, y probada por mi con antelación. Y ahí entra Vagrant**
> Lo mas gracioso del caso es que, *pese a todo*, *Oratual* acabó con el proceso cancelado mientras ruby seguía lanzándole lineas en segundo plano. **Ya puedes hacerlo fácil, testarlo mil veces, que si tu colega hace *ctrl+c* para pasarte lo que le dice la consola** por Skype...no puedes hacer nada. Es una batalla perdida. **Lo mejor que tiene Vagrant es lo fácil que es borrar la carpeta, y volver a empezar de 0.** La descarga de **la imagen "original" del SO se guarda aparte**, por lo que no tienes que esperar de nuevo a que se descargue. **Destruye las máquinas sin miedo.**

## Vagrant es sopa de sobre
Instalas Vagrant y VirtualBox   
```
Mac (instala primero Homebrew): 
     brew install Caskroom/cask/virtualbox Caskroom/cask/vagrant
Windows (instala primero Git y CMDer):
     choco install vagrant virtualbox
```

Clonas mi repositorio [Vagrant-Boxes](https://github.com/arkdelkaos/Vagrant-Boxes)   
```
git clone https://github.com/arkdelkaos/Vagrant-Boxes.git Vagrant-Boxes
```

Lanzas Vagrant  
```
vagrant up
```

**Y ya está**. Esperas, y cuando acabe haces  
```
vagrant ssh
```

En mi receta de *sopa de sobre* te instalo una Ubuntu14 de servidor, en una VM de 1core/512MB, y todo lo que se me ha ocurrido que puedas necesitar a nivel *--global*. Y si se me ocurriese alguna app extra, *git pull*, y, sinceramente, se tarda menos haciendo *vagrant destroy && vagrant up*
Así me seguro que todo mi equipo tiene una VM que he supervisado, fácil de destruir y aún mas fácil de crear. Una consola *unix* como *Dios manda*, y ejecutando los proyectos mediante una carpeta compartida con la VM, por lo que **para la edición ya cada cual que use *lo que mas rabia le de***.
> Os recomiendo que echéis un vistazo a [Visual Studio Code](https://code.visualstudio.com/): Es Simple, es bonito, y es cómodo. **Bastante mas rápido que Atom, mucho menos aparatoso que Sublime**.  
Ahora, al final del día todos los editores vienen siendo lo mismo. Se hace raro programar software libre en un iMac, con un editor de Microsoft. Vivimos [tiempos interesantes](https://www.wikiwand.com/es/Tiempos_interesantes)

## Ahora, ¿quieres tu propia receta?
Aquí ya la cosa se complica, como de costumbre. Hay mil una apps, librerías, configuraciones, clones, que hacen lo mismo *pero diferente*. Buscas un árbol y encuentras un bosque.  
Yo he acabado harto. Si no fuese por que *me da mas rabia la excusa de marras*, le hubiese dado una patada a Vagrant. 
Además todo esto está *como muy enfocado* a PHP, sobre todo si te dejas llevar por **el maravilloso trabajo de [scoth.io, y su 'box'](https://box.scotch.io/)**. Casi da hasta rabia ver como se lo montan en PHP hoy en día, sabiendo como era antes.  
Vagrant menos, pero **Puppet**, que es lo que una vez vagrant ha creado la VM procede con la instalación de los paquetes, **parece que le tenga asco a Node y MongoDB**. Problemas mil.  
Al final acabé instalando **[N, el gestor de versiones de Node](https://github.com/tj/n)** para manejar la instalación de node *propiamente dicho*, y mongo al estilo clásico. Y **funciona**, así que *una aspirina menos*.

Si vas a modificar la receta, empieza clonandola, no te cortes.  
Hay 2 archivos a tener en cuenta:
* **[Vagrantfile](https://github.com/arkdelkaos/Vagrant-Boxes/blob/master/Ubuntu14/Vagrantfile)**: A lo *Gruntfile*, es lo que mira vagrant cuando lo ejecutas en la carpeta donde está el archivo. Su configuración, simple como ella sola.  
No tiene mucho misterio, pero te voy a dar un par de consejos:  
  * En la parte de los puertos verás que el 22 del SSH lleva la coletilla *id: 'ssh'*. O le pones eso, o te creará un segundo binding al 22, en vez de redireccionar el 22. Digamos que **sobreescribe el comportamiento *default***.
  * La parte que dice *config.vm.provision "fix-no-tty"*...es una *ñapa* como una catedral. No tengo idea de que hace exactamente, pero **se come un error muy molesto que me impedía lanzar *vagrant ssh* tras puppet**. Si alguien quiere explicármelo, la verdad es que me llama la atención...pero no como para ir a buscarlo ahí fuera.
  * Los módulos de puppet son un aburrimiento importante, y una fuente de dolores de cabeza. Si ves que no consigues que funcionen como se supone que deberían, sáltatelos y hazlo a mano. Es una pena no poder hacer un simple *vagrant provision* para actualizar los paquetes, pero la idea de todo esto, IMHO, es dejar de perder tiempo de trabajo por *cacharrear* con el entorno de trabajo: tampoco tiene sentido perderlo *cacharreando* con Puppet si simplemente necesitas una manera de dotar de una VM sencilla a tu equipo. 
  > **Puppet** esta pensado para administrar software y configuración de muchas VMs a la vez, por ejemplo en un servidor. Para eso es importantísimo que los módulos, de 3os o propios, funcionen como un reloj. Para *cosas mundanas*, es demasiado *overkill*.
* **[default.pp](https://github.com/arkdelkaos/Vagrant-Boxes/blob/master/Ubuntu14/manifests/default.pp)** es la receta de Puppet. Es un caos, un descontrol total, y aunque existan los [stages](https://docs.puppetlabs.com/puppet/latest/reference/lang_run_stages.html), y te aviso que son incompatibles con la mitad de módulos que he probado. La única manera fiable de asegurar que se vaya instalando en cola, es mediante ***require***.  
  * Las clases hay que cargarlas con include, no te olvides. 
  * Los package se ejecutan directamente, en el momento en el que su *require* de valide.
  * Un *require* puede ser cualquier proceso, desde una *Class* a un *Exec*, y puedes concatenarlo (AND) mediante un array de este estilo:  
  ```
  require => [Exec["git_clone_n"], Exec["install_n"], Class["apt_update"]]
  ```

 
#### Imágenes:
* [bg by real-sonkes](http://real-sonkes.deviantart.com/art/Captain-bridge-370212361)  
* [thumb by butterflywings2151](http://butterflywings2151.deviantart.com/art/Mecanism-II-79549947)

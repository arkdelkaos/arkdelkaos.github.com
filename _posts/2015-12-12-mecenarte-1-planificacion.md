---
layout: post
title: "Mecenarte I: Planificación"
date: 2015-12-12
backgrounds:
    - https://www.dropbox.com/s/j0hhehr9p6vndgx/vg_concept___theatre___by_antifan_real.jpg?dl=1
thumb: https://www.dropbox.com/s/u2lwzmudkg85q9z/road_by_damnengine.jpg?dl=1
category: mecenarte
tags: mecenarte nodejs angularjs api raml babel es6 es2015
---

La planificación del proyecto *mecenarte* está siendo mas complicada que de costumbre, y que al no tener que tratar con un cliente *propiamente dicho*, ya que este proyecto lo estamos haciendo pra Oratual, nos quita la presión de cumplir unas fechas específicas. Esto puede parecer bueno en un primer momento, pero está mostrándose un problema a la hora de ponernos a trabajar.  

## Tratando con nuevos clientes

Generalmente sigo un flujo de trabajo a la hor de acometer proyectos nuevos, que me suele ir muy bien:
* **Antes** de la entrevista con el cliente
  1. Investigo al cliente, y sus posibles necesidades
  2. Intento llevar la mayor cantidad de **contenido ya preparado** (y mejor, en papel):
    * Variedad de **CMS** para las tareas mas comunes: Homepage, Blog, eCommerce, comunidades...
    * Diseños para dichos CMS, con **screenshots** en diferentes colores
    * ¡**Tablas de colores**! ¡Menuda mejora de la calidad de vida fue introducir conjuntos de colores en las entrevistas!.  
     5 colores: Fondo (bg), Header (menús), Primario, Secundario, y extra.  
     Si no lo habéis probado, no os imagináis lo que simplifica el proceso de selección del estilo de la web. **Los clientes raramente sabe que quieren**, y menos a nivel de paleta de colores. Raramente salen de los colores *"de empresa"*, y **no suelen conocer que gamas de colores combinan entre si**. Si no llevas este paso definido, **corres el peligro de que el cliente te cambie de opinión en medio del diseño** cuando ve que su elección ha convertido la web en una mezcla entre el payaso de Micolor y un laser center de los 90.  
     Prueba [Coolors](https://coolors.co) si buscas una app que te simplifique este paso.
    * Contratos predefinidos, a ser posible uno por tipo de servicio: Uno por cada CMS, por cada hosting, por servicios extra *(ej: rediseño de logos)*...y **sobre todo que queden claros los sobrecostes en caso de pedir cambios/mejoras una vez firmado el contrato.**  
*  Una vez frente al cliente, lo primero es ver qué necesita. **No es lo mismo *"lo que el cliente cree que necesita"*, que lo que realmente necesita**.  
Es de cajón, pero conozco casos en los que, ya sea por exceso de respeto o por falta del mismo, dejan que sea el cliente el que tome las decisiones, y punto. Y ellos a programar.  
Esto no funciona así: Por lógica **alguien que se dedica a este sector está mucho mas capacitado para recomendar un producto, y evitar una mala decisión al cliente**. El 90% de las veces te van a pedir "una web que haga X"; O peor, *"una web como 'esa' de ahí"*.  
Lo suyo es entender que necesidad tiene el cliente, traduciendo lo que te esté pidiendo, y acto seguido **ofrecer un producto (o varios) que cumpla no solo lo que quiere, sino también lo que necesita** (aunque ni sepa que lo necesita).
* Una vez que tengo claro qué voy a ofrecer, presento **diseños**. Mejor que te diga *"hazme uno **como este**, cambiando esto y aquello"*. Y ya de paso decidiendo una paleta de colores.  
* Por ultimo se acuerda un **presupuesto**, y **se firman los contratos**. Los contratos deben tener una serie de clausulas que te hace la vida *as fácil*:
  * Se marca una **fecha de entrega**, donde tendrá que firmar el recibo, que de paso sirve como prueba de que el cliente recibe lo que se acordó. Tras la entrega, no tiene derecho a reclamación. Y así te aseguras que no va a estar pidiendo retoques "de gratis": Si tras entrega quiere cambiar algo, ya es servicio extra, y se paga aparte.
  * Al firmar el contrato también acepta el diseño (completo, o con mockup) y los colores. Nada de cambiar de idea a medio diseño, sin pagar el tiempo invertido en el diseño "anterior".
  * Y por supuesto, pagos por adelantado, en entrega, y demás. A mi me gusta pedir un 15% por adelantado el día de la firma de los contratos, y el 85% restante en entrega (y si no hay pago, no hay web). Los precios no se vuelven a negociar una vez firmado el contrato.  
  > Si vas a tener algún tipo de consideración especial con un cliente, pregúntate primero si él lo tendría contigo si tú fueses el cliente. **Ten respeto por tu trabajo haciendo que el cliente te respete**. Profesionalidad.
  
Claro, para mecenarte no puedo seguir este sistema, ya que *no hay cliente*. Pero sí he podido prever las necesidades del proyecto mientras Oratual decidía que funciones necesita.

## Primario, Secundario y Terciario

No es ta sencillo decidir las funciones que va a llevar una nueva app. Y menos aún **plantear la lista de una manera útil**.  
Me encontré a *Oratual* pensado la lista como si fuese un maquetador, apuntando secciones de la web. Esto me sorprendió bastante, ya que **al tener un sistema muy definido, suelo dar por supuesto que todo el mundo se planifica de la misma manera, o semejante**. Como maquetador no puedes hacer una lista útil, ya que estas planteandolo en la capa final del frontend, casi como usuario...y vamos a hacer una api.  
Cuando le expliqué como planteo estas listas, tampoco me expliqué bien, ya que acabó creando la misma lista **ordenada por prioridad**.  

Las listas de funciones tienen que estar lo suficientemete **pormenorizadas** como para que el diseño de las colecciones de la base de datos sea lo mas sencillo posible. Vamos, que tienes que tener la db como horizonte mientras rellenas la lista.  

Antes de nada empieza añadiendo 3 bloques: 
* **Primario**: Son las funciones vitales. Las que tiene que llevar la app por obligación. Lo básico. Los cimientos. Por ejemplo el sistema de usuarios, seguridad, información de la empresa, etc. Lo que tiene que estar en la versión alfa.
* **Secundario**: Son las funciones que quieres que tenga por obligación antes de sacarla al público, en la beta. Por ejemplo aquí entra el sistema de bolsa de trabajo para actores, y el sistema de perfiles-cv. 
* **Terciario**: Son las funciones que no necesitas en la app, pero que estaría bien implementarlas en algún momento, si se tercia. Por ejemplo usar un generador de páginas estáticas para aligerar partes del frontend.  

Una vez tienes los 3 bloques, simplemente tienes que ir recorriendo las funciones pormenorizando el proceso. Os muestro un ejemplo, a medias, de la lista de nuestro proyecto hecha en 5 minutos:  
```
Secundario
  Sistema de castings
    Home
      Link nuevo usuario
        Alumno
        No Alumno
      Link nuevo casting
        Casting masivo >> tags >> validacion >> aviso usuarios
        Casting unitario >> buscador >> seleccion >> validacion >> aviso usuario 
```
Como ves, tampoco está bien hecho: Falta afinar mucho mas de cara a que sea sencillo crear las colecciones de la db...pero para el ejemplo se entiende de sobra :)
 
 
 
#### Imágenes:
* [bg by antifan-real](http://antifan-real.deviantart.com/art/VG-Concept-Theatre-132063505)  
* [thumb by damnengine](http://damnengine.deviantart.com/art/Road-58172753)

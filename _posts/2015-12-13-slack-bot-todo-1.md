---
layout: post
title: "Slack ToDo-Bot I: Draft"
date: 2015-12-12
backgrounds:
    - https://www.dropbox.com/s/nt3rw3iq99rk5g4/slack-back-1024x745.jpg?dl=1
thumb: https://www.dropbox.com/s/cyoonifj511a0j5/Slack_Mark_Web.png?dl=1
category: slack
tags: slack bot api nodejs to-do
---

Esto es una idea loca, más que otra cosa, pero creo que podría ser interesante como *proyecto de fin de semana* :)  
Lo que mas me gusta de **Slack** es el hecho de **tener todo el equipo conectado en una misma app**, de manera sencilla. Sin embargo se queda corto como herramienta de gestión de equipos, de ahí que se utilicen conexiones con aplicaciones externas, como por ejemplo Astana o Trello. Pero esto va en contra de lo que me gusta de slack, obligando al equipo a registrarse en otros servicios externos y perdiendo el tiempo.  

Existe una **infraestructura para crear bots para slack**, que permite **comunicación bidireccional** dentro del propio chat de slack con herramientas externas.  
Permite dar instrucciones al bot *como si de una consola de comandos se tratase*, pudiendo enlazar a una api dichos comandos, por lo que se puede manejar una aplicación externa si salir de slack.

## Un bot que maneja una lista To-Do
El bot debería tener los siguientes comandos dentro de slack:
* **Administración de listas**
  * Crear una Nueva lista To-Do asociada al grupo y al canal.
     - bot list new
     - POST /list/*id_grupo*/*id_canal*/*id_usr*/
  * Borrar la lista asociada al canal (admin)
     - bot list del
     - DELETE /list/*id_grupo*/*id_canal*/*id_usr/
  * Borrar tareas hechas (admin)
     - bot list clean
     - DELETE /list/*id_grupo*/*id_canal*/*id_usr*/clean
* **Administración de tareas**
  * Nueva tarea
     - bot task new
     - POST /task/*id_grupo*/*id_canal*/*id_usr*/
  * Marcar como hecha
     - bot task *35* done
     - UPDATE /task/*id_grupo*/*id_canal*/*id_usr*/*id_task*/
  * Borrar tarea (admin)
     - bot task *35* del
     - DELETE /task/*id_grupo*/*id_canal*/*id_usr*/*id_task*/
  * Asignar tarea a usuario (own)
     - bot task *35* own
     - UPDATE /task/*id_grupo*/*id_canal*/*id_usr*/*id_task*:own
* **Comunicación**
  * Pintar lista
     - bot list
     - GET /list/*id_grupo*/*id_canal*/
  * Pintar lista asignada a usuario
     - bot list own
     - GET /list/*id_grupo*/*id_canal*/*id_usr*/
  * Pintar help (usr/admin)
     - bot help
     - GET /help/*id_grupo*/*id_canal*/*id_usr*/
  * Pintar URL frontend
     - bot url
     - GET /url/*id_grupo*/*id_canal*/*id_usr*/
* **Configuración** (admin)
  * Nombrar nuevo administrador (dueño)
     - bot admin add *nombre*
     - UPDATE /list/*id_grupo*/*id_canal*/*id_usr*:new:*id_new_usr*/
  * Dejar puesto admin (no admin = list del)
     - bot admin out
     - UPDATE /list/*id_grupo*/*id_canal*/*id_usr*:out
  * Auto pintar lista cada X horas
     - bot list cron *24* (default 24h)
     - UPDATE /list/*id_grupo*/*id_canal*/*id_usr*/cron:24
  * Auto limpiar lista (marcados como hecho) cada X horas
     - bot list clean cron *24* (default 7d)
     - UPDATE /list/*id_grupo*/*id_canal*/*id_usr*/clean:cron:24
     
La db sería algo de este estilo:
{% gist 6a811d0de7213e08388d %}  
 
#### Imágenes:
* [bg by eoldecisions](http://eoldecisions.designworkbench.com/2015/02/16/keeping-touch-slack/)  
* [thumb by slack](https://brandfolder.com/slack)

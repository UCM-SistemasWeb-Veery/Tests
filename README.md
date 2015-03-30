# REPOSITORIO DE PRUEBAS

Vamos a ir jugando con git y github para ponernos de acuerdo y acostumbrarnos al proceder típico.  
Intentaré describir cada procedimiento, dando el comando pertinente a cada paso. Quién trabaje con interfaz gráfica, que busque la opción en los menus.

  
## Lo primero es lo primero, definiciones

**Git:** Aplicación para mantener control de versiones, según el propio linus ( que creó git para mantener el código del kernel de linux ):

"git" can mean anything, depending on your mood.
 - random three-letter combination that is pronounceable, and not
   actually used by any common UNIX command.  The fact that it is a
   mispronunciation of "get" may or may not be relevant.
 - stupid. contemptible and despicable. simple. Take your pick from the
   dictionary of slang.
 - "global information tracker": you're in a good mood, and it actually
   works for you. Angels sing, and a light suddenly fills the room.
 - "goddamn idiotic truckload of sh*t": when it breaks.  
 
**Github:** Servidor para mantener proyectos de "git", es lo que nos permitirá discutir cambios, y tener un sitio en el que trabajar todos.
  
### Workaround en git ( local )
1. Como de momento vamos a trabajar sobre repositorios ya existentes, lo importante es como **clonar** un repo online, lo cual no tiene mucho misterio:
```bash
    git clone https://github.com/UCM-SistemasWeb-Veery/Tests.git
    cd Test
```
De esta manera se creará una carpeta "Test" con el proyecto, la cual se podrá renombrar localmente sin que afecte en absoluto.  
2. Una vez tengamos el proyecto local, vamos a añadir un cambio super importante, para ello, creamos un branch específico para el cambio, editamos lo que sea y hacemos un push.  
 * Creamos el branch "cabecera_index" y cambiamos a este
```bash
    git branch cabecera_index
    git checkout cabecera_index
```
 * Hacemos los cambios que sean (agregar ficheros, modificarlos...)
 * Añadimos los cambios para commitear.
```bash
    git add --all
```
 * Hacemos el commit de nuestros cambios.
```bash
    git commit
```
Una vez hayamos escribamos el comando, nos saldrá el editor de texto por defecto para crear el mensaje de commit (Procuremos que sea descriptivo, porque permanecerá para siempre en el proyecto).
  
  Ahora que hemos hecho un commit, si miramos el log `git log` veremos que aparece que la rama "cabecera_index" ya tiene un commit en su lista.
   * Ahora que ya tenemos nuestro cambios terminados, queremos subirlos al repositorio para que todos podamos verlos, para ello, haremos un **push** del branch "cabecera_index" al **"remote"** origin.
```bash
    git push -u origin cabecera_index
```
Y ya está, hemos editado cosas y están en el repo, asique todos sabemos que hay cambios en la rama "cabecera_index".

### Workaround en github ( web )
Ya tenemos cambios subidos en el repo y después de hacer más ediciones sobre "cabecera_index" a lo largo de una semana, decidimos que ya está terminado, asique vamos a mezclarlo con la rama master para que forme parte del proyecto principal.
Vamos a la web [Página principal del grupo](https://github.com/UCM-SistemasWeb-Veery/), hacemos click en el         repositorio **"Test"**, y nos aparecerá algo como esto:   
![repositorio](https://github.com/UCM-SistemasWeb-Veery/Tests/tree/master/img/Repositorio.png)  
 Entonces, podemos cambiar de branch, si pulsamos el menú desplegable aparecerán todos los branches que haya y se      marcará el que estemos visualizando actualmente.
Nos interesa hacer un **pull request**, asique al lío. Pulsamos el botón "Pull request"  
![pull request](https://github.com/UCM-SistemasWeb-Veery/Tests/tree/master/img/crear_pull_request.png "pull")  
y rellenamos los campos...  
![editar pull](https://github.com/UCM-SistemasWeb-Veery/Tests/tree/master/img/editar_request.png "edit")  
![editar pull](https://github.com/UCM-SistemasWeb-Veery/Tests/tree/master/img/editar_request_2.png "edit")  
Ahora es el momento de la verdad, a todos se nos notificará el request y podremos comentar que nos parece y votar para hacer el merge.  
Una vez aprobado por todos, o por mi mismo en este caso, hacemos un merge (si no hay conflictos de código)  
![merge pull request](https://github.com/UCM-SistemasWeb-Veery/Tests/tree/master/img/merge_request.png "merge")  
Y ya está, ya podemos borrar el branch, que no sirve para nada  
![borrar branch viejo](https://github.com/UCM-SistemasWeb-Veery/Tests/tree/master/img/merge_terminado.png "delete")  

Esto está muy bien, pero ahora los demás querrán tener su versión local actualizada, o estó será una locura, pero como está todo pensado, no hay problema, la palabra clave es **"fetch"**, o para hacerlo todo de golpe ,**"pull"**.
```bash
    git pull origin
```

ya está, se habrán actualizado los commits nuevos en master y se habrá borrado la rama "cabecera_index" en caso de que la tuvieras en local. 
  
    
## Más o menos estamos
Si todo va bien, esta será la manera típica de proceder, parece un lío de cojones, pero es muy sencillo una vez entiendes de que va.  
A medida que surjan, tendremos que aprender a lidiar con los problemas, por ejemplo, cuando queramos borrar un commit, o haya conflictos al hacer merge. Aún no me he encontrado con muchos casos de ese tipo, así que no hay tutorial... lo vamos viendo.


## Ultimas aclaraciones
##### Crear un nuevo proyecto
>Cuando sea necesario, hacemos un repaso a la manera de crear repos y proyectos de git nuevos.
##### Master branch
El branch Master se crea por defecto cuando haces el primer commit en un proyecto vacío.
##### Origin
Algunos comandos (los que trabajan con el servidor) usan el término "origin", este es el **remote** por defecto cuando clonas un proyecto, y apunta a la dirección web desde donde has clonado, se pueden crear más remotes, editar, borrar..., para más info `git help remote`
##### Fork
Vale, forking... podemos trabajar de momento en el repo de la organización, para no hacer más pasos intermedios en el workaround, asique podemos olvidarnos de todo este tema.


## Más información, si MÁS información
Esto no pretende ser más que una guía rápida de las 4 cosas básicas, quién esté interesado, supongo y espero que todo el mundo, puede echarle un vistazo a este
[enlace](http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control).  
Ahí están los tutoriales oficiales con muuuuucha más información sobre como hacer de todo ordenado por capítulos. Además se puede consultar la documentación del comando git `git help <opcion>` donde <opción> es cualqueir subcomando de git, como branch, remote, pull, push,...  
Existen miles de tutoriales para empezar y para hacer cosas más avanzadas, os dejo alguno más:  
[Tutorial de la gente de github](https://guides.github.com/activities/hello-world/)

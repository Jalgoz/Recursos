# COMANDOS GIT

**git init** 
> Iniciamos el git en la carpeta que estemos.

## Git Add

**git add .** 
> Para añadir los archivos al escenario(Stage), utilizar cuando quieres agregar archivos dentro de carpetas.

**git add -A** 
> Agregamos todos los archivos modificados o nuevos.

**git add -u** 
> Para actualizar si el archivo fue eliminado y asi poder realizar el commit.

**git add --all** 
> Agregamos todos los archivos al escenario(Stage).

**git reset**
> Para eliminar un git add

**git add pdfs/*.pdf** 
> Agregamos todos los PDFs dentro de la carpeta pdfs.

**git add pdfs/** 
> Agregamos todos los archivos que estén dentro de pdfs/

**git add "*.txt"** 
> Agregamos todos los txt de todo el proyecto.

**git add** ***.txt** 
> Agregamos todos los txt del directorio actual.

## Git Status

**git status** 
> Para ver que todo este bien.

**git status -s** 
> Muestra el status resumido.

## Git Log

**git log** 
> Muestra todos los commits.

**git log --oneline** 
> Muestra los commits resumidos.

**git log --oneline --decorate --all --graph** 
> Nos muestra el log con mas info. 

## Git Commit

**git commit -m "nombreCualquiera"** 
> Para guardar o tomar captura de los archivos en escenario(Stage).

**git commit -am "mensaje"** 
> Para añadir al stage y hacerle un commit, pero el git ya debe estar haciendo seguimiento a este archivo.

**git commit --amend -m "NuevoMensaje"** 
> Para corregir el mensaje del ultimo commit.

**git commit --amend** 
> Nos abre el editor para cambiar el mensaje del ultimo commit.

## Git checkout

**git checkout -- .** 
> Para volver al estado del ultimo commit que hicimos.

**git checkout -- nombreArchivo** 
> Para volver a su estado anterior especificando el archivo(Solo ese archivo vuelve a su estado anterior).

## Git Reset

**git reset NombreArchivo** 
> Lo sacamos del escenario(Stage).

**git reset --soft HEAD^** 
> Para eliminar el ultimo commit pero no perder los cambios. 

**git reset --soft hashCode** 
> Nos lleva hasta el punto en el tiempo de ese hashCode pero no elimina los cambios que estén por encima del hashCode.

**git reset --mixed hashCode** 
> Nos lleva al punto del hashCode y nos muestra los cambios que hay entre el ultimo punto al punto del hashCode pero no elimina los cambios que estén por encima del hashCode..

**git reset --hard hashCode** 
> Nos lleva al punto del hashCode y borra todos los cambios que estuvieran por encima de este punto.

## Git Diff

**git diff** 
> Muestra los cambios que se hizo en el documento.

**git diff --staged** 
> Igual muestra los cambios pero que estén en el stage.

**git diff Rama1 Rama2** 
> Para ver los cambios que hay de una rama a otra.

**git diff hashCode hashCode** 
> Para ver los cambios que hay de un punto a otro.

## Git Reflog

**git reflog** 
> Muestra todo el historial de cambios y acciones realizadas desde que creamos el repositorio.

## Editar o Eliminar archivos

**git mv nombreActual nombreNuevo** 
> Para renombrar archivos en git(Recomendado) luego se tiene que hacer el commit de esto.

**git add -u** + luego + **git add -A** 
> Cuando cambiamos el nombre de un archivo sin utilizar git se tiene que seguir esos pasos luego un commit y ya(No recomendado).

**git rm nombreArchivo** 
> Para eliminar un nombre en git(Recomendado) luego se tiene que hacer el commit de esto.

**git rm --cached nombreArchivo** 
> Para eliminar un archivo que ya se encuentra en el repositorio, pero no lo eliminara de los archivos locales

## Git Branch

**git branch nombreRama** 
> Para crear una rama.

**git checkout nombreRama** 
> Para cambiar de rama.

**git chekout -b nombreRama** 
> Para crear la rama y cambiarnos a ella automáticamente.

**git branch -d nombreRama** 
> Para eliminar una rama(Recomendable borrar una rama después de hacerle merge al master).

## Renombrar branch y eliminar rama en el repo
Para renombrar una rama localmente y eliminarla en el repositorio seguir los siguientes pasos:
**git check -m new-name**
> Si estas en la rama que deseas eliminar 

**git branch -m old-name new-name**
> Si quieres renombrar una rama que no sea en la que estas actualmente

**git push origin --delete branch-name**
> Con esto eliminas la rama en el repositorio 

**git push origin branch-name**
> Vuelves a subir la rama renombrada

## Git Merge

**git merge nombreRama** 
> Para unir la rama secundaria a master, tener en cuenta que ya tienes que estar apuntando a la rama master.

## Git Tag

**git tag nombreTag** 
> Para crear un tag.

**git tag -d nombreTag** 
> Para eliminar un tag

**git tag** 
> Para ver los tags creados

**git tag -a v1.0.0 -m "Version 1.0.0"** 
> Recomendado versionar asi.

**git tag -a v0.1.0 hashCode -m "Version alfa"** 
> Para poner un tag en cualquier commit.

**git show nombreTag** 
> Nos muestra la info de esa tag.

**git push --tags**
> para subir tags al GitHub

### Para los tags se usa de la siguiente manera v1.2.2 CambioMayor.CambioMenor.Parche

## Git Stash

**git stash** 
> Nos vuelve al ultimo commit pero nos guarda todos los cambio que hayamos hecho.

**git show stash** 
> Nos muestra la información del stash.

**git stash save "Mensaje"** 
> Guarda el stash con un mensaje

**git stash pop** 
> Recuperamos los cambios que hicimos antes del stash y borramos el primer stash.

**git stash drop** 
> Para borrar el stash. 

**git stash clear** 
> Borra todos los stash

**git stash drop stash@{0}** 
> Borramos el stash elegido.

**git stash apply** es lo mismo que **git stash apply stash@{0}** 
> Se aplica el primer stash.

**git stash save --include-untracked** 
> Incluye todos los archivos incluyendo a los que no les hace seguimiento.

## Para configurar alias 

**git config --global alias.lg** "log --oneline --decorate --all --graph"

**git lg** ---> **git log --oneline --decorate --all --graph**

**git config --global alias.s "status -s -b"**

**git s** ----> **git status -s -b**

## Para ver la configuración actual del git

**git  config --global -e** 
> Muestra la config del git

**git  config --global -l** 
> Muestra la config del git en modo solo lectura

## Rebase

### Se usa para unir dos ramas pero poner la rama secundaria por delante de la principal

### Se puede decir que actualizamos las ramas con los cambios

### Primero hacemos un rebase en la rama secundaria y agregamos master para indicar que ahi se hará el rebase

**git rebase master** 
> Una las ramas pero el master se queda atrás.

**git checkout master** 
> Para cambiar a la rama principal.

**git merger nombreRama** 
> Para terminar el proceso.

## Para unir 2 commits

### Utilizamos rebase interactivo y le pasamos HEAD~NumeroCommits y con este head agarramos los commits que queramos

**git rebase -i HEAD~4** 
> Se pone el numero de los commits que se agarraran

### Luego nos saldrá el editor y ponemos squash o s en vez de pick al commit que queremos unir solo a uno, guardamos los cambios y cerramos la pestaña

### Para cambiar el mensaje de cualquier commit igual hacemos el anterior paso pero ponemos r en vez de pick

### No editar mensajes donde esta el pick 

## Para revertir un Commit y separarlo si es necesario

**git rebase -i HEAD~2** 
> Se pone el numero del commit que se quiere revertir 

### Se abrirá el editor y hay que poner edit o e en lugar de pick

### Luego guardamos los cambios y cerramos la pestaña y ponemos el siguiente comando

**git reset HEAD^**

### Con eso nos revertirá el ultimo commit sin perder los cambios que teníamos

### Una vez realizamos las modificaciones necesarias debemos poner el siguiente comando si o siguiente

**git rebase --continue**

# COMANDOS GITHUB

## Para subir un repositorio local a GitHub

### Se usa el comando de abajo mas el link del repositorio 

**git remote add origin linkRepositorio**

### Luego 

**git push -u origin main**

### Para bajar los cambios del repositorio subido a github y tenerlos en nuestro proyecto se hace un:

**git pull**

### Para subir los cambios:

**git push**

### Para clonar un repositorio

**git clone linkCLone NombreArchivo** 
> El nombre es opcional en caso de no poner se bajara con el nombre que esta en el repositorio.

### Para Eliminar un git remote
**git remote -v** y luego **git remote rm origin**
> Para ver los git remote que hay y elegimos el que queremos eliminar en este caso origin


### Git Fetch

**git fetch** 
> Se usa cuando hicimos cambios en el repositorio local y también se hizo cambio en el Github, también se usa git fetch cuando intentando subir con un git push nos sale un error de Rejected.

### Luego usamos:

**git pull** 
> Después del git fetch usamos el pull, puede que lo usemos mas de una vez.

**git push** 
> Por ultimo hacemos un git push. 

# Para trabajar con colaboradores

### Cualquier cambio o archivo nuevo hacerlo en una rama aparte para no dañar el master

**git push origin nombreRama** 
> Para subir la rama donde se hicieron los cambios, se crea automáticamente un pull request en GitHub

**git pull --all** 
> Por si no bajara todos los cambias a nuestro repositorio local.
 
**git branch -a**
> Para ver las ramas que no fueron creadas de forma local.

**git push origin nombreRama**
> Para subir los cambios que hicimos localmente a la rama deseada.
 
**git branch -D nombreRama**
> Para eliminar una rama que no quiera se borrada

**git push origin :nombreRama**
> Para borrar las ramas rojas que nos aparezcan con git branch -a.

**git remote prune origin**
> Para borrar las ramas que ya hayan sido borradas en el GitHub

## Issues 

### Se abren para arreglar algún problema que haya
### Recomendable cerrar la conversación si es un repositorios publico

**git commit -m "mensaje fixes #Nro"**
> Para poder cerra el issues desde la terminar se pone fixex/closes después del mensaje pero dentro de las comillas seguido del numeral del issues

### Prueba

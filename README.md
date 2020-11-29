# HOgit
Repositorio con ejercicios para practicar comandos básicos de git

## Qué podemos hacer

### Commits
Modificar un archivo y agregarlo al repositorio como un nuevo commit

### Branches
Creamos un branch acerca de las charlas, y decimos que nos parecen buenísimas


## Cómo creamos este repositorio

Inicialmente estaba creado en github (desde la WEB) con 
sólo un README. En cualquier lugar pueden (y deberían!)
correr `git status` y `git branch -a` para chequear
en qué estado está el repositorio y en qué branch están:


### Clonando el repositorio
Clonamos un repositorio de github con sólo un README

```
git clone https://github.com/wtpc/HOgit.git
cd HOgit
```


### Nuevo snapshot: modificando archivo y haciedo commit del cambio
Editamos el archivo de README y hacemos un nuevo commit

```
vi README.md
.........
git add README.md
git commit
```


### Creando y saltando entre ramas: Modificacion del archivo en cada rama
Ya hay un nuevo snapshot. Ahora creamos una branch

```
git branch charlas
```

y nos movemos a ella

```
git checkout charlas
```

en esta branch, editamos README.md de nuevo

```
vi README.md
...
git add README.md
git commit
```

ahora vamos a master (que no tiene estos cambios, porque es otra branch!)

```
git checkout master
```

y a partir de master creamos una nueva branch

```
git branch ejercicios
git checkout ejercicios
```

editamos un archivo nuevo, ejercicios.md

```
vi ejercicios.md
...
git add ejercicios.md
git commit
```


### Uniendo cambios entre ramas
Y ahora, en master, hacemos un merge de ambas branches por separado:
(fíjense que no importa que el orden sea el mismo que en el que 
las modificamos. es sensato porque las branches no se comunican)

```
git merge --no-ff ejercicios
git merge --no-ff charlas
```

la opción --no-ff sirve para que no "mezcle" las dos branches, y queda más prolijo el network. recomienod que la usen siempre, pero no es fundamental.


### Cheaqueando historia del repositorio
si quieren ver cómo quedó la historia del repo:

```
git log --oneline --graph
```


### Subiendo cambios al repositiorio online
finalmente, hacemos un push de todas las branches:

```
git push -u origin master
git push -u origin ejercicios
git push -u origin charlas
```

y listo! en nuestra cuenta de github ya tiene que estar subido. pueden ver el network de github que les va a mostrar la historia


### Edición y subida final del README.md con los comandos propios
Luego también editamos este readme para agregar los comandos con los que hicimos el repositorio


```
vi README.md
...
git add README.md
git commit
```

y el push

```

### Mi historial de comandos siguiendo este tutorial
cd tecnicasDeProgramacionCientifica/ 
git clone https://github.com/matiascarletti/HOgit
cd HOgit/
gedit README.md 
git add README.md 
git commit -m 'Se separaron las actividades del tutorial por distintas tareas marcadas por subtitulos de tercera jerarquía. Además se corrigió un error de tipeo encontrado'
git status
git branch -a
git checkout charlas
git branch -a
gedit README.md 
git add README.md 
git commit -m "Agregando mi opinion sobre las charlas del curso" 
git status
git branch -a
git checkout master 
git checkout ejercicios
git branch -a
git status 
gedit ejercicios.md 
git status 
git add ejercicios.md 
git commit -m "agregando mi opinion personal sobre los ejercios del curso"
git status
git checkout master 
git merge --no-ff ejercicios 
git merge --no-ff charlas # me tiraba un mensage de conflicto
git branch -a #me fijé en que brack estaba parado
gedit README.md # miré el README.md a ver cuales eran los conflictos y borré esas lineas que daban conflicto
git merge --no-ff charlas # Mergie denuevo y me seguía tirando conflicto por que no puse el agregué el README.md modificado al git y #tampoco hice el commit del mismo
git add README.md 
git commit -m "Arreglando conflictos con charlas para realizar el respectivo merge"
git merge --no-ff charlas # Si funcionó esta vez!! 
git log --oneline --graph 
git push -u origin master
git push -u origin ejercicios 
git push -u origin charlas 
git push
```


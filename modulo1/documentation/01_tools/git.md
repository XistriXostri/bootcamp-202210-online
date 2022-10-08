# Git / Github

## CMD

git muestra la información usando el comande less

:f -> scroll next page
:b -> scroll previous page
:q -> quit

<https://git.io/use-less>

## Configuración

Parámetros básicos en la configuración global de git

```shell
git config
git config --global user.name "Alejandro Cerezo"
git config --global user.email "alce65@hotmail.es"
git config --global core.editor "code --wait --new-window"
git config –-list [--show-origin]
```

<https://git.io/config-editor>

Es posible editar directamente la configuración global

git config --edit --global

### Otras configuraciones

```shell
git config --global core.autocrlf false
```

controlado desde el .editorconfig

```shell
git config --global core.ignorecase true
```

si estáis en Windows

```shell
git config --global init.defaultBranch main
```

desde git 2.28 (released 27th July 2020)
<https://github.blog/2020-07-27-highlights-from-git-2-28/#introducing-init-defaultbranch>

## Primeros pasos

- Crear repositorio
- Crear el fichero gitignore
- Añadir contenidos al repositorio
- Comprobar el resultado

### Crear repositorio

```shell
git status
git init
git status
```

### Crear el fichero gitignore

### Añadir contenidos al repositorio

Añadir elementos al index

```shell
echo 'Hello world' > hello.txt
git add hello.txt
git status
```

Crear commits

```shell
git commit -m "Add initial hello.txt"
git status

```

### Comprobar el resultado

```shell
git log
git log --graph --decorate --oneline
```

Alias

```shell
git config --global alias.lol "log --graph --decorate --oneline"
git lol
```

Ver el resultado internamente ("fontanería")

```shell
tree .git
tree .git/objects /f
```

Se puede ver que el resultado consta de 3 cartetas/archivos

- tree
- blob
- commit

Cada uno es accesible por los 5 primeros caracteres de su hash/5:
la carpeta (2 caracteres) + inicio del fichero (3 caracteres)

```shell
git cat-file -t <hash/5>
git cat-file -p <hash/5>
```

Igualmente se pueden ver los punteros

- HEAD
- Master Branch

```shell
type .git\HEAD
// ref: refs/heads/master
type .git\refs\heads\master
// 7765ebb10c75ff61694bee0057ed12823a964473
```

## Operaciones en la Staging Area (Index)

### Añadir ficheros

```shell
md samples
echo 'Sample One' > samples\sample1.txt
echo 'Sample Two' > samples\sample2.txt
tree samples /f
```

Se puede añadir al index

- un conjunto de ficheros
- todos los disponibles

```shell
git add <file>
git add .
git status
```

### Eliminar de la Staging Area (Index)

Si no estaba en gitignore, readme.md se habrá añadido a la Staging Area, pero puede ser eliminado de ella

```shell
git rm --cache <file>
git reset HEAD <file>
git restore --staged <file>
```

git restore es un nuevo comando que reproduce una parte de la funcionalidad de git checkout: recover an earier commit

### Eliminar ficheros

Puede hacerse en dos fases

- eliminar de la workArea (mediante el SO)
- subir el cambio a la Staging Area

```shell
del samples\sample1.txt
git status
git add samples\sample1.txt
git status
```

Es preferible hacerlo en un solo paso
Al ser un borrado definitivo, es necesario el modificador f

```shell
git status
git rm samples\sample2.txt
git status
git rm -f samples\sample2.txt
git status
```

### Cambiar nombre de ficheros

```shell
md samples
echo 'Sample One' > samples\sample_bad1.txt
echo 'Sample Two' > samples\sample_bad2.txt
tree samples /f
git add .
```

Igual que en el caso anterior, puede hacerse en un paso o en dos

En dos fases

- cambiar el nombre en la workArea (mediante el SO)
- subir el cambio a la Staging Area

```shell
ren samples\sample_bad1.txt sample1.txt
git status
git add samples\sample_bad1.txt
git add samples\sample1.txt
git status
```

En una sola fase

```shell
git mv samples\sample_bad2.txt samples\sample2.txt
git status
```

## git checkout / git reset

### git checkout

git checkout mueve el puntero de referencia HEAD a un commit específico. - en otra rama (lo habitual) - en la misma rama:
git checkout HEAD~1

You are in 'detached HEAD' state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may do so (now or later) by using -c with the switch command. Example: git switch -c <new-branch-name>

Or undo this operation with: git switch -

### git checkout a nivel de archivo

En lugar de mover el HEAD del repositorio, lo que hace es llevar al directorio de trabajo el fichero al que hemos hecho checkout con el contenido que tenía en el commit especificado

### git reset

git reset mueve el puntero de referencia de una rama (acompañado por el HEAD), a un commit específico, normalmente un comit anterior de la misma rama. Estaremos 'deshaciendo' los commits posteriores que quedarán huérfanos y se eliminarán la próxima vez que Git haga limpieza.

Sus efectos sobre la working y staging areas dependen de la opción seleccionada: - hard: el contenido del commit apuntado por la rama se refleja en la working y staging areas - mixed: (valor por defecto) el contenido del commit apuntado por la rama se refleja en la staging area - soft: no se modifican la working y staging areas

### git reset a nivel de archivo

git reset HEAD <file>

En este caso no mueve el HEAD del repositorio, lo que hace es llevar al directorio de staged el fichero al que hemos hecho reset con el contenido que tenía en el último commit. Como se una el parámetro por defecto, mixed , en el directorio de trabajo estará la versión última del contenido pendiente de commit y en staged la versión del contenido a la que hemos vuelto.

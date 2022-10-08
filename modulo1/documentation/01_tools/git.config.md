# Configuración

## Valores del fichero

user.name=Alejandro Cerezo
user.email=alce65@hotmail.es
core.editor=code --wait --new-window[optional]
core.autocrlf=false
core.ignorecase=true
init.defaultBranch=main

## Procedimiento

### Parámetros básicos en la configuración global de git

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

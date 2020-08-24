---
title: Trabajando con git.
description: Comandos necesarios que nos pueden salvar la vida.
img: https://images.unsplash.com/photo-1556075798-4825dfaaf498?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1055&q=80
alt: Git
author: 
  name: g0d13
---

### Borrar una rama remota
```git[git]
git push origin --delete test
```

### Agregar cambios al ultimo commit.
``` git[git]
git commit --amend
```
### Editar el ultimo commit, sin abrir el archivo.
```git[git]
git commit --amend -m "Your new commit message"
```
### Agregar cambios al ultimo commit, sin editar el ultimo mensaje
```git[git]
git commit --amend --no-edit
```

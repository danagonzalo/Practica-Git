**Práctica 1 - Dana Gonzalo**

**-Qué comando utilizaste en el paso 11? ¿Por qué?**
Utilicé `git reset --hard HEAD~1`, porque:

`git reset` mueve una rama donde queramos, y nosotros queremos ir al commit anterior, donde el archivo git-nuestro.md no estaba editado. Para ello añadimos `HEAD~1`, que es el commit anterior al que está HEAD. Pero con esto no basta, ya que `git reset HEAD~1` solo estamos haciendo cambios en el repositorio, pero no estamos restaurando el contenido del archivo git-nuestro.md. Para hacerlo, añadimos el comando `--hard`, que no solo hace cambios en el repo, sino también en el Working Copy.


**-Qué comando o comandos utilizaste en el paso 12? ¿Por qué?**
En el paso 12 hice lo siguiente:

- primero, utilizar `git reflog` para poder ver todos los commits por los que ha pasado HEAD. Como solo hemos hecho 2 commits, `git reflog` nos mostrará el que hemos deshecho, junto con un id único. Copiamos ese id y
- volvemos a usar el comando del paso 11 pero, esta vez, borramos el añadido `--hard`, ya que no queremos restaurar los cambios en el Working Copy. Además, en lugar de `HEAD~1`, pegamos el id del commit al que queremos ir.
- Por lo tanto, el segundo comando sería: `git reset <id_commit_borrado>`


**-El merge del paso 13, ¿causó algún conflicto? ¿Por qué?**
No causa ningún conflicts. Todos los cambios que hemos hecho en main, ya están incluidos en styled, por lo que no se produce ninguna pérdida. También podríamos decir que, la rama que queremos "absorber" es la rama padre de nuestra rama actual.

**-El merge del paso 19, ¿causó algún conflicto? ¿Por qué?**
Sí, esta vez sí que hay conflicto, ya que hemos cambiado el mismo archivo y las misma líneas en dos ramas diferentes que están en "bifurcaciones" diferentes. Es decir, si hacemos commit de un archivo, se perderían los cambios realizados en el otro.
Git nos indica que hay conflicto y nos deja solucionarlo a nosotros, pudiendo elegir con qué archivo nos queremos quedar.


**-El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?**
No, porque se ha hecho un merge fast-forward, ya que las ramas que queremos mergear están en forma de "lista", es decir, no se perdería ningún cambio.


**-¿Qué comando o comandos utilizaste en el paso 25?**
Utilicé el comando `git log --graph --branches --oneline`.
Lo que hace este comando es hacer el diagrama de nuestro log, con diferentes colores para cada rama, y muestra solo el mensaje del commit (sin el resto de la información).
Para no escribir este comando tan largo cada vez que quiera el diagrama de esta manera, podemos hacer `git config --global alias.<nombre_nuevo_comando> "log --graph --branches --oneline"`. Lo que hace esta orden es ponerle un alias al comando que queramos, en este caso, `<nombre_nuevo_comando>`.


**-El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?**
Sí, porque las ramas "title" y "main" están, como hemos dicho antes, en forma de "lista"; es decir, la rama title es hijo directo de main. Es decir, todo los cambios que hemos hecho en main ya están incluídos en title, por lo que no se peirde información.


**-¿Qué comando o comandos utilizaste en el paso 27?**
- `git reflog`
- Buscar el id del merge y copiar el id anterior a este
- `git reset <id_commit_anterior_al_merge>`
Esta vez no añadimos `--hard` porque no queremos perder los cambios en el Working Copy.

**-¿Qué comando o comandos utilizaste en el paso 28?**
`git restore git-nuestro.md`


**-¿Qué comando o comandos utilizaste en el paso 29?**
`git branch -D title`


**-¿Qué comando o comandos utilizaste en el paso 30?**
Los mismos que en el paso 27. Esta vez sí que añadimos `--hard` al segundo comando.
- `git reflog`
- `git reset --hard <id_commit_anterior_al_merge>`

**-¿Qué comando o comandos usaste en el paso 32?**
- `git reflog`
- `git reset --hard <id_primer_commit>`


**-¿Qué comando o comandos utilizaste en el punto 33?**
- `git reflog`
- `git reset --hard <id_commit_en_title>`

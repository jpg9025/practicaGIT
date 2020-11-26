1. ¿Qué comando utilizaste en el paso 11? ¿Por qué?
git reset --hard HEAD~1
El reset --hard HEAD~1 elimina los cambios en el staging working copy además de hacerlo en el staging area, devolviéndonos dos pasos atrás, cuándo git-nuestro.md no tenia formatos. A diferencia del git reset HEAD~1, que sólo elimina las modificaciones en el staging area. 

2. ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
Primero se obtiene el rastro de commit con:
git reflog
Este comando nos muestra el rastro, por dónde ha pasado el puntero HEAD. Una vez obtenido el hash del commit que queremos recuperar 
git reset <hash> 
git reset 185a757
Ahora, estamos en el commit indicado, pero la consola nos advierte que "hay cambios fuera del stage area tras el reset" esto son los estilos del texto. 
nano git-nuestro.md (comprobar los cambios)
git restore git-nuestro.md (para recuperar esos cambios fuera del staging area)
nano git-nuestro.md (comprobar la recuperación)

3. El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
No. Se trata de un merge fast-forward. Estando HEAD en styled (commit de subida del estilo a github) y master un commit por debajo (commit de subida de git-nuestro.md sin estilos). Todos los cambios de master son visibles desde styled

4. El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
Sí, styled tiene el git-nuestro.md con unos formatos de texto, y htmlify tiene el mismo archivo con otros formatos de texto. Los dos parten del commit A (paso 4), pero uno styled va al commit B (paso 10) y htmlify va al commit C (paso 18). Se han editado las mismas líneea del código desde dos ramas diferentes. Merge sin fast-forward.


5. El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
No, se trata de un commit con fast-forward. Los commit en los que se encuentra cada rama (master en commit A - paso 4, y styled en commit D - paso 21) están en la misma línea del grafo

6. ¿Qué comando o comandos utilizaste en el paso 25?
git config --global alias.graph "log --graph --pretty=oneline"
Para configurar de forma global, el comando graph para obtener el grafo
git graph

7. El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
Sí, aunque podemos forzar a que el merge sea non-fast-forward tal y como pide el enunciado (mediante git merge --no-f title). Dado que el commit en el que se encuentra title -incluir el título y subirlo a staging area- y el commit en el que se encuentra master -incluir los estilos mediante styled- están alineados en el grafo.

8. ¿Qué comando o comandos utilizaste en el paso 27?
git reset HEAD~1

9. ¿Qué comando o comandos utilizaste en el paso 28?
nano git-nuestro.md (Comprobar el estado del archivo)
git restore git-nuestro.md (se recupera el archivo del working copy, perdiéndose los cambios, título del poema, que se han quedado en el commit E (paso 26 - merge no ff desde title a master)

10. ¿Qué comando o comandos utilizaste en el paso 29?
git branch (para saber dónde estamos, no podemos borrar title estando en ella)
git branch -D title (para borrar la rama)

11. ¿Qué comando o comandos utilizaste en el paso 30?
git reflog (para localizar el hash del commit que quedó fuera de ramas)
git reset <hash> (para llegar al commit E, aislado sin rama que le apunte)
nano git-nuestro.md (para seleccionar con qué versión nos quedamos, no tiene título. Lo añadimos, descartamos este cambio en el paso 28)
git add git-nuestro.md
git commit git-nuestro.md

12. ¿Qué comando o comandos utilizaste en el paso 32?
git reflog (para ubicar el hash del primer commit, cuándo se creó)
git reset <hash> (para llegar al primer commit A)

13. ¿Qué comando o comandos utilizaste en el paso 32?
git graph (para ubicar el hash del commit dónde pusimos título)
git reset <hash> (para llegar al commit E)

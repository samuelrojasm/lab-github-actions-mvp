# 🧪 Guia para trabajar con el flujo de trabajo de Trunk-based Development

## Comandos de Git: Para trabajar con el flujo de trabajo de Trunk-based Development
### ⚙️ 1. Clonar el repositorio
Para empezar a trabajar, clona el repositorio principal (el trunk o rama `main`) en tu máquina local.
    ```bash
    git clone <URL_del_repositorio>
    cd <nombre_del_repositorio>
    ```
### ⚙️ 2.Mantener tu rama local actualizada
Antes de empezar a trabajar en una nueva funcionalidad o corrección, es crucial que tu rama local `main` esté sincronizada con el repositorio remoto. Esto ayuda a evitar conflictos.
    ```bash
    git clone <URL_del_repositorio>
    cd <nombre_del_repositorio>
    ```
### ⚙️ 3. Crear una rama de corta duración
En el enfoque de Trunk-based, se crean ramas para funcionalidades o correcciones de bugs, pero estas ramas son de corta duración (duración de horas o un día como máximo). El objetivo es que se fusionen con la rama principal lo antes posible. 🚀
    ```bash
    git checkout -b <nombre_de_tu_rama>
    ```
### ⚙️ 4. Trabajar, hacer "commits" y subir cambios
Trabaja en tu funcionalidad, haz commits de forma frecuente y sube tus cambios a la rama remota.
    ```bash
    # Después de hacer tus cambios...
    git add .
    git commit -m "Descripción clara de tu cambio"
    git push origin <nombre_de_tu_rama>
    ```
### 5. Fusionar la rama con el tronco principal
Una vez que tu trabajo esté completo y revisado (usualmente a través de una **"pull request"** o **"merge request"**), se fusiona con la rama `main`.
    ```bash
    # Primero, asegúrate de estar en la rama 'main'
    git checkout main

    # Luego, fusiona tu rama de funcionalidad
    git merge --no-ff <nombre_de_tu_rama>
    
    # O, si prefieres una fusión "squash" para un solo commit
    git merge --squash <nombre_de_tu_rama>
    git commit -m "Descripción de la funcionalidad completa"

    # Sube el cambio fusionado al repositorio remoto
    git push origin main
    ```
> La fusión --no-ff (no fast-forward) es a menudo preferida porque crea un commit de fusión explícito, lo que ayuda a mantener un historial claro de los cambios.<br>
> El comando `git merge --no-ff` sí crea automáticamente un commit de fusión, por lo que no es necesario ejecutar `git commit` después.
### 6. Eliminar la rama de corta duración
Una vez que la funcionalidad ha sido fusionada y el código está en el tronco principal, la rama de corta duración ya no es necesaria y se puede eliminar.
    ```bash
    # Eliminar la rama local
    git branch -d <nombre_de_tu_rama>

    # Eliminar la rama remota
    git push origin --delete <nombre_de_tu_rama>
    ```

---

## ¿Cómo funciona git merge --no-ff?
- Cuando Git realiza un **"fast-forward merge"** (fusión de avance rápido), simplemente mueve el puntero de la rama `main` a la última confirmación de la rama de la característica, sin crear un nuevo commit. Esto ocurre solo si la rama `main` no ha tenido nuevos commits desde que se creó la rama de la característica.
- Sin embargo, al usar el comando **git merge --no-ff**, estás forzando a Git a crear un commit de fusión  de forma explícita, incluso si pudiera realizar un "fast-forward". Este commit de fusión es importante porque:
    - **Preserva el historial:** Mantiene un registro de que una rama de característica se fusionó con la rama principal. Esto es útil para auditar el historial de cambios y entender de dónde provienen las funcionalidades.
    - **Permite deshacer:** Si necesitas revertir un cambio grande de una característica, puedes revertir un solo commit (el commit de fusión), en lugar de tener que deshacer varios commits de forma individual.

## Diferencia con git merge --squash
- La opción `--squash` tiene un comportamiento diferente.
    - `git merge --squash`: Combina todos los commits de la rama de la característica en un solo commit. Después de ejecutar este comando, Git deja los cambios listos en tu área de preparación, pero no los confirma. Por lo tanto, sí necesitas ejecutar un `git commit` manualmente después para finalizar la fusión.
    - En resumen:
    |           |               |
    |:----------|:--------------|
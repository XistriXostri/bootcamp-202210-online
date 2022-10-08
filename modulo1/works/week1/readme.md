# Week 1. Git & GitHub

En este ejercicio vas a crear un nuevo proyecto que albergará uno de tus ejercicios de HTML del precurso (elige el que quieras, a poder ser alguno que tenga más de un archivo).

-   Crea una nueva carpeta en tu disco duro para el nuevo proyecto, y abre esta carpeta en el VSCode.

    -   Inicializa un **proyecto con npm**
    -   Inicializa un **repositorio Git**
    -   En el package.json creado por npm, modifica la configuración de **prettier**
    -   Junto a él, añade los **archivos iniciales** necesarios:
        .editorconfig, .gitignore y un readme.md inicial.
    -   Crea un **commit** con estos archivos (`Initial commit`) en la rama main.
        Recuerda que deberá ser tu único commit en esta rama

-   Crea un repositorio en tu cuenta de **GitHub**.
    El repo debe llamarse _202210-W1-tuNombre-tuApellido_ (p.e., 202210-W1-jose-gonzalez).
-   **Vincula** tu repositorio local con tu repositorio remoto de GitHub tal como te indican allí.
    De esta forma subes la rama master al repositorio remoto.
-   Intenta **proteger** en GitHub la rama principal para que no se pueda volcar nada en ella sin hacer una **Pull Request** (PR).

-   Crea un nuevo site en **Netlify** y vincúlalo con el repo que has creado en GitHub para que se despliegue (deploy) automáticamente. Éste será tu entorno de producción.

-   Instala **husky** con el método automático de instalación para disponer fácilmente de **hooks en Git**.
-   Añade los dos hooks adjuntos commit-msg y pre-push.

    -   commit-msg establece la longitud válida de los mensajes de commit entre 10 and 72 caracteres
    -   pre-push requiere que el nombre de las ramas comience por hotfix, bugfix o feature

-   En tu repo local, crea una rama auxiliar llamada feature/exercise-files y vete a ella Comprueba que husky te impide utilizar un nombre de rama inadecuado.
-   Añade los archivos de uno de los **ejercicios del pre-curso**, a ser posible de los que incluyen HTML.
-   Crea un commit o varios con todos los archivos. Si quieres puedes también modificar en algo los ejercicios que tenías y hacer commit con los cambios. Comprueba que husky te impide emplear un mensaje de commit de longitud inadecuada

-   Mediante una PR, mergea el trabajo de la rama auxiliar en la rama principal y borra la auxiliar.
-   Sube los cambios de master al repo y comprueba que se han desplegado los cambios a producción. Comprueba también si la web se ve bien en ese entorno.

## Opción

-   Puedes repetir el proceso para otros ejercicios del pre-curso.
-   Crea para cara ejercicio una carpeta y añádelos al proyecto mediante su propia rama
-   Añade en la raíz del proyecto un index.html que de acceso a cada uno de los ejercicios añadidos.

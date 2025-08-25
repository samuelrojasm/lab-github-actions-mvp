# 🧪 Guía de Git Commit Convencional

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196?logo=conventionalcommits&logoColor=white)](https://conventionalcommits.org)

## ⚙️ Recomendaciones para el mensaje de un git commit
- Un buen mensaje de git commit es claro, conciso y descriptivo. No solo sirve para entender el cambio que se realizó, sino que también facilita la revisión del código, la depuración y la generación de un historial de cambios legible. Aquí hay algunas recomendaciones clave:
    - **Línea de asunto concisa (máximo 50 caracteres)**: La primera línea debe ser un resumen breve y directo del cambio. No debe ser una frase completa, sino más bien un imperativo: "Corrige bug de autenticación" o "Añade botón de 'me gusta'".
    - **Dejar una línea en blanco**: Después de la línea de asunto, deja una línea en blanco. Esto es crucial para que herramientas como `git log`, `git shortlog` y `git rebase` funcionen correctamente y presenten la información de forma legible.
    - **Cuerpo del mensaje detallado (después de la línea en blanco)**: El cuerpo del mensaje debe explicar por qué se hizo el cambio y qué problema resuelve. ¿Qué motivó este cambio? ¿Qué efectos secundarios puede tener? Es el lugar ideal para explicar el **"por qué"** del cambio, no solo el **"qué"**.
    - **Usar el imperativo**: Escribe el mensaje como si estuvieras dando una orden. En lugar de "Se corrigió un bug...", usa "Corrige un bug...". Esto mantiene la coherencia y la claridad.
    - **Referenciar tickets o issues**: Si el cambio está relacionado con un ticket en un sistema de seguimiento de errores (como Jira, Trello, etc.), incluye el número de referencia. Esto ayuda a vincular el código con la tarea correspondiente. Por ejemplo: `[JIRA-123]`.
    - **Limitar la longitud de las líneas**: Aunque no es una regla estricta, se recomienda que las líneas no superen los **72 caracteres**. Esto mejora la legibilidad en la terminal y en diversas herramientas.

---

## ⚙️ Patrones y estándares de facto
- Existe un patrón de facto que se ha popularizado y es seguido por muchas comunidades de código abierto, especialmente la de Linux, la cual es la misma comunidad que desarrolló Git. Este patrón se conoce como **"Conventional Commits"**.
- El estándar **Conventional Commits** es una especificación ligera sobre cómo escribir mensajes de `commit`. Su objetivo es crear un historial de `commit` explícito, lo que facilita la automatización de herramientas como la generación de `changelogs` y la determinación automática de la versión semántica de un proyecto.
- El formato básico es:
> `tipo(alcance): descripción`<br>`cuerpo del mensaje`<br>`pie de página`
- A continuación, los elementos clave de este patrón:
    - `tipo`: Es una palabra clave que indica el tipo de cambio. Los más comunes son:
        - `feat`: Un nuevo **feature** o funcionalidad.
        - `fix`: Una corrección de un **bug**.
        - `docs`: Cambios en la documentación.
        - `style`: Cambios que no afectan la lógica del código (formato, espacios, etc.).
        - `refactor`: Un cambio de código que no añade funcionalidades ni corrige errores.
        - `test`: Añadir o modificar tests.
        - `chore`: Cambios en la configuración de la construcción o tareas repetitivas.
    - `(alcance)`: Opcional. Indica la parte del código que se modificó. Por ejemplo, `feat(autenticación)`.
    - `descripción`: La descripción corta y concisa, siguiendo las mismas reglas de la línea de asunto.
    - `cuerpo`: (Opcional) Un cuerpo detallado que explica el cambio.
    - `BREAKING CHANGE`: Una nota especial en el pie de página para indicar un cambio que rompe la compatibilidad (API) y que requiere una nueva versión mayor según el versionado semántico.
- El uso de **Conventional Commits** no solo estandariza el historial de commit, sino que también permite el uso de herramientas automatizadas para:
    - **Generar automáticamente archivos** `CHANGELOG`: Un registro de cambios del proyecto.
    - **Determinar automáticamente la próxima versión del proyecto**: Si hay un `feat`, podría ser un `minor release`, si hay un `fix`, un `patch release`, y si hay un `BREAKING CHANGE`, un `major release`.
    - **Facilitar la búsqueda de cambios específicos**: Permite filtrar commits por tipo o alcance de manera sencilla.

---

## ⚙️ Ejemplos
- Ejemplos de mensajes de `git commit` siguiendo el patrón **Conventional Commits** y las mejores prácticas.
    - Ejemplo 1:
        > **feat(autenticación)**: Añade inicio de sesión con redes sociales<br><br>Añade la posibilidad de que los usuarios se registren e inicien sesión usando sus cuentas de Google y Facebook. Esto mejora la experiencia del usuario y expande las opciones de registro.
    - Ejemplo 2:
        > **fix(css)**: Corrige el espaciado de los botones en la barra de navegación<br><br>Se ajustaron los márgenes y el relleno para asegurar que los botones "Inicio" y "Perfil" en la barra de navegación tengan el mismo espaciado, mejorando la consistencia del 
        diseño.
    - Ejemplo 3:
        > **docs(README)**: Actualiza las instrucciones de instalación<br><br>Se revisaron y actualizaron los pasos para instalar las dependencias del proyecto, incluyendo los comandos correctos para npm.
    - Ejemplo 4:
        > **refactor(api)**: Renombra la función `getUsers` a `fetchUsers`<br><br>El nombre `getUsers` no reflejaba adecuadamente la naturaleza asíncrona de la operación. El nuevo nombre, `fetchUsers`, es más descriptivo y coherente con el estilo de nomenclatura del proyecto.
    - Ejemplo 5:
        > **chore(deps)**: Actualiza las dependencias de producción a la última versión<br><br>Se actualizó `react-router-dom` a la versión `6.1.1` y `axios` a la versión `0.27.2` para corregir vulnerabilidades de seguridad y aprovechar las nuevas funcionalidades.

---

## ⚙️ Paso a paso para un commit completo
- La sintaxis de `git commit -m` solo te permite escribir una línea de mensaje, lo cual es ideal para mensajes simples. Sin embargo, para incluir un cuerpo de mensaje y dejar la línea en blanco, se usa un método diferente.
- La forma correcta de hacerlo desde la línea de comandos es no usar la opción `-m`. Simplemente ejecuta `git commit` sin más parámetros.
    1. **Ejecutar el comando**: En la terminal, escribir:
        ```bash
        git commit
        ```
    2. **Se abre el editor de texto**: Git abrirá el editor de texto predeterminado (por ejemplo, Vim, Nano, VS Code, etc.). Se verá una pantalla similar a esta, con comentarios que empiezan con `#`:
        <p align="center">
            <img src="../../imagenes/vi-commit.png" alt="vi-commit" width="60%">
        </p>
    3. **Escribe el mensaje**:
        - En la primera línea, escribe el asunto del `commit` (por ejemplo, `feat: Añade un nuevo botón en la página principal`).
        - Luego, deja una línea en blanco.
        - En la siguiente línea, escribe el cuerpo del mensaje, explicando el porqué de tu cambio.
    4. **Guarda y sal del editor**: Una vez escrito el mensaje, guardar el archivo y ciérralo.
        - En vi, presionar `Esc`, luego escribir `:wq` y presiona `Enter`.
        - En Nano, presionr `Ctrl + O`, `Enter` y luego `Ctrl + X`.
> Al hacer esto, Git leerá el mensaje completo (incluyendo el salto de línea y el cuerpo) y lo guardará en el `commit`. De esta manera, el historial de Git se mantendrá claro, descriptivo y fácil de navegar para nosotros y el equipo.<br><br>Recordar que si en algún momento se desea volver a la forma corta para un `commit` rápido, siempre se puede usar `git commit -m "Mensaje simple"`.

---

## 🔗 Referencias
- [Conventional Commits](https://www.conventionalcommits.org)

---
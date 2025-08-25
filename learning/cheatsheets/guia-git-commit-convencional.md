# 🧪 Guía de Git Commit Convencional

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
`tipo(alcance): descripción`
`cuerpo del mensaje`
`pie de página`
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
> **feat(autenticación)**: Añade inicio de sesión con redes sociales
> Añade la posibilidad de que los usuarios se registren e inicien sesión usando sus cuentas de Google y Facebook. Esto mejora la experiencia del usuario y expande las opciones de registro.


---

## 🔗 Referencias
- [Git Merge vs Rebase vs Squash ¿Qué estrategia debemos elegir?](https://www.youtube.com/watch?v=HlmZLXMOpEM)

---
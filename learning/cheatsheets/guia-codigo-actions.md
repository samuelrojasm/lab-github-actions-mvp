# 🧪 Explicación del Código de la Acción

### Estructura del flujo de trabajo o workflow

|Condición de Ejecución               |Descripción                                                            |
|:------------------------------------|:----------------------------------------------------------------------|
| `name: Validar Nombres de Archivos` | Es el nombre visible de tu flujo de trabajo en GitHub.                |
| `on: push`                          | Esta acción se activará cada vez que se haga un `push` al repositorio.|
| `branches: main`                    | Solo se ejecutará para los `push` en la rama `main`                   |
| `jobs: validar`                     | Define un job o trabajo. Puedes tener múltiples jobs.                 |
| `runs-on: ubuntu-latest`            | La acción se ejecutará en una máquina virtual de Ubuntu.              |

### Sección Steps del job
`steps`: Define los pasos que el job seguirá.

|Steps                          |Descripción     |
|:------------------------------|:---------------|
| `actions/checkout@v4`|Un paso común que "saca" los archivos del repositorio para que la acción pueda trabajar con ellos. Es una acción pre-construida de GitHub.|                    
| `name: Validar nombres`|El nombre del paso que se mostrará en los logs.|
| `run: \|`|Indica que este paso ejecutará comandos de shell.|
| `find . -name "*secreto*"`|El comando busca recursivamente en el directorio actual (.) archivos que contengan la palabra "secreto" en su nombre.|
| `if [ -n "$ARCHIVOS_MALOS" ]`|Comprueba si la variable ARCHIVOS_MALOS tiene contenido (es decir, si se encontró algún archivo).|
| `exit 1`|Si se encuentra un archivo "malo", este comando hace que el trabajo falle. Si no se encuentra, el trabajo termina con éxito automáticamente.|

|Steps|Descripción|
|:----|:----------|
|find . -name "*secreto*"|El comando busca recursivamente en el directorio actual (.) archivos que contengan la palabra "secreto" en su nombre.|
|if [ -n "$AECHIVOS_MALOS" ]|El comando busca recursivamente en el directorio actual (.) archivos que contengan la palabra "secreto" en su nombre.|
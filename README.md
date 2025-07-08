# TEMPLATE-NICLABS-REPO
Este template ([versión ingles](./README_english.md)) proporciona la información básica requerida para proyectos de GitHub. Además, incluye tutoriales e información adicional que facilitarán un mejor uso de la plataforma de GitHub y algunos de sus servicios. 

## 1. Creación del archivo `.project_info`
Debe crear un archivo llamado `.project_info` en la carpeta raíz del proyecto con la siguiente estructura:
```
Título: <Título del proyecto>  
Objetivo: <El objetivo principal del proyecto>  
Descripción: <Breve descripción de lo que hace tu proyecto>  
Miembros actuales: <Miembro1, Miembro2, ...>  
Miembros históricos: <Miembro histórico1, Miembro histórico2, ...>
Palabras clave: <ver archivo keywords.txt>  
Colaboración: <colaborador1, colaborador2, ...>  
Fecha de inicio: <YYYY-MM-DD>  
Fecha de finalización: <YYYY-MM-DD> (estimada)  
Estado: <Iniciando, En progreso, Completado, Bloqueado, Abandonado>
```

## 2. Estructura básica del README.md
La estructura básica de su README.md se sugiere que sea la siguiente:
1. Breve despripción del repositorio (puede utilizar la misma que .project_info si coincide).
2. Pre-instalación: Detalle los requisitos previos necesarios antes de instalar el proyecto. Por ejemplo: "Debe tener instalado Python3 en su sistema".
3. Instalación: Instrucciones para preparar y ejecutar el código. Ejemplo: "Instalar las librerías del archivo `requirements.txt`".
4. Uso: Explique cómo ejecutar el proyecto. Se recomienda incluir ejemplos de cómo interactuar con el código y qué resultados/salidas se esperan.
5. Licencia: Su proyecto **DEBE** utilizar la licencia del [MIT](https://opensource.org/licenses/MIT).

Nota: **NO DEBE** subir información sensible al repositorio, como direcciones IP, contraseñas, nombres de bases de datos, o archivos grandes de datos, a menos que se le indique lo contrario. Para esto le puede ser útil identificar estos archivos y agregarlos a su `.gitignore`
## 3. Issues & Milestones

El proyecto **DEBE** utilizar Issues y Milestones para planificar, realizar un seguimiento y gestionar las tareas de manera efectiva, asegurando que el progreso pueda monitorearse y los objetivos se cumplan a tiempo.

#### 3.1 Issues
Los Issues se pueden usar para planificar, discutir o hacer un seguimiento del progreso del proyecto. También son útiles para seguir actividades específicas, como la corrección de errores, nuevas funcionalidades y nuevas ideas.
[En este link](https://docs.github.com/es/issues/tracking-your-work-with-issues/about-issues) puede encontrar mas información sobre issues. 

[Un breve tutorial](https://docs.github.com/es/issues/tracking-your-work-with-issues/configuring-issues/quickstart) proporcionado por GitHub explica cómo crear issues. Es importante, en este punto, etiquetar el issue (se pueden crear nuevas categorías) y asociarlo con un milestone. 

### 3.2 Milestones
Los Milestones se pueden usar para realizar un seguimiento del progreso de grupos de issues o pull requests en un repositorio. Permiten agrupar tareas relacionadas y visualizar el estado y progreso de una funcionalidad, tarea o del proyecto. Los milestones se pueden usar para establecer metas a corto o largo plazo, y cada milestone puede estar vinculado a uno o más issues o pull requests específicos. Al crear un milestone, es importante establecer una fecha estimada de finalización para ayudar en una mejor planificación del proyecto.
[Un breve tutorial](https://docs.github.com/es/issues/using-labels-and-milestones-to-track-work/creating-and-editing-milestones-for-issues-and-pull-requests) para la creación de milestones está disponible en GitHub.

Adicionalmente, este [material suplementario](./slides-COM4602/Clase_8_seguimiento_de_tareas.pdf) puede ser de utilidad.

## 4. Commits & Branches
### 4.1 Commits
Los commits son esenciales para guardar los cambios en un proyecto. Permiten hacer un seguimiento de las modificaciones, revertir a estados anteriores y colaborar de manera eficiente. Al realizar commits, es importante:

* Escribir mensajes de commit claros y concisos
* Hacer commits pequeños y enfocados (Atómicos)
* Hacer commits con frecuencia

Es importante mantener la atomicidad de los commits para poder realizar un mejor seguimiento del progreso del proyecto. [Aquí](https://kapeli.com/cheat_sheets/Conventional_Commits.docset/Contents/Resources/Documents/index) puedes encontrar ejemplos de commits convencionales que podrían ser útiles.

### 4.2 Branches

Las branches permiten un desarrollo paralelo, ayudando a aislar diferentes características o correcciones. Al trabajar con branch, siga estas mejores prácticas:

* **Use nombres descriptivos para las branch**: Los nombres de las branch deben reflejar el propósito o la característica, por ejemplo, `feature/login-page`, `bugfix/header-error`.
* **Cree una branch para funcionalidad o bugs**: Evita hacer commits directamente en la branch principal. En su lugar, crea una nueva branch para cada tarea/versión/bug.
* **Usa Pull Requests (PRs)**: Una vez que los cambios en una branch estén completos, cree un pull request para fusionarlos con la branch principal. Esto permite la revisión del código y pruebas antes de la integración. [Aquí](https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) encontrará información sobre la creación y uso de pull requests.
* **Mantener las branches actualizadas**: Realice regularmente el merge de la branch principal en tus branches de funcionaliades/bugs para minimizar los conflictos de merge.

Este material suplementario sobre ([branches](./slides-COM4602/Clase_5_Manejo_de_ramas.pdf),[commits](./slides-COM4602/Clase_6_Alteraci_n_de_commits.pdf), [issues, milestones & pull request](./slides-COM4602/Clase_8_seguimiento_de_tareas.pdf)) puede ser de utilidad.

## 5. Git Hooks para testing
Los Git hooks son scripts que se ejecutan automáticamente. Pueden ser útiles para automatizar tareas como ejecutar pruebas, realizar chequeos de linting o de formato antes de hacer commit o push de los cambios. En el contexto del testing, los hooks pueden ayudar a asegurar que el código siempre sea validado antes de ingresar al repositorio, ayudando a mantener la calidad del código.

Los **Git hooks** se almacenan en el directorio `./git/hooks/` de un repositorio, y cada hook corresponde a un evento diferente de Git (por ejemplo, pre-commit, pre-push, etc.). A continuación, se presentan ejemplos de **Git Hooks** utilizados para testing:

* **Pre-commit Hook**: Este hook se ejecuta antes de que se complete el commit. Si las pruebas fallan, el commit no se ejecutará, asegurando que solo se haga commit de código que pase los tests correctamente. Su uso puede incluir test unitarios, análisis estático de código, entre otros.

* **Post-commit Hook**: Este hook se ejecuta después de que se ha realizado un commit. Si ocurre un error en esta etapa, no detendrá el commit (ya que se ejecuta después del commit), pero puede activar notificaciones o registrar el problema para su revisión posterior. Este hook puede ser útil para tareas como actualizar la documentación, enviar notificaciones o registrar detalles sobre el commit.

* **Pre-push Hook**: Este hook se ejecuta antes de hacer push al repositorio remoto. Si hay un error, el push se detendrá, permitiendo detectar y corregir problemas antes de actualizar la branch remota. Este hook es útil para ejecutar test de integración o test end-to-end, asegurando que el código que se sube al repositorio no rompa la funcionalidad.

* **Post-push Hook**: Este hook se ejecuta después de hacer push a un repositorio remoto. No detiene el push en sí, pero puede ser útil para tareas como enviar notificaciones, registrar cambios o actualizar un dashboard. Si ocurren errores, no afectarán al push, pero pueden generar alertas para su revisión posterior.


Aquí se tienen ejemplos de los hooks de Git más comúnmente utilizados, como `pre-commit`, `post-commit` y `pre-push`, que pueden ayudar a automatizar varias tareas. Otros hooks, como `commit-msg` y `pre-merge`, también pueden ser útiles dependiendo de tus necesidades. Cada hook tiene un propósito único, lo que permite personalizar y controlar la calidad en diferentes puntos del flujo de trabajo. Para una lista completa de todos los hooks de Git disponibles, puedes consultar la [documentación](https://git-scm.com/docs/githooks) oficial de Git.


### Ejemplo de Git Hook: pre-commit 
Aquí se tiene un ejemplo de cómo crear un hook pre-commit para verificar que las funciones `binary_search` y `seq_search` del archivo `search_algorithm.py` pasen todos los test de archivo `test_search_algorithm.py` antes de hacer el commit. **Puede que algunos comandos solo los pueda ejecutar en Linux o MacOS**

0. Reemplace la función `binary_search` en el archivo `search_algorithm.py` con esta versión incorrecta.
```python
def binary_search(arr, target):
    return True # devolvera siempre True
```
1. En la carpeta raíz, cree el archivo Hook (si no existe ya). Ejemplo:
```bash
$ cd .git/hooks
$ touch pre-commit
```
2. Agregue los comandos de prueba al archivo Hook. Ejemplo:
```
#!/bin/bash
echo "Running tests before committing..."

# Run the tests
python -B testing.py

# Check for errors and halt commit if tests fail
if [ $? -ne 0 ]; then
    echo "Tests failed. Commit aborted."
    exit 1
fi

echo "Tests passed. Proceeding with commit."

```
Nota: Se puede usar cualquier lenguaje, siempre que especifiques el intérprete al comienzo del archivo (por ejemplo, `#!/bin/bash`, `#!/usr/bin/env python3`, etc.).

3. Haga que el archivo sea ejecutable. Ejemplo:
```bash
.git/hooks$ cd ../..
$ chmod +x .git/hooks/pre-commit
```
4. Por favor, intente hacer el commit de los cambios realizados en `binary_search`, y no debería poder completar el commit.
```bash
$ git add search_algorithm.py
$ git commit -m "bad commit"
```

## 6. Material Complementario
El material presente en la carpeta [slides-COM4602](./slides-COM4602/) entrega conocimientos básicos y avanzados del uso de la herramienta git. Este material corresponde a las slides del curso "Introducción a los Repositorios de Código Distribuido" dictado por el profesor Diego Madariaga en la universidad de O'higgins el año 2021. Agradecemos enormemente a nuestro antiguo compañero de laboratorio Diego por facilitarnos el material.
## Acknowledgments:
@dmadariaga

@MelanieNICLabs

@lucastorrealba

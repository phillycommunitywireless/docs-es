# PCW Documentation

Technical documentation and onboarding materials for Philly Community Wireless.

<!-- 
* [Team Onboarding](docs/onboarding.md)
* [Hardware Inventory](docs/hardware.md)
* [Mesh Kit Setup](docs/mesh-kit.md) 
-->

---

---
# Edición de los documentos

## Edición en GitHub

Después de recibir acceso al repositorio, se pueden realizar modificaciones en el código del sitio directamente desde el repositorio de GitHub, si aparece como colaborador del repo. Sólo tiene que encontrar el archivo que desea editar (el nombre del archivo será el mismo que el de la página -- editar-docs para esta página) y haga clic en el icono del lápiz en la esquina. Una vez que haya completado los cambios, desplácese hasta la parte inferior, agregue un mensaje de confirmación y haga clic en “Confirmar cambios”. Los documentos públicos se actualizarán para reflejar esto.

## Edición local

Para realizar ediciones en documentos localmente, deberás tener una cuenta de GitHub y aparecer como colaborador de la `phillycommunitywireless/docs` depósito. También necesitarás `git` y un editor de rebajas de su elección.

## Realizar modificaciones en los datos del sitio

### Clonar el repositorio

Lo primero es lo primero: si aún no lo ha hecho, copie el repositorio de documentos en su máquina local:

``` bash
git clone https://github.com/phillycommunitywireless/docs.git 
cd docs
```

Si ya tiene el repositorio clonado, debe extraer cualquier cambio nuevo para sincronizarlo con el repositorio remoto:

``` bash
git pull
```

### Editar archivos de markdown

Debería ver varios archivos de rebajas en el `docs/docs` subcarpeta. Estos corresponden a las páginas del sitio principal. ¡Puede abrir y editar estos archivos en un editor de rebajas de su elección!

### Finalización de los cambios

Una vez que esté seguro de los cambios que ha realizado en los documentos, puede enviarlos de vuelta al repositorio remoto. [ReadTheDocs](https://readthedocs.io) será notificado de estos cambios e inmediatamente reconstruirá el sitio público con sus cambios reflejados.

``` bash
git add .
git commit -m "Add a message specifying what you changed"
git push
```

Si esta es la primera vez que empuja, es posible que deba ejecutar esto en su lugar:

``` bash
git push --set-upstream origin main
```

### Adición de nuevos archivos

Si acabas de añadir un nuevo `.md` doc a la `docs` carpeta, no lo verá reflejado inmediatamente en el sitio en vivo. Para agregarlo, deberá agregarlo a la configuración de navegación del sitio, que se establece en el `mkdocs.yml` file at the root of the project.

``` yaml
# /mkdocs.yml

nav:
  - Unidad de malla AP: index.md
  - Mesh Kit Setup Guide: mesh-kit/mesh-kit.md
  - Hardware: hardware.md
  - Onboarding: onboarding.md
  - Editing these docs: edit-docs.md
```

Para agregar una nueva página, simplemente agregue un nuevo par clave-valor a esta lista:

``` yaml
  - Your New Page: new-page.md
```

## Ejecución de una versión local del sitio de documentos

Esto sólo es necesario si necesita ver cómo los documentos se representan específicamente en nuestro sitio en vivo. Cualquier editor de marcas debe ser capaz de previsualizar los documentos como aparecerán en el sitio, sin mucha desviación. Si usted desea hacer cambios de estilo / estructurales en el sitio y/o su tema, esta es también la manera de hacer eso.

Primero, [clone el repositorio.]()

### Ejecutar un servidor local con Docker

1. Descargue [Docker,]() que debería incluir Docker Compose en la mayoría de las máquinas.
2. Corre`docker-compose up` dentro del directorio del proyecto.
3. El servidor mkdocs se iniciará y se puede acceder a él en`localhost:8000`. Cualquier cambio realizado en los documentos actualizará automáticamente la página.

### Opcional: Configurar el entorno de Python

Si necesita que su entorno de desarrollo se integre con otros programas en su máquina, por ejemplo, para linear en un editor de texto, necesitará configurar un entorno virtual Python con las dependencias necesarias instaladas.

Primero, asegúrese de tener Python 3 y `pip` instalado y ejecute los siguientes comandos:

``` bash
# install the pipenv package
pip install pipenv
# create a virtual environment and install dependencies in it
pipenv install -r requirements.txt
```

Sus dependencias ahora están instaladas en un entorno virtual (generalmente ubicado en algún lugar de su carpeta $HOME/.local/). Para activar el entorno en la línea de comandos, escriba `pipenv shell`. Si está usando [Visual Studio Code](https://vscode.com/) para la edición, cambie la configuración del intérprete de Python para que apunte a la ruta devuelta por `pipenv which python`.

---
title: Utilizar la Paleta de Comandos de Visual Studio Code en los Codespaces
intro: 'Puedes utilizar la característica de paleta de comandos de {% data variables.product.prodname_vscode %} para acceder a muchos comandos en Codespaces.'
versions:
  fpt: '*'
  ghec: '*'
type: reference
topics:
  - Codespaces
  - Visual Studio Code
product: '{% data reusables.gated-features.codespaces %}'
shortTitle: Paleta de Comandos de VS Code
allowTitleToDifferFromFilename: true
redirect_from:
  - /codespaces/codespaces-reference/using-the-command-palette-in-codespaces
---

## Acerca de la Paleta de Comandos de {% data variables.product.prodname_vscode %}

La paleta de comandos es una de las características focales de {% data variables.product.prodname_vscode %} y está disponible para que la utilices en Codespaces. La {% data variables.product.prodname_vscode_command_palette %} te permite acceder a muchos comandos para {% data variables.product.prodname_codespaces %} y {% data variables.product.prodname_vscode %}. Para obtener más información sobre cómo utilizar la {% data variables.product.prodname_vscode_command_palette %}, consulta la sección "[Interfaz de usuario](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)" en la documentación de Visual Studio Code.

## Acceder a la {% data variables.product.prodname_vscode_command_palette %}

Puedes acceder a la {% data variables.product.prodname_vscode_command_palette %} de varias formas.

- <kbd>Shift</kbd>+<kbd>Command</kbd>+<kbd>P</kbd> (Mac) / <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux).

  Nota que este comando es un atajo de teclado reservado en Firefox.
- <kbd>F1</kbd>
- Desde el menú de la aplicación, haz clic en **Visualizar > la paleta de comandos...**.

  ![El menú de la aplicación](/assets/images/help/codespaces/codespaces-view-menu.png)

## Comandos para los {% data variables.product.prodname_github_codespaces %}

Para ver todos los comandos relacionados con {% data variables.product.prodname_github_codespaces %}, [accede a la {% data variables.product.prodname_vscode_command_palette %}](#accessing-the-command-palette) y luego comienza a teclear "Codespaces".

![Una lista de todos los comandos que se relacionan con los codespaces](/assets/images/help/codespaces/codespaces-command-palette.png)

### Suspender o detener un codespace

Si agregas un secreto nuevo o cambias el tipo de máquina, tendrás que detener y reiniciar el codespace para que aplique tus cambios.

Para suspender o detener el contenedor de tu codespace [accede a la {% data variables.product.prodname_vscode_command_palette %}](#accessing-the-command-palette) y luego comienza a teclear "stop". Selecciona **Codespaces: Detener el codespace actual**.

![Comando para detner un codespace](/assets/images/help/codespaces/codespaces-stop.png)

### Agregar un contenedor de dev desde una plantilla

Para agregar un contenedor dev a una plantilla, [accede a la {% data variables.product.prodname_vscode_command_palette %}](#accessing-the-command-palette) y luego comienza a teclear "dev container". Selecciona **Codespaces: Agregar archivos de configuración del contenedor de desarrollo...**

![Comando para agregar un contenedor de dev](/assets/images/help/codespaces/add-prebuilt-container-command.png)

### Reconstruir un codespace

Si agregas un contenedor de dev o si editas cualquiera de los archivos de configuración (`devcontainer.json` y `Dockerfile`), tendrás que reconstruir tu codespace para que este aplique tus cambios.

Para recompilar tu contenedor, [accede a la {% data variables.product.prodname_vscode_command_palette %}](#accessing-the-command-palette) y luego comienza a teclear "recompilar". Selecciona **Codespaces: Reconstruir contenedor**.

![Comando para reconstruir un codespace](/assets/images/help/codespaces/codespaces-rebuild.png)

### Bitácoras de los codespaces

Puedes utilizar la {% data variables.product.prodname_vscode_command_palette %} para acceder a las bitácoras de creación de codespaces o puedes utilizarla para exportar todas las bitácoras.

Para recuperar las bitácoras para Codespaces, [accede a la {% data variables.product.prodname_vscode_command_palette %}](#accessing-the-command-palette) y luego comienza a teclear "log". Selecciona **Codespaces: Exportar bitácoras** para exportar todas las bitácoras relacionadas con los codespaces o selecciona **Codespaces: Ver las bitácoras de creación** para ver las bitácoras relacionadas con la configuración.

![Comando para acceder a las bitácoras](/assets/images/help/codespaces/codespaces-logs.png)

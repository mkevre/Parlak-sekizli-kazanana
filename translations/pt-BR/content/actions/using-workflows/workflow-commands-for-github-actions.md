---
title: Comandos do fluxo de trabalho para o GitHub Actions
shortTitle: Comandos do fluxo de trabalho
intro: Você pode usar comandos do fluxo de trabalho ao executar comandos do shell em um fluxo de trabalho ou no código de uma ação.
defaultTool: bash
redirect_from:
  - /articles/development-tools-for-github-actions
  - /github/automating-your-workflow-with-github-actions/development-tools-for-github-actions
  - /actions/automating-your-workflow-with-github-actions/development-tools-for-github-actions
  - /actions/reference/development-tools-for-github-actions
  - /actions/reference/logging-commands-for-github-actions
  - /actions/reference/workflow-commands-for-github-actions
  - /actions/learn-github-actions/workflow-commands-for-github-actions
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
---

{% data reusables.actions.enterprise-beta %}
{% data reusables.actions.enterprise-github-hosted-runners %}

## Sobre os comandos do fluxo de trabalho

As ações podem comunicar-se com a máquina do executor para definir as variáveis de ambiente, valores de saída usados por outras ações, adicionar mensagens de depuração aos registros de saída e outras tarefas.

A maioria dos comandos de fluxo de trabalho usa o comando `echo` em um formato específico, enquanto outros são chamados escrevendo um arquivo. Para obter mais informações, consulte ["Arquivos de ambiente".](#environment-files)

### Exemplo

{% bash %}

```bash{:copy}
echo "::workflow-command parameter1={data},parameter2={data}::{command value}"
```

{% endbash %}

{% powershell %}

```pwsh{:copy}
Write-Output "::workflow-command parameter1={data},parameter2={data}::{command value}"
```

{% endpowershell %}

{% note %}

**Observação:** Os nomes do comando do fluxo de trabalho e do parâmetro não diferenciam maiúsculas e minúsculas.

{% endnote %}

{% warning %}

**Aviso:** se você estiver usando um prompt do comando, omita as aspas duplas (`"`) ao usar comandos do fluxo de trabalho.

{% endwarning %}

## Usar comandos do fluxo de trabalho para acessar funções do kit de de ferramentas

O [actions/toolkit](https://github.com/actions/toolkit) inclui uma quantidade de funções que podem ser executadas como comandos do fluxo de trabalho. Use a sintaxe `::` para executar os comandos do fluxo de trabalho no arquivo YAML. Em seguida, esses comandos serão enviados para a o executor por meio do `stdout`. Por exemplo, em vez de usar o código para definir uma saída, como abaixo:

```javascript{:copy}
core.setOutput('SELECTED_COLOR', 'green');
```

### Example: Setting a value

Você pode usar o comando `set-output` no seu fluxo de trabalho para definir o mesmo valor:

{% bash %}

{% raw %}
```yaml{:copy}
      - name: Set selected color
        run: echo '::set-output name=SELECTED_COLOR::green'
        id: random-color-generator
      - name: Get color
        run: echo "The selected color is ${{ steps.random-color-generator.outputs.SELECTED_COLOR }}"
```
{% endraw %}

{% endbash %}

{% powershell %}

{% raw %}
```yaml{:copy}
      - name: Set selected color
        run: Write-Output "::set-output name=SELECTED_COLOR::green"
        id: random-color-generator
      - name: Get color
        run: Write-Output "The selected color is ${{ steps.random-color-generator.outputs.SELECTED_COLOR }}"
```
{% endraw %}

{% endpowershell %}

A tabela a seguir mostra quais funções do conjunto de ferramentas estão disponíveis dentro de um fluxo de trabalho:

| Função do kit de ferramentas | Comando equivalente do fluxo de trabalho                              |
| ---------------------------- | --------------------------------------------------------------------- |
| `core.addPath`               | Acessível usando o arquivo de ambiente `GITHUB_PATH`                  |
| `core.debug`                 | `debug` |{% ifversion fpt or ghes > 3.2 or ghae-issue-4929 or ghec %}
| `core.notice`                | `notice` 
{% endif %}
| `core.error`                 | `erro`                                                                |
| `core.endGroup`              | `endgroup`                                                            |
| `core.exportVariable`        | Acessível usando o arquivo de ambiente `GITHUB_ENV`                   |
| `core.getInput`              | Acessível por meio do uso da variável de ambiente `INPUT_{NAME}`      |
| `core.getState`              | Acessível por meio do uso da variável de ambiente `STATE_{NAME}`      |
| `core.isDebug`               | Acessível por meio do uso da variável de ambiente `RUNNER_DEBUG`      |
| `core.saveState`             | `save-state`                                                          |
| `core.setCommandEcho`        | `echo`                                                                |
| `core.setFailed`             | Usado como um atalho para `::error` e `exit 1`                        |
| `core.setOutput`             | `set-output`                                                          |
| `core.setSecret`             | `add-mask`                                                            |
| `core.startGroup`            | `grupo`                                                               |
| `core.warning`               | `aviso`                                                               |

## Definir um parâmetro de saída

Configura um parâmetro de saída da ação.

```{:copy}
::set-output name={name}::{value}
```

Opcionalmente, você também pode declarar os parâmetros de saída no arquivo de metadados de uma ação. Para obter mais informações, consulte "[Sintaxe de metadados para o {% data variables.product.prodname_actions %}](/articles/metadata-syntax-for-github-actions#outputs-for-docker-container-and-javascript-actions)".

### Example: Setting an output parameter

{% bash %}

```bash{:copy}
echo "::set-output name=action_fruit::strawberry"
```

{% endbash %}

{% powershell %}

```pwsh{:copy}
Write-Output "::set-output name=action_fruit::strawberry"
```

{% endpowershell %}

## Configurar uma mensagem de depuração

Imprime uma mensagem de erro no log. Você deve criar um segredo nomeado `ACTIONS_STEP_DEBUG` com o valor `true` para ver as mensagens de erro configuradas por esse comando no log. Para obter mais informações, consulte "[Habilitar o registro de depuração](/actions/managing-workflow-runs/enabling-debug-logging)".

```{:copy}
::debug::{message}
```

### Example: Setting a debug message

{% bash %}

```bash{:copy}
echo "::debug::Set the Octocat variable"
```

{% endbash %}

{% powershell %}

```pwsh{:copy}
Write-Output "::debug::Set the Octocat variable"
```

{% endpowershell %}

{% ifversion fpt or ghes > 3.2 or ghae-issue-4929 or ghec %}

## Configurando uma mensagem de aviso

Cria uma mensagem de aviso e a imprime no registro. {% data reusables.actions.message-annotation-explanation %}

```{:copy}
::notice file={name},line={line},endLine={endLine},title={title}::{message}
```

{% data reusables.actions.message-parameters %}

### Example: Setting a notice message

{% bash %}

```bash{:copy}
echo "::notice file=app.js,line=1,col=5,endColumn=7::Missing semicolon"
```

{% endbash %}

{% powershell %}

```pwsh{:copy}
Write-Output "::notice file=app.js,line=1,col=5,endColumn=7::Missing semicolon"
```

{% endpowershell %}
{% endif %}

## Configurar uma mensagem de aviso

Cria uma mensagem de aviso e a imprime no log. {% data reusables.actions.message-annotation-explanation %}

```{:copy}
::warning file={name},line={line},endLine={endLine},title={title}::{message}
```

{% data reusables.actions.message-parameters %}

### Example: Setting a warning message

{% bash %}

```bash{:copy}
echo "::warning file=app.js,line=1,col=5,endColumn=7::Missing semicolon"
```
{% endbash %}

{% powershell %}

```pwsh{:copy}
Write-Output "::warning file=app.js,line=1,col=5,endColumn=7::Missing semicolon"
```

{% endpowershell %}

## Configurar uma mensagem de erro

Cria uma mensagem de erro e a imprime no log. {% data reusables.actions.message-annotation-explanation %}

```{:copy}
::error file={name},line={line},endLine={endLine},title={title}::{message}
```

{% data reusables.actions.message-parameters %}

### Example: Setting an error message

{% bash %}

```bash{:copy}
echo "::error file=app.js,line=1,col=5,endColumn=7::Missing semicolon"
```

{% endbash %}

{% powershell %}

```pwsh{:copy}
Write-Output "::error file=app.js,line=1,col=5,endColumn=7::Missing semicolon"
```

{% endpowershell %}

## Agrupar linhas dos registros

Cria um grupo expansível no registro. Para criar um grupo, use o comando `grupo` e especifique um `título`. Qualquer coisa que você imprimir no registro entre os comandos `grupo` e `endgroup` estará aninhada dentro de uma entrada expansível no registro.

```{:copy}
::group::{title}
::endgroup::
```

### Example: Grouping log lines

{% bash %}

```yaml{:copy}
jobs:
  bash-example:
    runs-on: ubuntu-latest
    steps:
      - name: Group of log lines
        run: |
            echo "::group::My title"
            echo "Inside group"
            echo "::endgroup::"
```

{% endbash %}

{% powershell %}

```yaml{:copy}
jobs:
  powershell-example:
    runs-on: windows-latest
    steps:
      - name: Group of log lines
        run: |
            Write-Output "::group::My title"
            Write-Output "Inside group"
            Write-Output "::endgroup::"
```

{% endpowershell %}

![Grupo dobrável no registro da execução do fluxo de trabalho](/assets/images/actions-log-group.png)

## Mascarar um valor no registro

```{:copy}
::add-mask::{value}
```

Mascarar um valor evita que uma string ou variável seja impressa no log. Cada palavra mascarada separada por espaço em branco é substituída pelo caractere `*`. Você pode usar uma variável de ambiente ou string para o `value` da máscara.

### Example: Masking a string

Quando você imprime `"Mona The Octocat"` no log, você verá `"***"`.

{% bash %}

```bash{:copy}
echo "::add-mask::Mona The Octocat"
```

{% endbash %}

{% powershell %}

```pwsh{:copy}
Write-Output "::add-mask::Mona The Octocat"
```

{% endpowershell %}

### Example: Masking an environment variable

Ao imprimir a variável `MY_NAME` ou o valor `"Mona The Octocat"` no log, você verá `"***"` em vez de `"Mona The Octocat"`.

{% bash %}

```yaml{:copy}
jobs:
  bash-example:
    runs-on: ubuntu-latest
    env:
      MY_NAME: "Mona The Octocat"
    steps:
      - name: bash-version
        run: echo "::add-mask::$MY_NAME"
```

{% endbash %}

{% powershell %}

```yaml{:copy}
jobs:
  powershell-example:
    runs-on: windows-latest
    env:
      MY_NAME: "Mona The Octocat"
    steps:
      - name: powershell-version
        run: Write-Output "::add-mask::$env:MY_NAME"
```

{% endpowershell %}

## Parar e iniciar os comandos no fluxo de trabalho

Para de processar quaisquer comandos de fluxo de trabalho. Esse comando especial permite fazer o registro do que você desejar sem executar um comando do fluxo de trabalho acidentalmente. Por exemplo, é possível parar o log para gerar um script inteiro que tenha comentários.

```{:copy}
::stop-commands::{endtoken}
```

Para parar o processamento de comandos de fluxo de trabalho, passe um token único para `stop-commands`. Para retomar os comandos do fluxo de trabalho, passe o mesmo token que você usou para parar os comandos do fluxo de trabalho.

{% warning %}

**Aviso:** Certifique-se de que o token que você está usando é gerado aleatoriamente e exclusivo para cada execução.

{% endwarning %}

```{:copy}
::{endtoken}::
```

### Example: Stopping and starting workflow commands

{% bash %}

{% raw %}

```yaml{:copy}
jobs:
  workflow-command-job:
    runs-on: ubuntu-latest
    steps:
      - name: Disable workflow commands
        run: |
          echo '::warning:: This is a warning message, to demonstrate that commands are being processed.'
          stopMarker=$(uuidgen)
          echo "::stop-commands::$stopMarker"
          echo '::warning:: This will NOT be rendered as a warning, because stop-commands has been invoked.'
          echo "::$stopMarker::"
          echo '::warning:: This is a warning again, because stop-commands has been turned off.'
```
{% endraw %}

{% endbash %}

{% powershell %}

{% raw %}
```yaml{:copy}
jobs:
  workflow-command-job:
    runs-on: windows-latest
    steps:
      - name: Disable workflow commands
        run: |
          Write-Output '::warning:: This is a warning message, to demonstrate that commands are being processed.'
          $stopMarker = New-Guid
          Write-Output "::stop-commands::$stopMarker"
          Write-Output '::warning:: This will NOT be rendered as a warning, because stop-commands has been invoked.'
          Write-Output "::$stopMarker::"
          Write-Output '::warning:: This is a warning again, because stop-commands has been turned off.'
```

{% endraw %}

{% endpowershell %}

## Eco de saídas de comando

Habilita ou desabilita o eco de comandos de fluxo de trabalho. Por exemplo, se você usar o comando `set-output` em um fluxo de trabalho, ele definirá um parâmetro de saída, mas o registro da execução do fluxo de trabalho não irá mostrar o comando em si. Se você habilitar o comando de eco, o registro mostrará o comando, como `::set-output name={name}::{value}`.

```{:copy}
::echo::on
::echo::off
```

O eco de comandos encontra-se desabilitado por padrão. No entanto, um comando de fluxo de trabalho será refletido se houver algum erro que processa o comando.

Os comandos `add-mask`, `depurar`, `aviso` e `erro` não são compatíveis com o eco, porque suas saídas já estão ecoadas no registros.

Você também pode habilitar o comando de eco globalmente ativando o registrode depuração da etapa usando o segredo `ACTIONS_STEP_DEBUG`. Para obter mais informações, consulte[Habilitando o log de depuração](/actions/managing-workflow-runs/enabling-debug-logging)". Em contraste, o comando do fluxo de trabalho `echo` permite que você habilite o comando de eco em um nível mais granular em vez de habilitá-lo para cada fluxo de trabalho em um repositório.

### Example: Toggling command echoing

{% bash %}

```yaml{:copy}
jobs:
  workflow-command-job:
    runs-on: ubuntu-latest
    steps:
      - name: toggle workflow command echoing
        run: |
          echo '::set-output name=action_echo::disabled'
          echo '::echo::on'
          echo '::set-output name=action_echo::enabled'
          echo '::echo::off'
          echo '::set-output name=action_echo::disabled'
```

{% endbash %}

{% powershell %}

```yaml{:copy}
jobs:
  workflow-command-job:
    runs-on: windows-latest
    steps:
      - name: toggle workflow command echoing
        run: |
          write-output "::set-output name=action_echo::disabled"
          write-output "::echo::on"
          write-output "::set-output name=action_echo::enabled"
          write-output "::echo::off"
          write-output "::set-output name=action_echo::disabled"
```

{% endpowershell %}

The example above prints the following lines to the log:

```{:copy}
::set-output name=action_echo::enabled
::echo::off
```

Apenas os comandos do fluxo de trabalho `set-output` e `echo` estão incluídos no registro, porque o recurso de comandos só estava habilitado quando eles foram executados. Mesmo que nem sempre ele esteja ecoado, o parâmetro de saída é definido em todos os casos.

## Enviar valores para as ações anterior e posterior

Você pode usar o comando `save-state` para criar variáveis de ambiente para compartilhar com as ações `pre:` ou `post:`. Por exemplo, você pode criar um arquivo com a ação `pre:`, passar o local do arquivo para a ação `main:` e, em seguida, usar a ação `post:` para excluir o arquivo. Como alternativa, você pode criar um arquivo com a ação `main:` ação, passar o local do arquivo para a ação `post:`, além de usar a ação `post:` para excluir o arquivo.

Se você tiver múltiplas ações `pre:` ou `post:` ações, você poderá apenas acessar o valor salvo na ação em que `save-state` foi usado. Para obter mais informações sobre a ação `post:`, consulte "[Sintaxe de metadados para {% data variables.product.prodname_actions %}](/actions/creating-actions/metadata-syntax-for-github-actions#runspost)".

O comando `save-state` pode ser executado apenas em uma ação e não está disponível para arquivos YAML. O valor salvo é armazenado como um valor de ambiente com o prefixo `STATE_`.

Este exemplo usa o JavaScript para executar o comando `save-state`. A variável de ambiente resultante é denominada `STATE_processID` com o valor de `12345`:

```javascript{:copy}
console.log('::save-state name=processID::12345')
```

A variável `STATE_processID` está exclusivamente disponível para o script de limpeza executado na ação `principal`. Este exemplo é executado em `principal` e usa o JavaScript para exibir o valor atribuído à variável de ambiente `STATE_processID`:

```javascript{:copy}
console.log("O PID em execução a partir da ação principal é: " +  process.env.STATE_processID);
```

## Arquivos de ambiente

Durante a execução de um fluxo de trabalho, o executor gera arquivos temporários que podem ser usados para executar certas ações. O caminho para esses arquivos são expostos através de variáveis de ambiente. Você precisará usar a codificação UTF-8 ao escrever para esses arquivos para garantir o processamento adequado dos comandos. Vários comandos podem ser escritos no mesmo arquivo, separados por novas linhas.

{% powershell %}

{% note %}

**Note:** PowerShell versions 5.1 and below (`shell: powershell`) do not use UTF-8 by default, so you must specify the UTF-8 encoding. Por exemplo:

```yaml{:copy}
jobs:
  legacy-powershell-example:
    runs-on: windows-latest
    steps:
      - shell: powershell
        run: |
          "mypath" | Out-File -FilePath $env:GITHUB_PATH -Encoding utf8 -Append
```

PowerShell Core versions 6 and higher (`shell: pwsh`) use UTF-8 by default. Por exemplo:

```yaml{:copy}
jobs:
  powershell-core-example:
    runs-on: windows-latest
    steps:
      - shell: pwsh
        run: |
          "mypath" >> $env:GITHUB_PATH
```

{% endnote %}

{% endpowershell %}

## Definir uma variável de ambiente

{% bash %}

```bash{:copy}
echo "{environment_variable_name}={value}" >> $GITHUB_ENV
```

{% endbash %}

{% powershell %}

- Using PowerShell version 6 and higher:
```pwsh{:copy}
"{environment_variable_name}={value}" >> $env:GITHUB_ENV
```

- Using PowerShell version 5.1 and below:
```powershell{:copy}
"{environment_variable_name}={value}" | Out-File -FilePath $env:GITHUB_ENV -Encoding utf8 -Append
```

{% endpowershell %}

Você pode tornar uma variável de ambiente disponível para quaisquer etapas subsequentes em um trabalho de fluxo de trabalho definindo ou atualizando a variável de ambiente e gravando isso no arquivo de ambiente `GITHUB_ENV`. A etapa que cria ou atualiza a variável de ambiente não tem acesso ao novo valor, mas todos os passos subsequentes em um trabalho terão acesso. Os nomes das variáveis de ambiente são diferenciam maiúsculas e minúsculas e você pode incluir a pontuação. Para obter mais informações, consulte "[Variáveis de ambiente](/actions/learn-github-actions/environment-variables)".

### Exemplo

{% bash %}

{% raw %}
```yaml{:copy}
steps:
  - name: Set the value
    id: step_one
    run: |
      echo "action_state=yellow" >> $GITHUB_ENV
  - name: Use the value
    id: step_two
    run: |
      echo "${{ env.action_state }}" # This will output 'yellow'
```
{% endraw %}

{% endbash %}

{% powershell %}

{% raw %}
```yaml{:copy}
steps:
  - name: Set the value
    id: step_one
    run: |
      "action_state=yellow" >> $env:GITHUB_ENV
  - name: Use the value
    id: step_two
    run: |
      Write-Output "${{ env.action_state }}" # This will output 'yellow'
```
{% endraw %}

{% endpowershell %}

### Strings de linha múltipla

Para strings linha múltipla, você pode usar um delimitador com a seguinte sintaxe.

```{:copy}
{name}<<{delimiter}
{value}
{delimiter}
```

#### Exemplo

This example uses `EOF` as a delimiter, and sets the `JSON_RESPONSE` environment variable to the value of the `curl` response.

{% bash %}

```yaml{:copy}
steps:
  - name: Set the value in bash
    id: step_one
    run: |
      echo 'JSON_RESPONSE<<EOF' >> $GITHUB_ENV
      curl https://example.lab >> $GITHUB_ENV
      echo 'EOF' >> $GITHUB_ENV
```

{% endbash %}

{% powershell %}

```yaml{:copy}
steps:
  - name: Set the value in pwsh
    id: step_one
    run: |
      "JSON_RESPONSE<<EOF" >> $env:GITHUB_ENV
      (Invoke-WebRequest -Uri "https://example.lab").Content >> $env:GITHUB_ENV
      "EOF" >> $env:GITHUB_ENV
    shell: pwsh
```

{% endpowershell %}

## Adicionar um caminho do sistema

Prepara um diretório para a variável `PATH` do sistema e disponibiliza automaticamente para todas as ações subsequentes no trabalho atual; a ação atualmente em execução não pode acessar a variável de caminho atualizada. Para ver os caminhos atualmente definidos para o seu trabalho, você pode usar o `echo "$PATH"` em uma etapa ou ação.

{% bash %}

```bash{:copy}
echo "{path}" >> $GITHUB_PATH
```
{% endbash %}

{% powershell %}

```pwsh{:copy}
"{path}" >> $env:GITHUB_PATH
```

{% endpowershell %}

### Exemplo

Este exemplo demonstra como adicionar o diretório `$HOME/.local/bin` ao `PATH`:

{% bash %}

```bash{:copy}
echo "$HOME/.local/bin" >> $GITHUB_PATH
```

{% endbash %}


This example demonstrates how to add the user `$env:HOMEPATH/.local/bin` directory to `PATH`:

{% powershell %}

```pwsh{:copy}
"$env:HOMEPATH/.local/bin" >> $env:GITHUB_PATH
```

{% endpowershell %}

---
title: Sobre as pré-compilações de codespaces
shortTitle: Sobre as pré-criações
intro: As pré-criações de codespaces ajudam a acelerar a criação de novos codespaces.
versions:
  fpt: '*'
  ghec: '*'
topics:
  - Codespaces
product: '{% data reusables.gated-features.codespaces %}'
---

{% data reusables.codespaces.prebuilds-beta-note %}

## Visão Geral

A pré-construção de seus codespaces permite que você seja mais produtivo e tenha acesso ao seu codespace mais rápido, independentemente do tamanho e complexidade do seu projeto. Isso ocorre porque qualquer código-fonte, extensões de editor, dependências de projetos, comandos e configurações já foram baixadas, instaladas e aplicadas antes de criar um codespace para o seu projeto. Pense em uma pré-compilação como um modelo pronto para um codespace.

Sempre que você fizer alterações no repositório, {% data variables.product.prodname_codespaces %} irá usar {% data variables.product.prodname_actions %} para atualizar automaticamente suas pré-criações.

Quando as pré-criações estiverem disponíveis para um branch específic de um repositório e para sua região, você verá o a etiqueta "Pré-criação pronta de {% octicon "zap" aria-label="The zap icon" %}" na caixa de diálogo de tipo de máquina que é exibida quando você cria um codespace e vários tipos de máquina estão disponíveis.

![A caixa de diálogo para escolher um tipo de máquina](/assets/images/help/codespaces/choose-custom-machine-type.png)

## Sobre a cobrança para pré-criações de {% data variables.product.prodname_codespaces %}

{% data reusables.codespaces.billing-for-prebuilds %} Para obter detalhes de preços de armazenamento de {% data variables.product.prodname_codespaces %}, consulte[Sobre cobrança para {% data variables.product.prodname_codespaces %}](/billing/managing-billing-for-github-codespaces/about-billing-for-codespaces)."

O uso de codespaces criados usando pré-criações é cobrado na mesma frequência que os codespaces regulares.

## Sobre fazer push de alterações em branches com pré-criação

Cada push em um branch que tem uma configuração de pré-criação resulta em um fluxo de trabalho de ações gerenciadas por {% data variables.product.prodname_dotcom %} para atualizar o modelo de pré-criação. O fluxo de trabalho da pré-criação tem um limite de concorrência de uma execução de fluxo de trabalho de cada vez para uma determinada configuração de pré-compilação, a não ser que tenham sido feitas alterações que afetem a configuração do contêiner de desenvolvimento do repositório associado. Para obter mais informações, consulte "[Introdução a contêineres de desenvolvimento](/codespaces/setting-up-your-project-for-codespaces/configuring-codespaces-for-your-project)". Se uma execução já estiver em andamento, a execução do fluxo de trabalho que foi enfileirada mais recentemente será executada a seguir, depois que a execução atual for concluída.

Isso significa que se houver push muito frequentes no repositório, a criação pré-compilada ocorrerá pelo menos com a frequência necessária para executar o fluxo de trabalho pré-criado. Ou seja, se a execução do fluxo de trabalho normalmente leva uma hora para ser concluída, serão criadas pré-compilações para o repositório em aproximadamente uma hora, se a execução for bem sucedida, ou mais frequentemente se houve pushes que alteram o contêiner de desenvolvimento no branch.

Por exemplo, vamos imaginar que 5 pushes são feitos, em rápida sucessão, para um branch que tem uma configuração de pré-compilação. Nesta situação:

* A execução de um fluxo de trabalho é iniciada para o primeiro push, para atualizar o modelo de pré-compilação.
* Se os 4 pushes restantes não afetarem a configuração do contêiner de desenvolvimento, o fluxo de trabalho será executado em um estado de "pendência".

  Se qualquer um dos 4 pushes restantes alterar a configuração do contêiner de desenvolvimento, o serviço não irá ignorá-lo e irá executar imediatamente o fluxo de trabalho pré-criação, atualizando a pré-compilação adequadamente se puder.

* Quando a primeira execução for concluída, as execuções dos fluxos de trabalho para os pushes 2, 3 e 4 serão canceladas, e o último fluxo de trabalho na fila (para push 5) será executado e será atualizado o modelo de pré-compilação. 

---
title: Solução de problemas de detecção de dependências vulneráveis
intro: 'Se as informações sobre dependências relatadas por {% data variables.product.product_name %} não são o que você esperava, há uma série de pontos a considerar, e várias coisas que você pode verificar.'
shortTitle: Solução de problemas de vulnerabilidade
redirect_from:
  - /github/managing-security-vulnerabilities/troubleshooting-the-detection-of-vulnerable-dependencies
  - /code-security/supply-chain-security/troubleshooting-the-detection-of-vulnerable-dependencies
  - /code-security/supply-chain-security/managing-vulnerabilities-in-your-projects-dependencies/troubleshooting-the-detection-of-vulnerable-dependencies
versions:
  fpt: '*'
  ghes: '*'
  ghae: issue-4864
  ghec: '*'
type: how_to
topics:
  - Dependabot
  - Alerts
  - Troubleshooting
  - Errors
  - Security updates
  - Dependencies
  - Vulnerabilities
  - CVEs
  - Repositories
---

{% data reusables.dependabot.beta-security-and-version-updates %}
{% data reusables.dependabot.result-discrepancy %}

## Por que algumas dependências parecem estar faltando?

O {% data variables.product.prodname_dotcom %} gera e exibe dados de dependência de maneira diferente de outras ferramentas. Consequentemente, se você usou outra ferramenta para identificar dependências, quase certamente verá resultados diferentes. Considere o seguinte:

*   {% data variables.product.prodname_advisory_database %} é uma das fontes de dados que {% data variables.product.prodname_dotcom %} usa para identificar dependências vulneráveis. É um banco de dados gratuito e curado com informações sobre vulnerabilidade para ecossistemas de pacote comum em {% data variables.product.prodname_dotcom %}. Inclui tanto dados relatados diretamente para {% data variables.product.prodname_dotcom %} de {% data variables.product.prodname_security_advisories %} quanto os feeds oficiais e as fontes comunitárias. Estes dados são revisados e curados por {% data variables.product.prodname_dotcom %} para garantir que informações falsas ou não acionáveis não sejam compartilhadas com a comunidade de desenvolvimento. {% data reusables.security-advisory.link-browsing-advisory-db %}
*   O gráfico de dependências analisa todos os arquivos conhecidos de manifesto de pacote no repositório de um usuário. Por exemplo, para o npm, ele irá analisar o arquivo _package-lock.json_. Ele constrói um gráfico de todas as dependências do repositório e dependências públicas. Isso acontece quando você habilita o gráfico de dependências e quando alguém faz push para o branch-padrão, e inclui commits que fazem alterações em um formato de manifesto compatível. Para obter mais informações, consulte "[Sobre o gráfico de dependências](/github/visualizing-repository-data-with-graphs/about-the-dependency-graph)" e "[Solucionando problemas no gráfico de dependências](/code-security/supply-chain-security/understanding-your-software-supply-chain/troubleshooting-the-dependency-graph)".
*   {% data variables.product.prodname_dependabot %} verifica qualquer push, para o branch-padrão, que contém um arquivo de manifesto. Quando um novo registro de vulnerabilidade é adicionado, ele verifica todos os repositórios existentes e gera um alerta para cada repositório vulnerável. {% data variables.product.prodname_dependabot_alerts %} são agregados ao nível do repositório, em vez de criar um alerta por vulnerabilidade. Para obter mais informações, consulte "[Sobre {% data variables.product.prodname_dependabot_alerts %}](/code-security/supply-chain-security/about-alerts-for-vulnerable-dependencies)".
*   {% ifversion fpt or ghec or ghes > 3.2 %}{% data variables.product.prodname_dependabot_security_updates %} são acionados quando você recebe um alerta sobre uma dependência vulnerável no repositório. Sempre que possível, {% data variables.product.prodname_dependabot %} cria um pull request no repositório para atualizar a dependência vulnerável à versão mínima segura necessária para evitar a vulnerabilidade. Para obter mais informações, consulte "[Sobre {% data variables.product.prodname_dependabot_security_updates %}](/github/managing-security-vulnerabilities/about-dependabot-security-updates)" e "[Solução de problemas de {% data variables.product.prodname_dependabot %}](/github/managing-security-vulnerabilities/troubleshooting-dependabot-errors)".

    {% endif %}{% data variables.product.prodname_dependabot %} não pesquisa repositórios com relação a dependências vulneráveis de uma programação, mas o faz quando algo muda. Por exemplo, aciona-se uma varredura quando uma nova dependência é adicionada ({% data variables.product.prodname_dotcom %} verifica isso em cada push), ou quando uma nova vulnerabilidade é adicionada ao banco de dados da consultoria{% ifversion ghes or ghae-issue-4864 %} e sincronizado com {% data variables.product.product_location %}{% endif %}. Para obter mais informações, consulte "[Sobre {% data variables.product.prodname_dependabot_alerts %}](/code-security/supply-chain-security/about-alerts-for-vulnerable-dependencies#detection-of-vulnerable-dependencies)".

## {% data variables.product.prodname_dependabot_alerts %} só está relacionado a dependências vulneráveis nos manifestos e arquivos de bloqueio?

Os {% data variables.product.prodname_dependabot_alerts %} aconselham você com relação a dependências que você deve atualizar, incluindo dependências transitivas, em que a versão pode ser determinada a partir de um manifesto ou de um arquivo de bloqueio. {% ifversion fpt or ghec or ghes > 3.2 %}{% data variables.product.prodname_dependabot_security_updates %} sugere apenas uma mudança em que {% data variables.product.prodname_dependabot %} pode "corrigir" diretamente a dependência, ou seja, quando são:
* Dependências diretas, que são definidas explicitamente em um manifesto ou arquivo de bloqueio
* Dependências transitórias declaradas em um arquivo de bloqueio{% endif %}

**Verifique**: A vulnerabilidade não detectada para um componente não especificado no manifesto ou no arquivo de bloqueio do repositório?

## Por que não recebo alertas de vulnerabilidade em alguns ecossistemas?

O {% data variables.product.prodname_dotcom %} limita seu suporte a alertas de vulnerabilidade a um conjunto de ecossistemas onde podemos fornecer dados de alta qualidade e relevantes. As vulnerabilidades curadas no {% data variables.product.prodname_advisory_database %}, o gráfico de dependências, {% ifversion fpt or ghec %}{% data variables.product.prodname_dependabot %} atualizações de segurança, {% endif %}e  {% data variables.product.prodname_dependabot_alerts %} são fornecidos para vários ecossistemas, incluindo o Maven do Javaen, o npm do JavaScript e o Yarn, Nuget do .NET's, Pip Python, RubyGems e PHP Composer. Nós continuaremos a adicionar suporte para mais ecossistemas ao longo do tempo. Para uma visão geral dos ecossistemas de pacotes suportados por nós, consulte "[Sobre o gráfico de dependências](/github/visualizing-repository-data-with-graphs/about-the-dependency-graph#supported-package-ecosystems)".

Vale a pena observar que as consultorias de segurança de {% data variables.product.prodname_dotcom %} podem existir para outros ecossistemas. As informações em uma consultoria de segurança são fornecidas pelos mantenedores de um determinado repositório. Estes dados não são curados da mesma forma que as informações relativas aos ecossistemas suportados. {% ifversion fpt or ghec %}Para obter mais informações, consulte "[Sobre consultorias de segurança de {% data variables.product.prodname_dotcom %}](/github/managing-security-vulnerabilities/about-github-security-advisories){% endif %}

**Verificar**: A vulnerabilidade não capturada se aplica a um ecossistema não suportado?

## O {% data variables.product.prodname_dependabot %} gera alertas de vulnerabilidades que são conhecidas há muitos anos?

O {% data variables.product.prodname_advisory_database %} foi lançado em novembro de 2019 e preencheu, inicialmente, a inclusão de informações de vulnerabilidade para os ecossistemas compatíveis a partir de 2017. Ao adicionar CVEs ao banco de dados, priorizamos a curadoria de CVEs mais recentes e CVEs que afetam versões mais recentes do software.

Algumas informações sobre vulnerabilidades mais antigas estão disponíveis, especialmente quando estes CVEs estão particularmente disseminados. No entanto algumas vulnerabilidades antigas não estão incluídas no {% data variables.product.prodname_advisory_database %}. Se houver uma vulnerabilidade antiga específica que você precisar incluir no banco de dados, entre em contato com {% data variables.contact.contact_support %}.

**Verifique**: A vulnerabilidade não detectada tem uma data de publicação anterior a 2017 no Banco de Dados Nacional de Vulnerabilidade?

## Por que o {% data variables.product.prodname_advisory_database %} usa um subconjunto de dados de vulnerabilidade publicada?

Algumas ferramentas de terceiros usam dados de CVE não descurados que não são verificados ou filtrados por um ser humano. Isto significa que os CVEs com erros de etiqueta ou de gravidade, ou outros problemas de qualidade, gerarão alertas mais frequentes, mais ruidosos e menos úteis.

Uma vez que {% data variables.product.prodname_dependabot %} usa dados curados em {% data variables.product.prodname_advisory_database %}, o volume de alertas pode ser menor, mas os alertas que você recebe serão precisos e relevantes.

{% ifversion fpt or ghec %}
## Cada vulnerabilidade de dependência gera um alerta separado?

Quando uma dependência tem várias vulnerabilidades, gera-se um alerta para cada vulnerabilidade no nível da consultoria mais manifesto.

![Captura de tela da aba de {% data variables.product.prodname_dependabot_alerts %} que mostra dois alertas do mesmo pacote com manifestos diferentes.](/assets/images/help/repository/dependabot-alerts-view.png)

O legado de {% data variables.product.prodname_dependabot_alerts %} foi agrupado em um único alerta agregado com todas as vulnerabilidades para a mesma dependência. Se você acessar um link para um alerta de legadode {% data variables.product.prodname_dependabot %}, você será redirecionado para a aba de {% data variables.product.prodname_dependabot_alerts %} filtrada para exibir vulnerabilidades para esse pacote e manifesto dependente.

![Captura de tela da aba {% data variables.product.prodname_dependabot_alerts %} que mostra os alertas filtrados da navegação até um alerta de legado de {% data variables.product.prodname_dependabot %}.](/assets/images/help/repository/legacy-dependabot-alerts-view.png)

A contagem de {% data variables.product.prodname_dependabot_alerts %} em {% data variables.product.prodname_dotcom %} mostra um total para o número de alertas, que é o número de vulnerabilidades, não o número de dependências.

**Verifique**: Se houver discrepância no total que você está vendo, verifique se você não está comparando números de alerta com números de dependência. Também verifique se você está visualizando todos os alertas e não um subconjunto de alertas filtrados.
{% endif %}

## Leia mais

- "[Sobre {% data variables.product.prodname_dependabot_alerts %}](/code-security/supply-chain-security/about-alerts-for-vulnerable-dependencies)"
- "[Visualizando {% data variables.product.prodname_dependabot_alerts %} para dependências vulneráveis](/github/managing-security-vulnerabilities/viewing-and-updating-vulnerable-dependencies-in-your-repository)"
- "[Gerenciar as configurações de segurança e análise para o seu repositório](/github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository)"
- "[Solucionando problemas do gráfico de dependências](/code-security/supply-chain-security/understanding-your-software-supply-chain/troubleshooting-the-dependency-graph)"{% ifversion fpt or ghec or ghes > 3.2 %}
- "[Solucionar problemas de {% data variables.product.prodname_dependabot %}](/github/managing-security-vulnerabilities/troubleshooting-dependabot-errors)"{% endif %}

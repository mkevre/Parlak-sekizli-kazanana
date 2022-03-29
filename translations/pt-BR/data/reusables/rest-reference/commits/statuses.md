## Status do commit

A API de status permite que serviços externos marquem commits com status de `erro`, `falha`, `pendente` ou `sucesso`, o que é refletido em pull requests que envolvem esses commits.

Os status também podem incluir uma `descrição` opcional e `target_url`, e é altamente recomendável fornecê-los, pois tornam o status muito mais útil na interface de usuário do GitHub.

Como exemplo, um uso comum é para serviços de integração contínua para marcar commits como criações que passam ou que falham usando o status.  O `target_url` seria a URL completa para a saída da criação, e a `descrição` seria o resumo de alto nível do que aconteceu com a criação.

Os status podem incluir um `contexto` para indicar qual serviço está fornecendo esse status. Por exemplo, você pode fazer com que o seu serviço de integração contínua faça push status com um contexto de `ci`, e uma ferramenta de auditoria de segurança faça push dos status com um contexto de `segurança`.  Você pode usar [Obter o status combinado para uma referência específica](/rest/reference/commits#get-the-combined-status-for-a-specific-reference) para recuperar todo o status de um commit.

Observe que o `escopo do OAuth` [repo:status](/developers/apps/scopes-for-oauth-apps) concede acesso direcionado a status **sem** conceder acesso ao código do repositório, enquanto o escopo `repo` concede permissão para o código e para status.

Se você está desenvolvendo um aplicativo GitHub e deseja fornecer informações mais detalhadas sobre um serviço externo, você deverá usar a [API de verificação](/rest/reference/checks).
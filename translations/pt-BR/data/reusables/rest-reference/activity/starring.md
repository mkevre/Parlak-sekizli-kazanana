## Marcar com uma estrela

Marcar o repositório como uma estrela é uma funcionalidade que permite aos usuários favoritar os repositórios. As estrelas são exibidas ao lado dos repositórios para mostrar um nível de interesse aproximado. As estrelas não têm efeito nas notificações ou no feed da atividade.

### Marcar como estrela vs. Inspecionar

Em agosto de 2012, [mudamos a forma como a inspeção funciona](https://github.com/blog/1204-notifications-stars) em {% data variables.product.prodname_dotcom %}. Muitas aplicações de cliente da API podem estar usando os pontos de extremidade originais de "inspetor" para acessar estes dados. Agora você pode começar a usar os pontos de extremidade "estrela" (descritos abaixo). Para obter mais informações, consulte a [Post de alteração da API de Inspeção](https://developer.github.com/changes/2012-09-05-watcher-api/) e a [API de Inspeção do repositório](/rest/reference/activity#watching)".

### Tipos de mídia personalizados para marcar como estrela

Existe um tipo de mídia personalizado com suporte para a API REST estrelada. Ao usar este tipo de mídia personalizada, você receberá uma resposta com a propriedade do registro de tempo `starred_at`, que indica o tempo que a estrela foi criada. A resposta também tem uma segunda propriedade que inclui o recurso retornado quando o tipo de mídia personalizado não está incluído. A propriedade que contém o recurso será `usuário` ou `repositório`.

    application/vnd.github.v3.star+json

Para obter mais informações sobre os tipos de mídia, consulte "[Tipos de mídia personalizados](/rest/overview/media-types)".
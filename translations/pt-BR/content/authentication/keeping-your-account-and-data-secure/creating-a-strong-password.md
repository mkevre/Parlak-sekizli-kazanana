---
title: Criar uma senha forte
intro: 'Proteja sua conta em {% ifversion ghae %}{% data variables.product.product_name %}{% else %}{% data variables.product.product_location %}{% endif %} com uma senha forte e única usando um gerenciador de senhas.'
redirect_from:
  - /articles/what-is-a-strong-password
  - /articles/creating-a-strong-password
  - /github/authenticating-to-github/creating-a-strong-password
  - /github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-strong-password
versions:
  fpt: '*'
  ghes: '*'
  ghec: '*'
topics:
  - Identity
  - Access management
shortTitle: Criar uma senha forte
---

Você deve escolher ou gerar uma senha para a sua conta em {% ifversion ghae %}{% data variables.product.product_name %}{% else %}{% data variables.product.product_location %}{% endif %} que seja pelo menos:
- {% ifversion ghes %}Sete{% else %}Oito{% endif %} caracteres, se incluir um número e uma letra minúscula, ou
- 15 caracteres com qualquer combinação de caracteres

Para manter sua conta protegida, é recomendável seguir estas práticas recomendadas:
- Use um gerenciador de senhas, como [LastPass](https://lastpass.com/) ou [1Password](https://1password.com/) para gerar uma senha de pelo menos 15 caracteres.
- Gere uma senha exclusiva para o {% data variables.product.product_name %}. Se você usar sua senha {% data variables.product.product_name %} em outro lugar e o serviço estiver comprometido, os invasores ou outros atores maliciosos poderiam usar essa informação para acessar sua conta em {% ifversion ghae %}{% data variables.product.product_name %}{% else %}{% data variables.product.product_location %}{% endif %}.

- Configure a autenticação de dois fatores para sua conta pessoal. Para obter mais informações, consulte "[Sobre a autenticação de dois fatores](/articles/about-two-factor-authentication)".
- Nunca compartilhe sua senha, mesmo com um possível colaborador. Cada pessoa deve usar a própria conta pessoal no {% data variables.product.product_name %}. Para obter mais informações sobre maneiras de colaborar, consulte: "[Convidar colaboradores para um repositório pessoal](/articles/inviting-collaborators-to-a-personal-repository)", "[Sobre modelos de desenvolvimento colaborativo](/articles/about-collaborative-development-models/)" ou "[Colaborar com grupos em organizações](/organizations/collaborating-with-groups-in-organizations/)".

{% data reusables.repositories.blocked-passwords %}

Você só pode usar sua senha para entrar no {% data variables.product.product_name %} usando seu navegador. Ao efetuar a autenticação no {% data variables.product.product_name %} de outra forma, como, por exemplo, linha de comando ou API, você deve usar outras credenciais. Para obter mais informações, consulte "[Sobre a autenticação do {% data variables.product.prodname_dotcom %}](/github/authenticating-to-github/about-authentication-to-github)".

{% ifversion fpt or ghec %}{% data reusables.user-settings.password-authentication-deprecation %}{% endif %}

## Leia mais

- "[Armazenar suas credenciais de {% data variables.product.product_name %} no Git](/github/getting-started-with-github/caching-your-github-credentials-in-git/)"
- "[Manter a conta e os dados seguros](/articles/keeping-your-account-and-data-secure/)"

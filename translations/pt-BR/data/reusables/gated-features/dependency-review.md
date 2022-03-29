{%- ifversion fpt %}
Dependency review is enabled on public repositories. Dependency review is also available in private repositories owned by organizations that use {% data variables.product.prodname_ghe_cloud %} and have a license for {% data variables.product.prodname_GH_advanced_security %}.

{%- elsif ghec %}
Revisão de dependências está incluída em {% data variables.product.product_name %} para repositórios públicos. To use dependency review in private repositories owned by organizations, you must have a license for {% data variables.product.prodname_GH_advanced_security %}.

{%- elsif ghes > 3.1 %}
Dependency review is available for organization-owned repositories in {% data variables.product.product_name %}. This feature requires a license for {% data variables.product.prodname_GH_advanced_security %}.

{%- elsif ghae-issue-4864 %}
Dependency review is available for organization-owned repositories in {% data variables.product.product_name %}. This is a {% data variables.product.prodname_GH_advanced_security %} feature (free during the beta release).

{%- endif %} {% data reusables.advanced-security.more-info-ghas %}
---
title: Visualizar el tiempo de ejecución de un job
intro: 'Puedes ver el tiempo de ejecución de un job, incluyendo los minutos facturables que este job ha acumulado.'
redirect_from:
  - /actions/managing-workflow-runs/viewing-job-execution-time
versions:
  fpt: '*'
  ghec: '*'
shortTitle: Visualizar el tiempo de ejecución de un job
---

{% data reusables.actions.enterprise-beta %}
{% data reusables.actions.enterprise-github-hosted-runners %}

Los minutos de ejecución facturables para un job solo se muestran en aquellos jobs que se ejecutan en repositorios privados que utilizan ejecutores hospedados en {% data variables.product.prodname_dotcom %} y se redondean al siguiente minuto. No hay minutos facturables cuando se utiliza {% data variables.product.prodname_actions %} en repositorios públicos o para trabajos que se ejecutan en ejecutores auto-hospedados.

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.actions-tab %}
{% data reusables.repositories.navigate-to-workflow %}
{% data reusables.repositories.view-run %}
1. Debajo del resumen del job, puedes ver el tiempo de ejecución del mismo. Para ver los detalles sobre el tiempo facturable de la ejecución de jobs, da clic en el tiempo que se muestra debajo de **tiempo facturable**. ![Enlace para los detalles de tiempo facturable y de ejecución](/assets/images/help/repository/view-run-billable-time.png)

   {% note %}

   **Nota:** El tiempo facturable que se muestra no incluye ningún multiplicador de minutos. Para ver tu uso total de {% data variables.product.prodname_actions %}, incluyendo los multiplicadores de minutos, consulta la sección "[Visualizar tu uso de {% data variables.product.prodname_actions %}](/billing/managing-billing-for-github-actions/viewing-your-github-actions-usage)".

   {% endnote %}

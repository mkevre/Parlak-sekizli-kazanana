---
title: Enabling automatic user license sync for your enterprise
intro: 'You can manage license usage across your {% data variables.product.prodname_enterprise %} environments by automatically syncing user licenses from {% data variables.product.product_location %} to {% data variables.product.prodname_ghe_cloud %}.'
redirect_from:
  - /enterprise/admin/installation/enabling-automatic-user-license-sync-between-github-enterprise-server-and-github-enterprise-cloud
  - /enterprise/admin/configuration/enabling-automatic-user-license-sync-between-github-enterprise-server-and-github-enterprise-cloud
  - /admin/configuration/enabling-automatic-user-license-sync-between-github-enterprise-server-and-github-enterprise-cloud
  - /admin/configuration/managing-connections-between-github-enterprise-server-and-github-enterprise-cloud/enabling-automatic-user-license-sync-between-github-enterprise-server-and-github-enterprise-cloud
  - /admin/configuration/managing-connections-between-your-enterprise-accounts/enabling-automatic-user-license-sync-between-github-enterprise-server-and-github-enterprise-cloud
permissions: Enterprise owners can enable automatic user license synchronization.
versions:
  ghes: '*'
type: how_to
topics:
  - Enterprise
  - GitHub Connect
  - Licensing
shortTitle: Sincronización automática de licencias de usuario
---

## Acerca de la sincronización de licencias

{% data reusables.enterprise-licensing.about-license-sync %} For more information, see "[About {% data variables.product.prodname_github_connect %}](/admin/configuration/configuring-github-connect/about-github-connect#data-transmission-for-github-connect)."

If you enable automatic user license sync for your enterprise, {% data variables.product.prodname_github_connect %} will automatically synchronize license usage between {% data variables.product.prodname_ghe_server %} and {% data variables.product.prodname_ghe_cloud %} weekly.

If you use multiple {% data variables.product.prodname_ghe_server %} instances, you can enable automatic license sync between each of your instances and the same organization or enterprise account on {% data variables.product.prodname_ghe_cloud %}.

{% data reusables.enterprise-licensing.view-consumed-licenses %}

También puedes cargar en forma manual información de licencias de usuario {% data variables.product.prodname_ghe_server %} en {% data variables.product.prodname_ghe_cloud %}. Para obtener más información, consulta la sección "[Sincronizar el uso de licencia entre {% data variables.product.prodname_ghe_server %} y {% data variables.product.prodname_ghe_cloud %}](/billing/managing-your-license-for-github-enterprise/syncing-license-usage-between-github-enterprise-server-and-github-enterprise-cloud)".

{% data reusables.enterprise-licensing.verified-domains-license-sync %}

## Habilitar la sincronización de licencias

Before enabling license synchronization on {% data variables.product.product_location %}, you must enable {% data variables.product.prodname_github_connect %}. Para obtener más información, consulta la sección "[Administrar {% data variables.product.prodname_github_connect %}](/admin/configuration/configuring-github-connect/managing-github-connect)".

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.github-connect-tab %}
1. En "El servidor puede sincronizar el recuento y uso de licencias de usuario", usa el menú desplegable y selecciona **Enabled** (Habilitado). ![Menú desplegable para habilitar la sincronización automática de licencias de usuario](/assets/images/enterprise/site-admin-settings/enable-user-license-drop-down.png)

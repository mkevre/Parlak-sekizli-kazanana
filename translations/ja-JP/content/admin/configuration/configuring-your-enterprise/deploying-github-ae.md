---
title: Deploying GitHub AE
intro: 'You can deploy {% data variables.product.product_name %} to an available Azure region.'
versions:
  ghae: '*'
topics:
  - Accounts
  - Enterprise
type: how_to
shortTitle: Deploy GitHub AE
redirect_from:
  - /get-started/signing-up-for-github/setting-up-a-trial-of-github-ae
---

## About deployment of {% data variables.product.product_name %}

{% data reusables.github-ae.github-ae-enables-you %} 詳しい情報については、「[{% data variables.product.prodname_ghe_managed %} について](/admin/overview/about-github-ae)」を参照してください。

After you purchase or start a trial of {% data variables.product.product_name %}, you can deploy {% data variables.product.product_name %} to an available Azure region. This guide refers to the Azure resource that contains the deployment of {% data variables.product.product_name %} as the {% data variables.product.product_name %} account. You'll use the Azure portal at [https://portal.azure.com](https://portal.azure.com) to deploy the {% data variables.product.product_name %} account.

## 必要な環境

- Before you can deploy {% data variables.product.product_name %}, you must request access from your {% data variables.product.company_short %} account team. {% data variables.product.company_short %} will enable deployment of {% data variables.product.product_name %} for your Azure subscription. If you haven't already purchased {% data variables.product.product_name %}, you can contact {% data variables.contact.contact_enterprise_sales %} to check your eligibility for a trial.

- You must have permission to perform the `/register/action` operation for the resource provider in Azure. The permission is included in the `Contributor` and `Owner` roles. For more information, see [Azure resource providers and types](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/resource-providers-and-types#register-resource-provider) in the Microsoft documentation.

## Deploying {% data variables.product.product_name %} with the {% data variables.actions.azure_portal %}

The {% data variables.actions.azure_portal %} allows you to deploy the {% data variables.product.product_name %} account in your Azure resource group.

1. Click one of the following two links to begin deployment of {% data variables.product.product_name %}. The link you should click depends on the Azure cloud where you plan to deploy {% data variables.product.product_name %}. For more information about Azure Government, see [What is Azure Government?](https://docs.microsoft.com/en-us/azure/azure-government/documentation-government-welcome) in the Microsoft documentation.

   - [Deploy {% data variables.product.product_name %} to Azure Commercial](https://aka.ms/create-github-ae-instance)
   - [Deploy {% data variables.product.product_name %} to Azure Government](https://aka.ms/create-github-ae-instance-gov)
1. To begin the process of adding a new {% data variables.product.product_name %} account, click **Create GitHub AE account**.
1. Complete the "Project details" and "Instance details" fields. ![{% data variables.actions.azure_portal %} search result](/assets/images/azure/github-ae-azure-portal-form.png)
    - **Account name:** The hostname for your enterprise
    - **Administrator username:** A username for the initial enterprise owner that will be created in {% data variables.product.product_name %}
    - **Administrator email:** The email address that will receive the login information
1. To review a summary of the proposed changes, click **Review + create**.
1. After the validation process has completed, click **Create**.

The email address you entered above will receive instructions on how to access your enterprise. After you have access, you can get started by following the initial setup steps. 詳しい情報については、「[{% data variables.product.product_name %} を初期化する](/admin/configuration/initializing-github-ae)」を参照してください。

{% note %}

**Note:** Software updates for your {% data variables.product.product_name %} deployment are performed by {% data variables.product.prodname_dotcom %}. For more information, see "[About upgrades to new releases](/admin/overview/about-upgrades-to-new-releases)."

{% endnote %}

## Navigating to your enterprise

You can use the {% data variables.actions.azure_portal %} to navigate to your {% data variables.product.product_name %} deployment. The resulting list includes all the {% data variables.product.product_name %} deployments in your Azure region.

1. On the {% data variables.actions.azure_portal %}, in the left panel, click **All resources**.
1. From the available filters, click **All types**, then deselect **Select all** and select **GitHub AE**: ![{% data variables.actions.azure_portal %} search result](/assets/images/azure/github-ae-azure-portal-type-filter.png)

## 次のステップ

- Once your deployment has been provisioned, the next step is to initialize {% data variables.product.product_name %}. 詳しい情報については、「[{% data variables.product.product_name %} を初期化する](/github-ae@latest/admin/configuration/configuring-your-enterprise/initializing-github-ae)」を参照してください。
- If you're trying {% data variables.product.product_name %}, you can upgrade to a full license at any time during the trial period by contacting contact {% data variables.contact.contact_enterprise_sales %}. If you haven't upgraded by the last day of your trial, then the deployment is automatically deleted. {% data variables.product.product_name %} を評価するための時間がさらに必要な場合は、{% data variables.contact.contact_enterprise_sales %} に連絡して延長をリクエストしてください。

## 参考リンク

- "[Enabling {% data variables.product.prodname_advanced_security %} features on {% data variables.product.product_name %}](/github/getting-started-with-github/about-github-advanced-security#enabling-advanced-security-features-on-github-ae)"
- "[{% data variables.product.product_name %} release notes](/github-ae@latest/admin/overview/github-ae-release-notes)" 

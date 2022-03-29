---
title: 关于代码空间的计费
shortTitle: 关于计费
intro: '查看定价并了解如何管理组织的 {% data variables.product.prodname_codespaces %} 计费。'
permissions: 'To manage billing for Codespaces for an organization, you must be an organization owner or a billing manager.'
versions:
  fpt: '*'
  ghec: '*'
type: overview
product: '{% data reusables.gated-features.codespaces %}'
topics:
  - Codespaces
  - Billing
---

## {% data variables.product.prodname_codespaces %} 定价

{% data variables.product.prodname_codespaces %} 的使用将针对团队和企业计划中的所有帐户计费，并且不包括任何权利。 个人帐户目前不为 {% data variables.product.prodname_codespaces %} 使用付费。

{% data variables.product.prodname_codespaces %} 使用按下表中的计量单位计费：

| 产品            | SKU    | 计量单位   | 价格    |
| ------------- | ------ | ------ | ----- |
| Codespaces 计算 | 2 个内核  | 1 小时   | $0.18 |
|               | 4 个内核  | 1 小时   | $0.36 |
|               | 8 个内核  | 1 小时   | $0.72 |
|               | 16 个内核 | 1 小时   | $1.44 |
|               | 32 个内核 | 1 小时   | $2.88 |
| Codespaces 存储 | 存储器    | 1 GB-月 | $0.07 |

## 关于 {% data variables.product.prodname_codespaces %} 的计费

{% data reusables.codespaces.codespaces-billing %}

您的 {% data variables.product.prodname_codespaces %} 使用将共用帐户的现有计费日期、付款方式和收据。 {% data reusables.dotcom_billing.view-all-subscriptions %}

{% ifversion ghec %}
如果您通过微软企业协议购买 {% data variables.product.prodname_enterprise %} ， 您可以将您的 Azure 订阅ID 连接到您的企业账户，以启用并支付您的 {% data variables.product.prodname_codespaces %} 使用费用。 更多信息请参阅“[将 Azure 订阅连接到您的企业](/billing/managing-billing-for-your-github-account/connecting-an-azure-subscription-to-your-enterprise)”。
{% endif %}

{% data reusables.dotcom_billing.pricing_calculator.pricing_cal_codespaces %}

### {% data variables.product.prodname_codespaces %} 预构建的计费

{% data reusables.codespaces.prebuilds-beta-note %}

{% data reusables.codespaces.billing-for-prebuilds %}

## 设置支出限制

{% data reusables.codespaces.codespaces-spending-limit-requirement %}

有关管理和更改帐户支出限制的信息，请参阅“[管理 {% data variables.product.prodname_codespaces %} 的支出限制](/billing/managing-billing-for-github-codespaces/managing-spending-limits-for-codespaces)”。

{% data reusables.codespaces.exporting-changes %}

## 限制机器类型的选择

用户在创建代码空间时选择的计算机类型会影响该代码空间的每分钟费用，如上所示。

组织所有者可以创建策略来限制用户可用的计算机类型。 For more information, see "[Restricting access to machine types](/codespaces/managing-codespaces-for-your-organization/restricting-access-to-machine-types)."

## 如何处理复刻的存储库的计费

{% data variables.product.prodname_codespaces %} 只能在定义了计费所有者的组织中使用。 要对组织收费，用户必须是成员或协作者，否则他们无法创建代码空间。

例如，私有组织中的用户可以复刻该组织内的存储库，随后可以使用向组织计费的代码空间；这是因为组织是父存储库的所有者，父存储库可以删除用户的访问权限、复刻的存储库和代码空间。

## 传输存储库时如何处理计费

使用每小时计费和报告。 因此，当存储库位于您的组织内时，您需要为任何使用付费。 将存储库移出组织时，该存储库中的所有代码空间都将作为传输过程的一部分被删除。

## 移除用户后会发生什么情况

如果从组织或存储库中移除用户，则会自动删除其代码空间。 

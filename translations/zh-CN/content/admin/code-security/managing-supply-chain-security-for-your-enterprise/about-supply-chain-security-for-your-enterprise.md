---
title: About supply chain security for your enterprise
intro: You can enable features that help your developers understand and update the dependencies their code relies on.
shortTitle: About supply chain security
permissions: ''
versions:
  ghes: '*'
  ghae: issue-4864
type: how_to
topics:
  - Enterprise
  - Security
  - Dependency graph
---

You can allow users to identify their projects' dependencies by enabling the dependency graph for {% data variables.product.product_location %}. For more information, see "[Enabling the dependency graph for your enterprise](/admin/code-security/managing-supply-chain-security-for-your-enterprise/enabling-the-dependency-graph-for-your-enterprise)."

You can also allow users on {% data variables.product.product_location %} to find and fix vulnerabilities in their code dependencies by enabling {% data variables.product.prodname_dependabot_alerts %}{% ifversion ghes > 3.2 %} and {% data variables.product.prodname_dependabot_updates %}{% endif %}. For more information, see "[Enabling {% data variables.product.prodname_dependabot %} for your enterprise](/admin/configuration/configuring-github-connect/enabling-dependabot-for-your-enterprise)."

After you enable {% data variables.product.prodname_dependabot_alerts %}, you can view vulnerability data from the {% data variables.product.prodname_advisory_database %} on {% data variables.product.product_location %} and manually sync the data. For more information, see "[Viewing the vulnerability data for your enterprise](/admin/code-security/managing-supply-chain-security-for-your-enterprise/viewing-the-vulnerability-data-for-your-enterprise)."

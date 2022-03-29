---
title: Generating a Health Check for your enterprise
intro: 'You can gain insight into the general health and Git and API requests of {% data variables.product.product_location %} by generating a Health Check.'
versions:
  ghes: '*'
type: how_to
topics:
  - Enterprise
  - Fundamentals
  - Infrastructure
  - Monitoring
  - Performance
product: '{% data reusables.gated-features.generated-health-checks %}'
---

{% note %}

**Note:** Generating a Health Check is currently in beta for {% data variables.product.prodname_ghe_server %} and subject to change.

{% endnote %}

## About generated Health Checks

You can create a support bundle for {% data variables.product.product_location %} that contains a lot of data, such as diagnostics and log files. To help analyze and interpret this data, you can generate a Health Check. For more information about support bundles, see "[Providing data to {% data variables.contact.github_support %}](/support/contacting-github-support/providing-data-to-github-support#creating-and-sharing-support-bundles)."

A Health Check provides the following information about {% data variables.product.product_location %}.
- Insights into the general health of {% data variables.product.product_location %}, such as upgrade status, storage, and license seat consumption
- A security section, which focuses on subdomain isolation and user authentication
- Analysis of Git requests, with details about the busiest repositories and Git users
- Analysis of API requests, including the busiest times, most frequently requested endpoints, and most active callers

## Generating a Health Check

Before you can generate a Health Check, you must create a support bundle. Para obtener más información, consulta "[Proporcionar datos a {% data variables.contact.github_support %}](/support/contacting-github-support/providing-data-to-github-support#creating-and-sharing-support-bundles)".

1. Navigate to the [{% data variables.contact.support_portal %}](https://support.github.com/).
2. In the upper-right corner of the page, click **Premium**.

   ![Screenshot of the "Premium" link in the GitHub Support Portal header.](/assets/images/enterprise/support/support-portal-header-premium.png)

3. To the right of **Health Checks**, click **Request Health Check**.

   ![Screenshot of the "Request Health Check" button.](/assets/images/enterprise/support/support-portal-request-health-check.png)

4. Under "Select an enterprise account", select the dropdown menu and click an enterprise account.

   ![Screenshot of the "enterprise account" dropdown menu.](/assets/images/enterprise/support/health-check-dialog-ea.png)

5. Under "Upload a support bundle", click **Chose File** and choose a file to upload. Then, click **Request Health Check**.

   ![Screenshot of the "Choose file" and "Request Health Check" buttons.](/assets/images/enterprise/support/health-check-dialog-choose-file.png)


After you request a Health Check, a job is scheduled to generate the Health Check. After several hours to one day, the generated Health Check will appear in the "Health Checks" section of the {% data variables.contact.support_portal %}.

![Screenshot of the Health Checks section of the {% data variables.contact.support_portal %}.](/assets/images/enterprise/support/support-portal-health-checks-section.png)

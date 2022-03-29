---
title: 修改 GitHub 应用程序
intro: '{% data reusables.shortdesc.modifying_github_apps %}'
redirect_from:
  - /apps/building-integrations/managing-github-apps/modifying-a-github-app
  - /apps/managing-github-apps/modifying-a-github-app
  - /developers/apps/modifying-a-github-app
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - GitHub Apps
---

{% data reusables.user-settings.access_settings %}
{% data reusables.user-settings.developer_settings %}
{% data reusables.user-settings.github_apps %}
{% data reusables.user-settings.modify_github_app %}
5. 在“Basic information（基本信息）”中，修改您要更改的 GitHub 应用程序信息。 ![Basic information section for your GitHub App](/assets/images/github-apps/github_apps_basic_information.png){% if device-flow-is-opt-in %}
1. 如果您的 GitHub 应用程序将使用设备流来识别和授权用户，请单击 **Enable device flow（启用设备流）**。 有关设备流的更多信息，请参阅“[授权 OAuth 应用程序](/developers/apps/building-oauth-apps/authorizing-oauth-apps#device-flow)”。 ![Screenshot showing field for enabling device flow](/assets/images/oauth-apps/enable-device-flow.png){% endif %}
6. 单击 **Save changes（保存更改）**。 ![保存 GitHub 应用程序更改的按钮](/assets/images/github-apps/github_apps_save_changes.png)

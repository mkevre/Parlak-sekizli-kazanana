---
title: Organization の OAuth App アクセス制限の無効化
intro: 'Organizationのオーナーは、Organizationのリソースへのアクセスを持つ{% data variables.product.prodname_oauth_apps %}に対する制限を無効化できます。'
redirect_from:
  - /articles/disabling-third-party-application-restrictions-for-your-organization
  - /articles/disabling-oauth-app-access-restrictions-for-your-organization
  - /github/setting-up-and-managing-organizations-and-teams/disabling-oauth-app-access-restrictions-for-your-organization
versions:
  fpt: '*'
  ghec: '*'
topics:
  - Organizations
  - Teams
shortTitle: OAuth Appの無効化
---

{% danger %}

**警告**: Organization で {% data variables.product.prodname_oauth_app %} のアクセス制限を無効化すると、Organization のメンバーであれば誰でも、個人アカウント設定でアプリケーションの使用を承認していれば、自動的に {% data variables.product.prodname_oauth_app %} から Organization のプライベートリソースへのアクセスが認証されます。

{% enddanger %}

{% data reusables.profile.access_org %}
{% data reusables.profile.org_settings %}
{% data reusables.organizations.oauth_app_access %}
5. [**Remove restrictions**] をクリックします。 ![[Remove restrictions] ボタン](/assets/images/help/settings/settings-third-party-remove-restrictions.png)
6. サードパーティアプリケーション制限の無効化に関する情報を確認したら、[**Yes, remove application restrictions**] (はい、アプリケーション制限を削除します) をクリックします。 ![[Remove confirmation] ボタン](/assets/images/help/settings/settings-third-party-confirm-disable.png)

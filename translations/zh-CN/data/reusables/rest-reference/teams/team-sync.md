## 团队同步

团队同步 API 允许您管理 {% data variables.product.product_name %} 团队与外部身份提供程序 (IdP) 组之间的连接。 要使用此 API，经过身份验证的用户必须是团队维护员或与团队关联的组织的所有者。 用于身份验证的令牌还需要获得授权才能与 IdP (SSO) 提供程序一起使用。 更多信息请参阅“<a href="/github/authenticating-to-github/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on" class="dotcom-only">授权个人访问令牌用于 SAML 单点登录组织</a>”。

您可以通过 IdP 通过团队同步管理 GitHub 团队成员。 必须启用团队同步才能使用团队同步 API。 更多信息请参阅“<a href="/organizations/managing-saml-single-sign-on-for-your-organization/managing-team-synchronization-for-your-organization" class="dotcom-only">在身份提供程序与 GitHub 之间同步团队</a>”。

{% note %}

**注意：** 团队同步 API 不能与 {% data variables.product.prodname_emus %} 一起使用。 要了解有关管理 {% data variables.product.prodname_emu_org %} 的更多信息，请参阅“[外部组 API](/enterprise-cloud@latest/rest/reference/teams#external-groups)”。

{% endnote %}
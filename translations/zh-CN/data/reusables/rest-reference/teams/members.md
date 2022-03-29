## 成员

此 API 仅适用于团队组织中经过身份验证的成员。 OAuth 访问令牌需要 `read:org` [scope](/apps/building-oauth-apps/understanding-scopes-for-oauth-apps/)。

{% ifversion fpt or ghes or ghec %}
{% note %}

**注：**当您为具有组织身份提供程序 (IdP) 的团队设置了团队同步时，如果尝试使用 API 更改团队的成员身份，则会看到错误。 如果您有权访问 IdP 中的组成员身份，可以通过身份提供程序管理 GitHub 团队成员身份，该提供程序会自动添加和删除组织的成员。 更多信息请参阅“<a href="/organizations/managing-saml-single-sign-on-for-your-organization/managing-team-synchronization-for-your-organization" class="dotcom-only">在身份提供程序与 GitHub 之间同步团队</a>”。

{% endnote %}

{% endif %}
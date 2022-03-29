---
title: Testing dev container configuration changes on a prebuild-enabled branch
shortTitle: Test dev container changes
allowTitleToDifferFromFilename: true
intro: When you change the dev container configuration for a branch that's enabled for prebuilds you should test your changes in a codespace.
versions:
  fpt: '*'
  ghec: '*'
type: how_to
topics:
  - Codespaces
  - Set up
product: '{% data reusables.gated-features.codespaces %}'
permissions: People with write permissions to a repository can create or edit the dev container configuration for a branch.
---

{% data reusables.codespaces.prebuilds-beta-note %}

Any changes you make to the dev container configuration for a prebuild-enabled branch will result in an update to the codespace configuration and the associated prebuild template. It’s therefore important to test such changes in a codespace from a test branch before committing your changes to a branch of your repository that's actively used. This will ensure you’re not introducing breaking changes for your team.

更多信息请参阅“[开发容器简介](/codespaces/setting-up-your-project-for-codespaces/configuring-codespaces-for-your-project)”。

## Testing changes to the dev container configuration

1. Create a codespace from the prebuild-enabled branch whose dev container you want to change. For more information, see "[Creating a codespace ](/codespaces/developing-in-codespaces/creating-a-codespace#creating-a-codespace)."
1. In the codespace, check out a test branch. For more information, see "[Using source control in your codespace](/codespaces/developing-in-codespaces/using-source-control-in-your-codespace#creating-or-switching-branches)."
1. Make the required changes to the dev container configuration.
1. Apply the changes by rebuilding the container. 更多信息请参阅“[开发容器简介](/codespaces/setting-up-your-project-for-codespaces/configuring-codespaces-for-your-project#applying-changes-to-your-configuration)”。
1. After everything looks good, we also recommend creating a new codespace from your test branch to ensure everything is working. You can then commit your changes to your repository's default branch, or an active feature branch, triggering an update of the prebuild template for that branch.

   {% note %}

   **Note**: Creating this codespace will take longer than usual because it will not be created from a prebuild.

   {% endnote %}

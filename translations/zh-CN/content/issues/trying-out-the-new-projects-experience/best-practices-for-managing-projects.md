---
title: 管理项目的最佳实践（测试版）
intro: '学习在 {% data variables.product.company_short %} 中管理项目的技巧。'
allowTitleToDifferFromFilename: true
miniTocMaxHeadingLevel: 3
versions:
  fpt: '*'
  ghec: '*'
type: overview
topics:
  - Projects
  - Issues
  - Project management
---

{% data reusables.projects.projects-beta %}

您可以使用项目来管理您在 {% data variables.product.company_short %} 上的工作，其中包括您的议题和拉取请求。 阅读提示以便高效和有效地管理您的项目。 有关项目的更多信息，请参阅“[关于项目](/issues/trying-out-the-new-projects-experience/about-projects)”。

## 将大议题分成较小的议题

将大议题分解为较小的议题，使工作更加易于管理，并使团队成员能够并行工作。 它还会导致较小的拉取请求，这些请求更容易审查。

要跟踪较小的议题如何融入更大的目标，请使用任务列表、里程碑或标签。 更多信息请参阅“[关于任务列表](/issues/tracking-your-work-with-issues/creating-issues/about-task-lists)”、“[关于里程碑](/issues/using-labels-and-milestones-to-track-work/about-milestones)”和“[管理标签](/issues/using-labels-and-milestones-to-track-work/managing-labels)”。

## 沟通

议题和拉取请求包括内置功能，让您轻松地与协作者沟通。 使用@提及提醒个人或整个团队注意评论。 指派议题协作者负责沟通。 链接到相关的议题或拉取请求以沟通它们是如何连接的。

## 使用描述和 README

使用您的项目描述和 README 来分享有关该项目的信息。

例如：

- 解释项目的目的。
- 描述项目视图及其使用方法。
- 包括相关链接和要联系的人员以获取更多信息。

项目 README 支持 Markdown，它允许您使用图像和高级格式，如链接、列表和标题。

更多信息请参阅“[创建项目（测试版）](/issues/trying-out-the-new-projects-experience/creating-a-project#updating-your-project-description-and-readme)”。

## 使用视图

使用项目视图从不同角度查看您的项目。

例如：

- 按状态过滤以查看所有未启动的项
- 按自定义优先级字段分组以监控高优先级项目的数量
- 按自定义日期字段排序，以查看具有最早目标运输日期的物品

更多信息请参阅“[自定义项目视图](/issues/trying-out-the-new-projects-experience/customizing-your-project-views)”。

## 拥有单一真相来源

为了防止信息不同步，请保持单一真相来源。 例如，在一个位置跟踪目标运输日期，而不是分布于多个字段。 然后，如果目标运输日期发生变化，您只需要在一个位置更新日期。

{% data variables.product.company_short %} 项目自动更新 {% data variables.product.company_short %} 数据，例如受理人、里程碑和标签。 当其中一个字段在议题或拉取请求中发生变化时，更改会自动反映在您的项目中。

## 使用自动化

您可以自动执行任务，以减少您在繁琐工作上花费的时间，将更多的时间用于项目本身。 需要手动操作的越少，项目就越有可能保持最新状态。

项目（测试版）提供内置工作流程。 例如，当议题关闭时，您可以自动将状态设置为“完成”。

此外，{% data variables.product.prodname_actions %} 和 GraphQL API 还可让您实现例行项目管理任务自动化。 例如，要跟踪等待审查的拉取请求，您可以创建一个工作流程，将拉取请求添加到项目并将状态设置为“需要审核”；当拉取请求标记为“准备审核”时，可以自动触发此过程。

- 有关示例工作流程，请参阅“[自动化项目](/issues/trying-out-the-new-projects-experience/automating-projects)”。
- 有关 API 的更多信息，请参阅“[使用 API 管理项目](/issues/trying-out-the-new-projects-experience/using-the-api-to-manage-projects)”。
- 有关 {% data variables.product.prodname_actions %} 的更多信息，请参阅[“{% data variables.product.prodname_actions %}](/actions)”。

## 使用不同的字段类型

利用各种字段类型来满足您的需求。

使用迭代字段可以安排工作或创建日程表。 您可以按迭代进行分组以查看项目在迭代之间是否平衡，也可以进行筛选以专注于单个迭代。 迭代字段还允许您查看在过去迭代中完成的工作，这有助于快速规划和反映团队的成就。 迭代字段还支持休息，以显示您和您的团队何时从迭代中抽出时间。 更多信息请参阅“[管理项目中的迭代](/issues/trying-out-the-new-projects-experience/managing-iterations)”。

使用单选字段可以根据预设的值列表跟踪有关任务的信息。 例如，跟踪优先级或项目阶段。 由于这些值是从预设列表中选择的，因此您可以轻松地对值进行分组或筛选，以将焦点放在具有特定值的项目上。

有关不同字段类型的详细信息，请参阅“[创建项目（测试版）](/issues/trying-out-the-new-projects-experience/creating-a-project#adding-custom-fields)。

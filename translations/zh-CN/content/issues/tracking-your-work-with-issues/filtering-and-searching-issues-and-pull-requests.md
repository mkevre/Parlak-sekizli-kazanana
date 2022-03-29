---
title: 筛选和搜索议题以及拉取请求
intro: '要在 {% data variables.product.product_name %} 上查找有关仓库的详细信息，您可以过滤、排序和搜索与仓库相关的议题和拉取请求。'
redirect_from:
  - /github/managing-your-work-on-github/finding-information-in-a-repository/filtering-issues-and-pull-requests-by-assignees
  - /articles/filtering-issues-and-pull-requests-by-assignees
  - /github/managing-your-work-on-github/filtering-issues-and-pull-requests-by-assignees
  - /github/managing-your-work-on-github/finding-information-in-a-repository/filtering-issues-and-pull-requests-by-labels
  - /articles/filtering-issues-and-pull-requests-by-labels
  - /github/managing-your-work-on-github/filtering-issues-and-pull-requests-by-labels
  - /github/managing-your-work-on-github/finding-information-in-a-repository/filtering-issues-and-pull-requests
  - /articles/filtering-issues-and-pull-requests
  - /github/managing-your-work-on-github/filtering-issues-and-pull-requests
  - /github/managing-your-work-on-github/finding-information-in-a-repository/filtering-pull-requests-by-review-status
  - /articles/filtering-pull-requests-by-review-status
  - /github/managing-your-work-on-github/filtering-pull-requests-by-review-status
  - /github/managing-your-work-on-github/finding-information-in-a-repository
  - /articles/finding-information-in-a-repository
  - /github/managing-your-work-on-github/finding-information-in-a-repository/sharing-filters
  - /articles/sharing-filters
  - /github/managing-your-work-on-github/sharing-filters
  - /github/managing-your-work-on-github/finding-information-in-a-repository/using-search-to-filter-issues-and-pull-requests
  - /articles/using-search-to-filter-issues-and-pull-requests
  - /github/managing-your-work-on-github/using-search-to-filter-issues-and-pull-requests
  - /github/managing-your-work-on-github/finding-information-in-a-repository/sorting-issues-and-pull-requests
  - /articles/sorting-issues-and-pull-requests
  - /github/managing-your-work-on-github/sorting-issues-and-pull-requests
  - /github/administering-a-repository/finding-information-in-a-repository
  - /github/administering-a-repository/finding-information-in-a-repository/filtering-issues-and-pull-requests
  - /github/administering-a-repository/finding-information-in-a-repository/filtering-issues-and-pull-requests-by-assignees
  - /github/administering-a-repository/finding-information-in-a-repository/filtering-issues-and-pull-requests-by-labels
  - /github/administering-a-repository/finding-information-in-a-repository/filtering-pull-requests-by-review-status
  - /github/administering-a-repository/finding-information-in-a-repository/sorting-issues-and-pull-requests
  - /github/administering-a-repository/finding-information-in-a-repository/using-search-to-filter-issues-and-pull-requests
  - /github/administering-a-repository/finding-information-in-a-repository/sharing-filters
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Issues
  - Pull requests
shortTitle: 筛选和搜索
type: how_to
---

{% data reusables.cli.filter-issues-and-pull-requests-tip %}

## 过滤议题和拉取请求

议题和拉取请求带有一组默认过滤器，您可以应用这些过滤器来组织列表。

{% data reusables.search.requested_reviews_search %}

您可以过滤议题和拉取请求以查找：
- 所有打开的议题和拉取请求
- 您已创建的议题和拉取请求
- 分配给您的议题和拉取请求
- [**@提及**](/articles/basic-writing-and-formatting-syntax/#mentioning-people-and-teams)您的议题和拉取请求

{% data reusables.cli.filter-issues-and-pull-requests-tip %}

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-issue-pr %}
3. 单击 **Filters（过滤器）**以选择您感兴趣的过滤器类型。 ![使用过滤器下拉菜单](/assets/images/help/issues/issues_filter_dropdown.png)

## 按受理人过滤议题和拉取请求

将[议题或拉取请求分配给某人](/articles/assigning-issues-and-pull-requests-to-other-github-users)后，您可以根据处理这些项目的人来查找项。

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-issue-pr %}
3. 在右上角，选择 Assignee（受理人）下拉菜单。
4. Assignee（受理人）下拉菜单将列出对仓库有写入权限的每个人。 单击要查看项目的受理人用户名，或单击 **Assigned to nobody（未分配给任何人）**以查看未分配的议题。 ![使用受理人下拉菜单选项卡](/assets/images/help/issues/issues_assignee_dropdown.png)

{% tip %}

要清除过滤器选择，请单击 **Clear current search query, filters, and sorts（清除当前搜索查询、过滤和排序）**。

{% endtip %}

## 按标签过滤议题和拉取请求

将[标签应用于议题或拉取请求](/articles/applying-labels-to-issues-and-pull-requests)后，您可以根据项目的标签查找项。

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-issue-pr %}
{% data reusables.project-management.labels %}
4. 在标签列表中，单击标签以查看应用了该标签的议题和拉取请求。 ![仓库标签列表](/assets/images/help/issues/labels-page.png)

{% tip %}

**提示：**要清除过滤器选择，请单击 **Clear current search query, filters, and sorts（清除当前搜索查询、过滤和排序）**。

{% endtip %}

## 按审查状态过滤拉取请求

您可以使用过滤器按审查状态列出拉取请求，查找您已审查的拉取请求或其他人要求您审查的拉取请求。

您可以过滤仓库的拉取请求列表以查找：
- 尚未[审查](/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews)的拉取请求
- [需要审查](/github/administering-a-repository/about-protected-branches#require-pull-request-reviews-before-merging)后才能合并的拉取请求
- 审查者已批准的拉取请求
- 审查者要求更改的拉取请求
- 您已审核的拉取请求{% ifversion fpt or ghae-issue-5181 or ghes > 3.2 or ghec %}
- 有人要求您直接审核的拉取请求{% endif %}
- [有人要求您或您所属团队进行审查](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review)的拉取请求

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-pr %}
3. 在右上角，选择 Reviews（审查）下拉菜单。 ![拉取请求列表上方过滤器菜单中的审查下拉菜单](/assets/images/help/pull_requests/reviews-filter-dropdown.png)
4. 选择一个过滤器以查找具有该过滤器状态的所有拉取请求。 ![审查下拉菜单中的过滤器列表](/assets/images/help/pull_requests/pr-review-filters.png)

## 使用搜索过滤议题和拉取请求

您可以使用高级筛选器来搜索符合特定条件的议题和拉取请求。

### 搜索议题和拉取请求

{% webui %}

议题和拉取请求搜索栏可以定义您自己的自定义过滤器并按各种标准进行排序。 您可以在每个仓库的 **Issues（议题）**和 **Pull requests（拉取请求）**选项卡上以及[议题和拉取请求仪表板](/articles/viewing-all-of-your-issues-and-pull-requests)上找到搜索栏。

![议题和拉取请求搜索栏](/assets/images/help/issues/issues_search_bar.png)

{% tip %}

**提示：**{% data reusables.search.search_issues_and_pull_requests_shortcut %}

{% endtip %}

{% endwebui %}

{% cli %}

{% data reusables.cli.cli-learn-more %}

您可以使用 {% data variables.product.prodname_cli %} 来搜索议题或拉取请求。 使用 `gh issue list` 或 `gh pr list` 子命令以及 `--search` 参数和搜索查询。

例如，您可以按创建日期的顺序列出所有没有受理人且有标签 `help wanted` 或 `bug` 的议题。

```shell
gh issue list --search 'no:assignee label:"help wanted",bug sort:created-asc'
```

您还可以列出所有提及 `octo-org/octo-team` 团队的拉取请求。

```shell
gh pr list --search "team:octo-org/octo-team"
```

{% endcli %}

### 关于搜索词

使用议题和拉取请求搜索词，您可以：

- 按作者过滤议题和拉取请求：`state:open type:issue author:octocat`
- 过滤涉及但不一定[**@提及**](/articles/basic-writing-and-formatting-syntax/#mentioning-people-and-teams)的特定人员的议题和拉取请求：`state:open type:issue involves:octocat`
- 按受理人过滤议题和拉取请求：`state:open type:issue assignee:octocat`
- 按标签过滤议题和拉取请求：`state:open type:issue label:"bug"`
- 使用 `-` before the term: `state:open type:issue -author:octocat` 过滤搜索词。

{% ifversion fpt or ghes > 3.2 or ghae or ghec %}
{% tip %}

**提示：** 您可以使用逻辑 OR 或使用逻辑 AND 按标签筛选问题和拉取请求。
- 要使用逻辑 OR 筛选议题，请使用逗号语法：`label:"bug","wip"`。
- 要使用逻辑 AND 筛选问题，请使用单独的标签筛选器：`label:"bug" label:"wip"`。

{% endtip %}
{% endif %}

{% ifversion fpt or ghes or ghae or ghec %}
对于议题，您还可以使用搜索来：

- 通过关闭引用过滤链接到拉取请求的议题：`linked:pr`
{% endif %}

对于拉取请求，您还可以使用搜索来：
- 过滤[草稿](/articles/about-pull-requests#draft-pull-requests)拉取请求：`is:draft`
- 过滤尚未[审查](/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews)的拉取请求：`state:open type:pr review:none`
- 过滤[需要审查](/github/administering-a-repository/about-protected-branches#require-pull-request-reviews-before-merging)然后才能合并的拉取请求：`state:open type:pr review:required`
- 过滤审查者已批准的拉取请求：`state:open type:pr review:approved`
- 过滤审查者要求更改的拉取请求：`state:open type:pr review:changes_requested`
- 按[审查者](/articles/about-pull-request-reviews/)过滤拉取请求：`state:open type:pr reviewed-by:octocat`
- 按[请求审查](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review)的特定用户过滤拉取请求：`state:open type:pr review-requested:octocat`{% ifversion fpt or ghae-issue-5181 or ghes > 3.2 or ghec %}
- 过滤有人直接要求您审核的拉取请求：`state:open type:pr user-review-requested:@me`{% endif %}
- 按申请审查的团队过滤拉取请求：`state:open type:pr team-review-requested:github/atom`{% ifversion fpt or ghes or ghae or ghec %}
- 过滤链接到拉取请求可能关闭的议题的拉取请求：`linked:issue`{% endif %}

## 排序议题和拉取请求

可以排序过滤器以在特定时间段内提供更好的信息。

您可以按以下各项排序任何过滤的视图：

* 最新创建的议题或拉取请求
* 最早创建的议题或拉取请求
* 评论最多的议题或拉取请求
* 评论最少的议题或拉取请求
* 最新更新的议题或拉取请求
* 最早更新的议题或拉取请求
* 反应最多的议题或拉取请求

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-issue-pr %}
1. 在右上角，选择 Sort（排序）下拉菜单。 ![使用排序下拉菜单选项卡](/assets/images/help/issues/issues_sort_dropdown.png)

要清除您的排序选择，请单击 **Sort（排序）<**>**Newest（最新）**。


## 共享过滤器

当您过滤或排序议题和拉取请求时，浏览器的 URL 自动更新以匹配新视图。

您可以将议题生成的 URL 发送给任何用户，这些用户将能够看到与您所见相同的过滤视图。

例如，如果您过滤分配给 Hubot 的议题，然后对最早的开放议题进行排序，您的 URL 将更新为类似如下内容：

```
/issues?q=state:open+type:issue+assignee:hubot+sort:created-asc
```

## 延伸阅读

- "[搜索议题和拉取请求](/articles/searching-issues)"

## 标星

仓库标星是允许用户为仓库添加书签的功能。 显示在仓库旁边的星标表示大致的兴趣程度。 星标对通知或活动馈送没有影响。

### 标星与 关注

2012 年 8 月，我们[更改了 {% data variables.product.prodname_dotcom %} 上的关注方式](https://github.com/blog/1204-notifications-stars)。 许多 API 客户端应用程序可能在使用原始的“关注者”端点来访问此数据。 现在，您可以开始使用“星标”端点了（如下所述）。 更多信息请参阅[关注者 API 更改帖子](https://developer.github.com/changes/2012-09-05-watcher-api/)和“[仓库关注 API](/rest/reference/activity#watching)”。

### 标星的自定义媒体类型

标星 REST API 有一个支持的自定义媒体类型。 使用此自定义媒体类型时，您将收到带有 `starred_at` 时间戳属性的响应，该属性指示星标创建的时间。 该响应还有第二个属性，该属性包括在不使用自定义媒体类型时返回的资源。 包含资源的属性为 `user` 或 `repo`。

    application/vnd.github.v3.star+json

有关媒体类型的更多信息，请参阅“[自定义媒体类型](/rest/overview/media-types)”。
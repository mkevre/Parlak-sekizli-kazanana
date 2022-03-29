## 内容

此 API 端点允许您在仓库中创建、修改和删除 Base64 编码的内容。 要请求原始格式或渲染的 HTML（如果支持），请对仓库内容使用自定义媒体类型。

### 仓库内容的自定义媒体类型

[自述文件](/rest/reference/repos#get-a-repository-readme)、[文件](/rest/reference/repos#get-repository-content)和[符号链接](/rest/reference/repos#get-repository-content)支持以下自定义媒体类型：

    application/vnd.github.VERSION.raw
    application/vnd.github.VERSION.html

使用 `.raw` 媒体类型检索文件内容。

对于 Markdown 或 AsciiDoc 等标记文件，您可以使用 `.html` 媒体类型检索渲染的 HTML。 使用我们的开源[标记库](https://github.com/github/markup)将标记语言渲染为 HTML。

[所有对象](/rest/reference/repos#get-repository-content)都支持以下自定义媒体类型：

    application/vnd.github.VERSION.object

使用 `object` 媒体类型参数以一致的对象格式检索内容，而不考虑内容类型。 例如，响应将是包含对象数组的 `entries` 属性的对象，而不是目录的对象数组。

您可以在[此处](/rest/overview/media-types)阅读有关 API 中媒体类型使用情况的更多信息。
# HTML

**`<h1> - <h6>`:HTML区域标题元素**

**HTML `<h1>`–`<h6>` 标题 (Heading) 元素**呈现了六个不同的级别的标题，`<h1>` 级别最高，而 `<h6>` 级别最低。

```html
<h1>这是h1元素，级别最大。</h1>
<h2>这是h2元素，级别次之。</h2>
<h3>这是h3元素，排行第三。</h3>
<h4>这是h4元素，排行第四。</h4>
<h5>这是h5元素，排行第五。</h5>
<h6>这是h6元素，排行第六。</h6>
```



![image-20240828191754755](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240828191754755.png)

------

**`<p></p>`元素，段落元素**

<p> HTML 元素表示文本的一个段落。在视觉媒体中，段落通常表现为用空行和/或首行缩进与相邻段落分隔的文本块，但 HTML 段落可以是相关内容的任何结构分组，如图像或表格字段。

------

**注释**

HTML文档中通过`<!---->`表示注释

![image-20240828192609987](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240828192609987.png)

------

**`<main></main>`**

HTML **`<main>` 元素**呈现了文档的 `<body>` 或应用的主体部分。主体部分由与文档直接相关，或者扩展于文档的中心主题、应用的主要功能部分的内容组成。

在文档中，`<main>` 元素的内容应当是独一无二的。任何同时存在于任意一系列文档中的相同、重复内容，比如侧边栏、导航栏链接、版权信息、网站 Logo，搜索框（除非搜索框为文档的主要功能），都不应当被包含在其内。

------

**`<img>`:图像嵌入元素**

`<img>` HTML 元素将一张图像嵌入文档。

- `src` 属性是**必须的**，它包含了你想嵌入的图片的路径。

- `alt` 属性包含一条对图像的文本描述，这不是强制性的，但对无障碍而言，它**难以置信地有用**——屏幕阅读器会将这些描述读给需要使用阅读器的使用者听，让他们知道图像的含义。

Web 最常用的图像格式是：

- [APNG（动态可移植网络图形）](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types#apng_animated_portable_network_graphics)——无损动画序列的不错选择（GIF 性能较差）。
- [AVIF（AV1 图像文件格式）](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types#avif_image)——静态图像或动画的不错选择，其性能较好。
- [GIF（图像互换格式）](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types#gif_graphics_interchange_format)——*简单*图像和动画的不错选择。
- [JPEG（联合图像专家组）](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types#jpeg_joint_photographic_experts_group_image)——有损压缩静态图像的不错选择（目前最流行的格式）。
- [PNG（便携式网络图形）](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types#png_portable_network_graphics)——对于无损压缩静态图像而言是不错的选择（质量略好于 JPEG）。
- [SVG（可缩放矢量图形）](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types#svg_scalable_vector_graphics)——矢量图像格式。用于必须以不同尺寸准确描绘的图像。
- [WebP（网络图片格式）](https://developer.mozilla.org/zh-CN/docs/Web/Media/Formats/Image_types#webp_image)——图像和动画的绝佳选择。

属性：

[`loading`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#loading)

指示浏览器应当如何加载该图像。允许的值：

- [`eager`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#eager)：立即加载图像，不管它是否在可视视口（visible viewport）之外（默认值）。

- [`lazy`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#lazy)：延迟加载图像，直到它和视口接近到一个计算得到的距离（由浏览器定义）。目的是在需要图像之前，避免加载图像所需要的网络和存储带宽。这通常会提高大多数典型用场景中内容的性能。

------

**`<a> </a>`:锚元素**

[HTML](https://developer.mozilla.org/zh-CN/docs/Web/HTML) **`<a>`** 元素（或称*锚*元素）可以通过[它的 `href` 属性](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a#href)创建通向其他网页、文件、电子邮件地址、同一页面内的位置或任何其他 URL 的超链接。

属性：

- `href`:超链接所指向的 URL。链接不限于基于 HTTP 的 URL——它们可以使用浏览器支持的任何 URL 协议：
  - 使用文档片段链接到页面的某一段
  - 使用[文本片段](https://developer.mozilla.org/zh-CN/docs/Web/URI/Fragment/Text_fragments)链接到某一段文字
  - 使用媒体片段链接到某个媒体文件
  - 使用 `tel:` URL 链接到一个电话号码
  - 使用 `mailto:` URL 链接到一个邮箱地址
  - 如果 web 浏览器不能支持其他 URL 协议，网站可以使用 [`registerProtocolHandler()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Navigator/registerProtocolHandler)
- `download`:导致浏览器将链接的 URL 视为下载资源。可以使用或不使用 `filename` 值：
  - 如果没有指定值，浏览器会从多个来源决定文件名和扩展名：
    - [`Content-Disposition`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Disposition) HTTP 标头。
    - URL [路径](https://developer.mozilla.org/zh-CN/docs/Web/API/URL/pathname)的最后一段。
    - [媒体类型](https://developer.mozilla.org/zh-CN/docs/Glossary/MIME_type)。来自 [`Content-Type`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Type) 标头，[`data:` URL](https://developer.mozilla.org/zh-CN/docs/Web/URI/Schemes/data) 的开头，或 [`blob:` URL](https://developer.mozilla.org/zh-CN/docs/Web/API/URL/createObjectURL_static) 的 [`Blob.type`](https://developer.mozilla.org/zh-CN/docs/Web/API/Blob/type)。
  - `filename`：决定文件名的值。`/` 和 `\` 被转化为下划线（`_`）。文件系统可能会阻止文件名中其他的字符，因此浏览器会在必要时适当调整文件名。

- `target`:该属性指定在何处显示链接的 URL，作为*浏览上下文*的名称（标签、窗口或 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe)）。以下关键词对加载 URL 的位置有特殊含义：

  - `_self`：当前页面加载。（默认）
  - `_blank`：通常在新标签页打开，但用户可以通过配置选择在新窗口打开。
  - `_parent`：当前浏览环境的父级浏览上下文。如果没有父级框架，行为与 `_self` 相同。
  - `_top`：最顶级的浏览上下文（当前浏览上下文中最“高”的祖先）。如果没有祖先，行为与 `_self` 相同。

  > [!CAUTION]
  >
  > **备注：**在 `<a>` 元素上使用 `target="_blank"` 隐式提供了与使用 [`rel="noopener"`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel/noopener) 相同的 `rel` 行为，即不会设置 `window.opener`。

------


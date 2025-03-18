# 4 个关键的CSS 属性，帮助你快速入门CSS

**1、Display**

指定元素的显示行为。

它需要许多不同的值，但坦率地说，在大多数情况下你将只使用 4 个值。

- block：CSS 中的块级元素，它占用尽可能多的空间，但它们不能放置在同一水平线上。开发人员主要使用块级元素来简化布局过程，因为他们能够改变他们选择的元素的宽度和高度。
- inline：这是默认值，如果没有指定任何其他显示值，元素可以并排放置在与内联元素相同的水平线上。像<strong>、<em>、<a> 等 HTML 标签就是内联元素的好例子，我们无法控制它们的宽度和高度。
- inline-block：你可以将其视为块元素和内联元素的组合值，你可以在其中设置它们的宽度和高度，并且元素可以毫无问题地出现在同一水平线上。
- none：使用此值可以从网页中隐藏元素。您可以在下拉菜单中使用它，当你将鼠标悬停在导航菜单上时会显示附加信息。

![图片](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcYrCZQrWpXtiapdrVJaLOjHw9OMy5Wnia72MYFTJrqHXiac7b99YCOY72pwxiaianhMh9SvaxSgeSD3xvw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**2、Float**

float 属性用于定位和格式化内容。

简单来说，float 属性管理HTML内容在父容器一侧边缘的位置。

例如，

![图片](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcYrCZQrWpXtiapdrVJaLOjHwawf3QZ6GSibN60frFVkWD6HNYVdtu8K6UCRHAZwHeNicwZpM7OF1qpdQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

Float 属性接受多个属性，但你将使用其中的 3 个，分别是 right、left 和 none。

**3、Background**

为元素添加背景效果。

它只是指 HTML 元素的背景，大多数时候开发人员在多个背景属性之间感到困惑。但是，如果你对如何在 CSS 中选择背景有一个清晰的解释，那么使用 HTML 元素会容易得多。

你需要了解 4 种主要类型的背景属性：

background-color：应用元素的背景颜色，并采用十六进制或 RGB 值。

background-image：将图像应用为背景，并使用路径 URI 或 URL 来访问图像资源。

background-repeat：你可以使用这些值，如果宽度超过背景大小，则使应用的背景重复自身。

background-position：可以控制背景相对于HTML元素的位置，这里需要两个值，X & Y。X是离左边的偏移值，Y是离顶部的偏移值。

**4、Position**

此属性指定用于元素的定位方法的类型。

如果你想掌握一些布局技巧，这个 CSS 属性是非常重要的，因为大多数时候开发人员会在 CSS 中定位元素，使用正确的定位值可以轻松完成工作。

大多数情况下，你将使用以下 3 个值：

绝对：绝对定位的元素查找本身具有相对、绝对或固定位置的父后代元素。

相对：具有相对位置的元素将相对于其正常位置进行定位。

固定：具有固定位置的元素相对于视口定位，但是，顶部、底部、左侧和右侧属性用于定位元素。

例如;

![图片](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcYrCZQrWpXtiapdrVJaLOjHw8IW11siagIKMGMoM2ZZJlpJeic1m4QmyxGMgU5icgcVHfv0wTIZDnxlpQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

当子元素被定位为absolute时，我们可以通过top、left、bottom值来控制它在整个body元素中的位置。你可以将其称为独立子元素，其中 body 元素是父元素。

但是，当我们为父元素（蓝色容器）提供相对位置时，所有具有绝对位置的元素都将落入新的父元素之下。

你可以观察到，当我们将相对位置值传递给父元素时，子元素的高度现在是相对于父元素的。

![图片](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcYrCZQrWpXtiapdrVJaLOjHwF1DARhwibZRDtiaXhJUMrraXfXEtQsJvDqzrMyCicaf0krKdbGdomzfqA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)
DOCTYPE
DOCTYPE是document type(文档类型)的简写，在web设计中用来说明使用的XHTML或者HTML是什么版本。
HTML5 不基于 SGML，所以不需要引用 DTD。

<!DOCTYPE html>声明必须是 HTML 文档的第一行，位于 <html> 标签之前。

<!DOCTYPE html>
<html>
    <head>
        <title></title>
    </head>
    <body>

    </body>
</html>
Copy to clipboardErrorCopied
在HTML 4.01中，<!DOCTYPE>声明引用DTD，因为HTML 4.01基于SGML。 DTD规定了标记语言的规则，这样浏览器才能正确地呈现内容。

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
Copy to clipboardErrorCopied
其中的DTD叫文档类型定义，里面包含了文档的规则，浏览器就根据定义的DTD来解释你页面的标识，并展现出来。

要建立符合标准的网页，DOCTYPE声明是必不可少的关键组成部分；除非你的XHTML确定了一个正确的DOCTYPE，否则标识和CSS都不会生效。

XHTML 1.0 提供了三种DTD声明可供选择
过渡的Transitional：要求非常宽松的DTD，它允许继续使用HTML4.01的标识(但是要符合xhtml的写法)，完整代码如下：
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
Copy to clipboardErrorCopied
严格的Strict：要求严格的DTD，不能使用任何表现层的标识和属性，例如<br>，完整代码如下：
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
Copy to clipboardErrorCopied
框架的Frameset：专门针对框架页面设计使用的DTD，如果页面中包含有框架，需要采用这种DTD，完整代码如下：
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
Copy to clipboardErrorCopied
每日一题
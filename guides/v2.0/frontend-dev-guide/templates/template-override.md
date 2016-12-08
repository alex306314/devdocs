---
layout: default  
group: fedg
subgroup: C_Templates
title: 模板基础概念
menu_title: 模板基础概念
menu_order: 3
version: 2.0
github_link: frontend-dev-guide/templates/template-override.md
redirect_from: /guides/v1.0/frontend-dev-guide/templates/template-override.html
---

<h2>What's in this topic 此专题讲什么</h2>
This topic discusses the main concepts of how default templates work in the Magento application. 
The following topics are covered:

本专题讨论默认模板如何在Magento程序中工程的主要概念。包含如下专题：

* <a href="#template-layout">How templates are initiated 模板如何初始化</a>
* <a href="#root">Root template 根模板</a>
* <a href="#template-convention">Conventional templates location 常规模块位置</a>
* <a href="#override">Templates overriding 模板覆写</a>
* <a href="#getter">Getting argument values from layout 从布局获取参数值</a>


<h2 id="template-layout">How templates are initiated 模板如何被初始化</h2>

Templates are usually initiated in layout files.
Each layout block has an associated template. 
The template is specified in the `template` attribute of the <block> layout instruction. 
For example, from <code><a href="{{site.mage2000url}}app/code/Magento/Catalog/view/frontend/layout/catalog_category_view.xml" target="_blank">&lt;Magento_Catalog_module_dir&gt;/view/frontend/layout/catalog_category_view.xml</a></code>:

模板通常在布局文件中初始化。每个布局区块有对应的模板。模板是在black布局指定的template属性中指定的。如

<pre>
&lt;block class=&quot;Magento\Catalog\Block\Category\View&quot; name=&quot;category.image&quot; template=&quot;Magento_Catalog::category/image.phtml&quot;/&gt;
</pre>

This means that the `category.image` block is rendered by the `image.phtml` template, which is located in the `category` subdirectory of the `Magento_Catalog` module templates directory.

这意味着 `category.image` 区块是通过 `image.phtml`模板渲染的，它的位置在`Magento_Catalog`模块模板目录的`category`子目录

The templates directory of `Magento_Catalog` is `<Magento_Catalog_module_dir>/view/frontend/templates`.

`Magento_Catalog`模板的目录是`<Magento_Catalog_module_dir>/view/frontend/templates`.

The next section describes where templates can be located in general. 

下一部分描述一般可以在哪定位到模板

<h2 id="template-convention">Conventional templates location 常规模板位置</h2> 

Templates are stored in the following locations:

模板存储在如下位置：

* <span id="module">Module templates模块模板: <code>&lt;module_dir&gt;/view/frontend/templates/&lt;path_to_templates&gt;</code>
* <span id="theme">Theme templates主题模板: <code>&lt;theme_dir&gt;/&lt;Namespace&gt;_&lt;Module&gt;/templates/&lt;path_to_templates&gt;</code>

Here <code>&lt;path_to_templates&gt;</code> might have several levels of directory nesting, or might be empty. Examples:

这里<code>&lt;path_to_templates&gt;</code>或许会有很多层级目录嵌套，也有可能是空的。如

* `<Magento_Catalog_module_dir>/view/frontend/templates/product/widget/new/content/new_grid.phtml`
* `<Magento_Checkout_module_dir>/view/frontend/templates/cart.phtml`

<h2 id="override">Templates overriding 模板覆写</h2>
For template files with the same name, the following is true: 
theme templates override module templates, and those of a <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-inherit.html" target="_blank">child theme</a> override parent theme templates.

对具有相同名称的模板文件，真实情况如下：主题模板覆写模块模板，并且它们的子主题覆写父主题模板

This mechanism is the basis of the template customization concept in Magento application: to change the output defined by a certain default template, you need to override one in your custom theme.

这种机制是Magneto应用程序中自定义模板概念的基础

Overriding templates is described with more details in the <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-inherit.html#theme-inherit-templates" target="_blank">Theme Inheritance article</a>.

覆写模板更多描述在主题继承一文

<h2 id="root">Root template 根模板</h2>

In Magento there's a special template which serves as root template for all storefront pages in the application: `<Magento_Theme_module_dir>/view/base/templates/root.phtml`.

在Magento中这有一个特殊的模型充当所有网店页面根模板：

Unlike other templates, `root.phtml` contains the `doctype` specification and contributes to `<head>` and `<body>` sections of all pages rendered by Magento application. But similar to other templates, `root.phtml` can be overridden in a theme. 

不同于其它模板，`root.phtml`包含有`doctype`规范并贡献于Magneto应用程序提供的所有页面的head和body区域


<h2 id="getter">Getting argument values from layout 从布局获取参数值</h2>

Arguments values set in a layout file can be accessed in templates using the <code>get{ArgumentName}()</code> and <code>has{ArgumentName}()</code> methods. There are more details in the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#getter" target="_blank">Layout instructions article.

布局文件设置的参数值在模板可以使用<code>get{ArgumentName}()</code> and <code>has{ArgumentName}()</code>方法获取。更多详细在布局指令一文

## Related reading

[Set a block's template]({{page.baseurl}}frontend-dev-guide/layouts/xml-manage.html#set_template)

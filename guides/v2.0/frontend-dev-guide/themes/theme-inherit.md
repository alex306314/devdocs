---
layout: default
group: fedg
subgroup: A_Themes
title: 主题继承
menu_title: 主题继承
menu_order: 5
version: 2.0
github_link: frontend-dev-guide/themes/theme-inherit.md
redirect_from: /guides/v1.0/frontend-dev-guide/themes/theme-inherit.html
---

<h2 id="theme-inherit-over">What's in this topic 此专题讲什么？</h2>

Theme inheritance enables you to easily extend themes and minimize the maintenance efforts. You can use an existing theme as a basis for customizations, or minor store design updates, like holidays decoration. Rather than copy extensive theme files and modify what you want to change, you can add overriding and extending files.

主题继承使你很容易扩展主题及减少维护工作量。你可以使用已有主题做为基础进行定制，或小部分更新店面设计，如假日装饰。除了复制大量的主题文件和修改你想改变的，你可添加覆写和扩展文件。

The level of theme inheritance is not limited.主题的继承层次是没有限制的

Theme inheritance is based on the fallback mechanism, which guarantees that if a view file is not found in the current theme, the system searches in the ancestor themes, module view files or library.

主题继承是基于回调机制，它保证如果在当前主题没有找到视图文件，系统会到被继承的主题、模块视图文件或库查找

The fallback order is slightly different for static assets (CSS, JavaScript, fonts and images) and other theme files, layouts and templates. The article describes the fallback for each type of theme files, and provides an overview of how to override ancestor themes and module designs.

回调的顺序和其它静态资源（CSS、JS、字体和图片）和其它主题文件、布局和模板略有不同。本篇介绍每种类型主题文件的回调，并提供如何覆写父主题和模块设计的概览。

For comprehensive information about developing theme components, see
subsequent chapters in this guide.

更多关于开发主题组件查看本指南随后章节

* TOC
{:toc}

## Set a parent theme 设置一个父主题

A parent theme is specified in the child theme `theme.xml` declaration file.

父主题是在子主题的theme.xml定义文件指定的

Example:
the Orange theme by OrangeCo inherits from the Magento Blank theme. The inheritance is declared in `app/design/frontend/OrangeCo/orange/theme.xml` as follows:

如OrangeCo的Orange主题继承自Blank主题。继承被定义在`app/design/frontend/OrangeCo/orange/theme.xml`中如下：

{% highlight xml %}
<theme xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Config/etc/theme.xsd">
     <title>Orange</title>
     <parent>Magento/blank</parent>
     <media>
         <preview_image>media/preview.jpg</preview_image>
     </media>
 </theme>
{% endhighlight xml %}

<div class="bs-callout bs-callout-info" id="info">
  <p>A parent and a child theme can belong to different vendors. For example, your custom theme can inherit from the Magento Blank theme.<br/>父和子主题可以属于不同的供应商。如你的自定义主题可以继承自Blank主题</p>
</div>

## Override view.xml file 覆写view.xml文件

If your theme does not contain a `view.xml` configuration file, it will be inherited from the parent theme. If you add the `<theme_dir>/etc/view.xml` file in your theme, it overrides the parent's file.

如果你的主题没有view.xml配置文件，它会继承自父主题。如果你在主题添加 `<theme_dir>/etc/view.xml`文件，它会覆写父主题的文件

## Override static assets {#theme-inherit-static} 覆写静态资源

Static assets, or static view files, are styles, JavaScript, images, and fonts.

静态资源或静态视图文件是样式、JS、图片和字体。

To customize static view files defined in the parent theme, module view, or library files, you can override them by adding a file with the same name in the relevant location according to the fallback schemes described further. This also refers to the `.less` files, which technically are not static assets.

要自定义父主题、模块视图或库文件的静态视图文件，你可以通过参考回调方案在相应位置添加同名的文件覆写他们。这也指.less文件，虽然技术上不是静态资源。

The particular directories, where the system searches in the course of the fallback, depend on whether module context is known for file. Following are the descriptions of both options.

系统在回调过程中查找的特定目录基于文是否知道模块上下文。下面是这种选项的描述。

If module context is not defined for a file:如果模块上下文不是定义为一个文件

1. Current theme static files for a specific locale (the locale set for the storefront): `<theme_dir>/web/i18n/<locale>`
2. Current theme static files: `<theme_dir>/web/`
2. Ancestor's static files, recursively, until a theme with no parent is reached:
- `<parent_theme_dir>/web/i18n/<locale>`
- `<parent_theme_dir>/web/`
3. Library static view files: `lib/web/`

If module context is defined for a file:

1. Current theme and current locale module static files:`<theme_dir>/web/i18n/<locale>/<Namespace>_<Module>`
2. Current theme module static files `<theme_dir>/<Namespace>_<Module>/web/`. Example: `app/design/frontend/OrangeCorp/orange/Magento_Catalog/web/`
3. Ancestor themes module static files, recursively, until a theme with no ancestor is reached:
- `<parent_theme_dir>/web/i18n/<locale>/<Namespace>_<Module>`
- `<parent_theme_dir>/<Namespace>_<Module>/web/`
3. Module static view files for the `frontend` area: `<module_dir>/view/frontend/web/`
4. Module static view files for the `base` area: `<module_dir>/view/base/web/`


<u>Example</u>

A company named OrangeCo created a theme named Orange. The theme files are located in `app/design/frontend/OrangeCo/orange`.
Orange inherits from the Magento Blank theme.

公司名为OrangeCo创建主题叫Orange。主题文件就在`app/design/frontend/OrangeCo/orange`. Orange继承自blank主题

Let's imagine OrangeCo needs to add some winter holidays decor. So it creates a new `orange_winter` theme, which inherits from Orange. The theme is located in `app/design/frontend/OrangeCo/orange_winter`.

让我们假设OrangeCo需要添加一些冬天节日装饰。所以创建一个新的orange_winter主题，继承自Orange。主题在`app/design/frontend/OrangeCo/orange_winter`

In the Orange theme there is a footer background image located at `app/design/frontend/OrangeCo/orange/web/images/background.jpg`.

Orange主题有一个底部背景图在

<img src="{{ site.baseurl }}common/images/inh-background1.jpg"/>

OrangeCo wants it to be replaced with a holiday one, so it places a new background image with exactly the same name and extension in `app/design/frontend/OrangeCo/orange_winter/web/images/background.jpg`

OrangeCo想把它替换为节日的图片，因此放一个新的有相同名称的背景放到`app/design/frontend/OrangeCo/orange_winter/web/images/background.jpg`

Once the Orange Winter theme is applied, the new holiday image overrides the one from Orange, so on storefront the holiday background is visible.

一旦 Orange Winter 主题被应用，新的节日图片会覆盖Orange的，然后在店面就可以看见节日背景

<img src="{{ site.baseurl }}common/images/inh-background2.jpg"/>


## Override templates {#theme-inherit-templates} 覆写模板

The fallback scheme for templates is the following (module context is always known for them):

模板的回调机制如下（它们永远知道模块主下文）

1. Current theme templates: `<theme_dir>/<Namespace>_<Module>/templates`
2. Ancestors themes templates, recursively, until a theme with no ancestor is reached: `<parent_theme_dir>/<Namespace>_<Module>/templates`
3. Module templates: `<module_dir>/view/frontend/templates`


So if you need to customize a certain template, you need to create an overriding one with the same name in the `../templates/<path_to_template>` directory in the theme module files. Where `<path_to_template>` is the path to the original template.

如果你需要自定义指定模板，你需要在主题模块文件的`../templates/<path_to_template>`目录创建一个同名文件来覆写。`<path_to_template>` 是原模块路径

For example, if you must override the `<Magento_Catalog_module_dir>/view/frontend/templates/category/widget/link/link_block.phtml` template, the `<path_to_template>` is `category/widget/link/`
例如： 如果你需要覆写模块

<u>Example</u>
By default, according to the module template, in the mini shopping cart products are listed under the Go to Checkout button:
<p><img src="{{ site.baseurl }}common/images/inherit_mini1.png" alt="In the minishopping cart products are listed under the Go to Checkout button "></p>

默认参考模块模板在小购物车里产品列表在Go to Checkout按钮下面：

The order is defined in the `<Magento_Checkout_module_dir>/view/frontend/templates/cart/minicart.phtml` module template. The Blank theme does not override this template.

订单定义在/minicart.phtml模块模板。blank模板没有覆写这个模板。

OrangeCo decided they want the product list to be displayed before the Go to Checkout button.
To do this, they need to add an overriding template for the corresponding module in the Orange theme folder:
`app/design/frontend/OrangeCo/orange/Magento_Checkout/templates/cart/minicart.phtml`
Note, that the path to the template inside the `templates` directory in the theme corresponds to that in the module.

OrangeCo考虑让产品列表显示在Go to Checkout按钮之前。 为实现这个，它们要添加对应的覆写模板在主题文件夹`app/design/frontend/OrangeCo/orange/Magento_Checkout/templates/cart/minicart.phtml`。注意templates里面的模板路径对应到模块里的。

Having changed the order or elements in the templates, OrangeCo got the minicart look like following:
已经修改过的模板订单或元素， OrangeCo的购物车看起来如下：
<p><img src="{{ site.baseurl }}common/images/inherit_mini2.png" alt="In the minishopping cart products are listed above the Go to Checkout button "></p>
You can find out what exactly code changes are required to perform this and other tasks in the <a href="{{page.baseurl}}frontend-dev-guide/templates/template-sample.html">Illustration of customizing templates topic</a>.

你可找到哪些个体代码需要修改来完成这种或其它任务在 <a href="{{page.baseurl}}frontend-dev-guide/templates/template-sample.html">定制模板专题详解</a>.

## Extend layouts {#theme-inherit-layout} 扩展布局

The layouts processing mechanism does not involve fallback. The system collects layout files in the following order:

布局处理机制没有包含回调。系统以如下顺序收集布局文件：

1. Current theme layouts: `<theme_dir>/<Vendor>_<Module>/layout/`
2. Ancestor themes layouts, starting from the  most distant ancestor, recursively until a theme with no parent is reached: `<parent_theme_dir>/<Vendor>_<Module>/layout/`
3. Module layouts for the `frontend` area: `<module_dir>/view/frontend/layout/`
4. Module layouts for the `base` area: `<module_dir>/view/base/layout/`

Unlike templates or images, layout can be not only overridden, but also extended. And the recommended way to customize layout is to extend it by creating theme extending layout files.

不同于模板或图片、布局不仅可以覆写，还可以扩展。推荐的自定义布局是通过创建主题扩展布局文件来扩展它。

To add an extending layout file: 添加一个扩展布局文件：

* Put your custom layout file in the `<theme_dir>/<Vendor>_<Module>/layout/` directory.
把你的自定义布局文件放在`<theme_dir>/<Vendor>_<Module>/layout/`目录

<u>Example</u>

OrangeCo decided they should remove the “Report bugs” link from the footer, defined in `<Magento_Theme_module_dir>/view/frontend/layout/default.xml`
To do this, they added an extending layout in `app/design/frontend/OrangeCo/orange/Magento_Theme/layout/default.xml` :

OrangeCo想移除底部“Report bugs”链接 。添加扩展布局在`app/design/frontend/OrangeCo/orange/Magento_Theme/layout/default.xml` :

{%highlight xml%}
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        <referenceBlock name='report.bugs' remove='true'/>
    </body>
</page>
{%endhighlight xml%}


For more information about extending layout refer to the <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">Extend a layout</a> article.

扩展布局更多信息查看

## Override layouts {#theme-inherit-layout-over} 覆写布局

Though overriding layouts is not recommended, it is still possible, and might be a solution for certain customization tasks.
To override the instructions from an ancestor theme layout file:

虽然覆写布局不推荐，但还是有可能，或许是某些定制任务的解决方案。要覆写父主题布局文件：

* Create a layout file with the same name in the `<theme_dir>/<Vendor>_<Module>/layout/override/theme/<Vendor>/<ancestor_theme>` directory.
在目录创建同名布局文件


To override module layout instructions (base layout): 覆写模块布局结构

* Create a layout file with the same name in the `<theme_dir>/<Vendor>_<Module>/layout/override/base` directory.
在目录创建同名布局文件










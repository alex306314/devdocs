---
layout: default
group: fedg
subgroup: B_Layouts
title: 一般布局任务
menu_title:一般布局任务
menu_order: 6
version: 2.0
github_link: frontend-dev-guide/layouts/xml-manage.md
redirect_from: /guides/v1.0/frontend-dev-guide/layouts/xml-manage.html
---

<h2>What's in this topic 此专题内容</h2>

This article describes the following typical layout customization tasks:

此文描述如下典型布局自定义任务：

*	<a href="#layout_markup_columns">Set the page layout 设置页面布局</a>
*	<a href="#layout_markup_css">Include static resources (JavaScript, CSS, fonts) in &lt;head&gt;在head包含静态文件</a>
*	<a href="#layout_markup_css_remove">Remove static resources (JavaScript, CSS, fonts) in &lt;head&gt;移除静态文件</a>
*	<a href="#create_cont">Create a container 创建一个容器</a>
*	<a href="#ref_container">Reference a container 引用一个容器</a>
*	<a href="#xml-manage-block">Create a block 创建一个区块</a>
*	<a href="#set_template">Set a block's template 设置一个区块的模板</a>
*	<a href="#layout_markup_modify-block">Modify block arguments 修改区块参数 </a>
*	<a href="#xml-manage-ref-block">Reference a block 引用一个区块</a>
*	<a href="#layout_markup_block-properties">Use block object methods to set block properties 引用区块对象方法设置区块属性</a>
*	<a href="#layout_markup_rearrange">Rearrange elements 重新排序元素</a>
*	<a href="#layout_markup_remove_elements">Remove elements 移除元素</a>
*	<a href="#layout_markup_replace_elements">Replace elements 替换元素</a>

<div class="bs-callout bs-callout-info" id="info">
<span class="glyphicon-class">
  <p>To ensure stability and secure your customizations from being deleted during upgrade, do not change out-of-the-box Magento module and theme layouts. To customize layout, create extending and overriding layout files in your custom theme.
  为确保稳定性并保护你的自定义在升级过程中不被删除，请勿更改开箱即用的Magento模块和主题布局。要自定义布局，在你的自定义主题中创建扩展和覆写布局文件
  </p></span>
</div>

<h2 id="layout_markup_columns">Set the page layout 设置页面布局</h2>

The type of page layout to be used for a certain page is defined in the page configuration file, in the `layout` attribute of the root <code>&lt;page&gt;</code> node.

用于一个具体页面的页面布局类型是定义在页面配置文件中，在根节点page的layout属性的中

Example:
Change the layout of Advanced Search page from default "1-column" to "2-column with left bar". To do this, extend `catalogsearch_advanced_index.xml` in your theme by adding the following layout:

例如：修改高级搜索页面的布局从"1-column" 到 "2-column with left bar"。要实现这个，在你的主题通过添加如下布局扩展`catalogsearch_advanced_index.xml`

<b><code>app/design/frontend/&lt;Vendor&gt;/&lt;theme&gt;/Magento_CatalogSearch/layout/catalogsearch_advanced_index.xml</code></b>

{%highlight xml%}
<page layout="2columns-left" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
...
</page>
{%endhighlight xml%}


<h2 id="layout_markup_css">Include static resources (JavaScript, CSS, fonts) 包含静态资源</h2>

JavaScript, CSS and other static assets are added in the `<head>` section of a <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html#layout-types-conf" target="_blank">page configuration</a> file. The default look of a Magento store page `<head>` is defined by `app/code/Magento/Theme/view/frontend/layout/default_head_blocks.xml`. The recommended way to add CSS and JavaScript is to extend this file in your custom theme, and add the assets there.
The following file is a sample of a file you must add:

JS、CSS和其它静态资源是在页面配置文件的head区域添加。默认的网店样式head是被定义在 `app/code/Magento/Theme/view/frontend/layout/default_head_blocks.xml`。推荐的添加CSS和JS是在你的自定义主题扩展这个文件，然后在那添加资源。下面的文件是你要添加的示例文件：

<code>&lt;theme_dir&gt;/Magento_Theme/layout/default_head_blocks.xml</code>

{%highlight xml%}
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <head>
        <!-- Add local resources -->
    	<css src="css/my-styles.css"/>
    
        <!-- The following two ways to add local JavaScript files are equal -->
        <script src="Magento_Catalog::js/sample1.js"/>
        <link src="js/sample.js"/>
		
    	<!-- Add external resources -->
	    <css src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap-theme.min.css" src_type="url" />
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/js/bootstrap.min.js" src_type="url" />
        <link src="http://fonts.googleapis.com/css?family=Montserrat" src_type="url" /> 
    </head>
</page>
{%endhighlight xml%}


When adding external resources, specifying the <code>src_type="url"</code> argument value is a must.

当添加外部资源时，必须指定参数值<code>src_type="url"</code>


You can use either `<link src="js/sample.js"/>` or `<script src="js/sample.js"/>` instruction to add a locally stored JavaScript file to your theme.

你可以使用`<link src="js/sample.js"/>` 或 `<script src="js/sample.js"/>`指令向你的主题添加本地存储的JS文件

The path to assets is specified relatively to one the following locations:

资源路径是指定的相对下位置中的一个：

<ul>
<li><code>&lt;theme_dir&gt;/web</code></li>
<li><code>&lt;theme_dir&gt;/&lt;Namespace&gt;_&lt;Module&gt;/web</code></li>

</ul>

<h3>Adding conditional comments 添加条件注解</h3>
<a href="http://en.wikipedia.org/wiki/Conditional_comment" target="_blank">Conditional comments</a> are meant to give special instructions for Internet Explorer. 
In the terms of adding assets, you can add CSS files to be included for a specific version of Internet Explorer. 
A sample follows:

条件注解指的是为IE浏览器提供的特殊指令。增加静态资源方面，你可以对指定版本IE浏览器添加包含的CSS

{%highlight xml%}
    <head>
        <css src="css/ie-9.css" ie_condition="IE 9" />
    </head>
</page>
{%endhighlight xml%}

This adds an IE conditional comment in the generated HTML, like in the following example:

这句在生成的HTML添加了IE条件注解，如下：

{%highlight html%}
<!--[if IE 9]>
<link rel="stylesheet" type="text/css" media="all" href="<your_store_web_address>/pub/static/frontend/OrangeCo/orange/en_US/css/ie-9.css" />
<![endif]-->
{%endhighlight html%}

In this example, <code>orange</code> is a custom theme created by the OrangeCo vendor.

在这个示例<code>orange</code>是OrangeCo供应商创建的一个自定义主题

<h2 id="layout_markup_css_remove">Remove static resources (JavaScript, CSS, fonts) 移除静态资源</h2>

To remove the static resources, linked in a page `<head>`, make a change similar to the following in a theme extending file:

为了移除链接在页面head的静态资源，在一个主题扩展文件做如下相似修改：

`app/design/frontend/<Vendor>/<theme>/Magento_Theme/layout/default_head_blocks.xml`

{%highlight xml%}
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
   <head>
        <!-- Remove local resources -->
        <remove src="css/styles-m.css" />
        <remove src="my-js.js"/>
        <remove src="Magento_Catalog::js/compare.js" />
								
	<!-- Remove external resources -->
        <remove src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap-theme.min.css"/>
        <remove src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/js/bootstrap.min.js"/>
        <remove src="http://fonts.googleapis.com/css?family=Montserrat" /> 
   </head>
{%endhighlight xml%}

Note, that if a static asset is added with a module path (for example `Magento_Catalog::js/sample.js`) in the initial layout, you need to specify the module path as well when removing the asset.

注意： 如果在初始布局一个静态资源是随着模块路径一起添加的，你也需要在移除资源时指定模块路径。

<h2 id="create_cont">Create a container 创建一个容器</h2>

Use the following sample to create (declare) a container:

使用如下示例创建一个容器

{%highlight xml%}
<container name="some.container" as="someContainer" label="Some Container" htmlTag="div" htmlClass="some-container" />
{%endhighlight xml%}

<h2 id="ref_container">Reference a container 引用一个容器</h2>

To update a container use the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_ref" target="_blank">`<referenceContainer>`</a> instruction.

更新一个容器使用`<referenceContainer>`指令

Example: add links to the page header panel. 如给页面头部添加链接 

{%highlight xml%}
<referenceContainer name="header.panel">
        <block class="Magento\Framework\View\Element\Html\Links" name="header.links">
            <arguments>
                <argument name="css_class" xsi:type="string">header links</argument>
            </arguments>
        </block>
</referenceContainer>
{%endhighlight xml%}

<h2 id="xml-manage-block">Create a block 创建一个区块</h2>

Blocks are created (declared) using the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_block" target="_blank">`<block>`</a> instruction.

区块使用`<block>`指令创建（声明）

Example: add a block with a product SKU information. 如添加一个有产品SKU信息的区块

{%highlight xml%}
<block class="Magento\Catalog\Block\Product\View\Description" name="product.info.sku" template="product/view/attribute.phtml" after="product.info.type">
    <arguments>
        <argument name="at_call" xsi:type="string">getSku</argument>
        <argument name="at_code" xsi:type="string">sku</argument>
        <argument name="css_class" xsi:type="string">sku</argument>
    </arguments>
</block>
{%endhighlight xml%}


<h2 id="xml-manage-ref-block">Reference a block 引用一个区块</h2>

To update a block use the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_ref" target="_blank">`<referenceBlock>`</a> instruction.

要更新一个区块使用`<referenceBlock>`指令

Example: pass the image to the `logo` block. 如向LOGO区块传递图片

{%highlight xml%}
<referenceBlock name="logo">
        <arguments>
            <argument name="logo_file" xsi:type="string">images/logo.png</argument>
        </arguments>
</referenceBlock>
{%endhighlight xml%}

## Set a block template {#set_template} 设置区块模板

There are two ways to set the template for a block: 

有两种设置区块模板的方式：

- using the `template` attribute
- using the `<argument>` instruction

Both approaches are demonstrated in the following examples of changing the template of the page title block.

如下两种方法演示修改页面标题区块模板

**Example 1:**

{%highlight xml%}
 <referenceBlock name="page.main.title" template="%Namespace_Module::new_template.phtml%"/>
{%endhighlight%}

**Example 2:** 

{%highlight xml%}
 <referenceBlock name="page.main.title">
        <arguments>
            <argument name="template" xsi:type="string">%Namespace_Module::new_template.phtml%</argument>
        </arguments>
 </referenceBlock>
{%endhighlight%}

In both example, the template is specified according to the following:

两个示例中，模板根据下面来指定：

 * `Namespace_Module:` defines the module the template belongs to. For example, `Magento_Catalog`.
 <br/>定义模板所属的模块。如`Magento_Catalog`
 * `new_template.phtml`: the path to the template relatively to the `templates` directory. It might be `<module_dir>/view/<area>/templates` or `<theme_dir>/<Namespace_Module>/templates`.
 <br/>相对于`templates`目录的路径。有可能是`<module_dir>/view/<area>/templates` 或 `<theme_dir>/<Namespace_Module>/templates`


<div class="bs-callout bs-callout-info" id="info">
  <p>Template values specified as attributes have higher priority during layout generation, than the ones specified using <code>&lt;argument&gt;</code>. It means, that if for a certain block, a template is set as attribute, it will override the value you specify in <code>&lt;argument&gt;</code> for the same block.
  作为属性指定的模板值在布局生成时，比使用<code>&lt;argument&gt;</code>指定的拥有更高权限。也就是如果对一个指定区块，用属性设置的模板会覆写在<code>&lt;argument&gt;</code>中指定的值。
  </p>
</div>

<h2 id="layout_markup_modify-block">Modify block arguments 修改区块参数</h2>

To modify block arguments, use the `<referenceBlock>` instruction.

修改区块参数使用`<referenceBlock>`指令

Example: change the value of the existing block argument and add a new argument.

如修改已有区块参数值并添加新参数 

Initial block declaration: 原始区块定义：

{%highlight xml%}
...
<block class="Namespace_Module_Block_Type" name="block.example">
    <arguments>
        <argument name="label" xsi:type="string">Block Label</argument>
    </arguments>
</block>
...
{%endhighlight xml%}

Extending layout:

{%highlight xml%}
...
<referenceBlock name="block.example">
    <arguments>
        <!-- Modified block argument -->
        <argument name="label" xsi:type="string">New Block Label</argument>
        <!- Newly added block argument -->
        <argument name="custom_label" xsi:type="string">Custom Block Label</argument>
    </arguments>
</referenceBlock> 
...
{%endhighlight xml%}

<h2 id="layout_markup_block-properties">Use block object methods to set block properties 使用区块对象方法设置区块属性</h2>

There are two ways to access block object methods:

有两种方式获取区块对象方法

- using the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#argument"><code>&lt;argument&gt;</code></a> instruction for `<block>` or `<referenceBlock>`
<br/>使用`<block>` or `<referenceBlock>`的<code>&lt;argument&gt;</code>指定
- using the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_act"><code>&lt;action&gt;</code></a> instruction. This way is not recommended, but can be used for calling those methods, which are not refactored yet to be accessed through `<argument>`. 
<br/>
使用<code>&lt;action&gt;</code>指令，此方式不推荐，但可用于调用那些还没有被argument访问重构的方法。

Example 1: Set a CSS class and add an attribute for the product page using `<argument>`.

如使用`<argument>`为产品页面设置CSS类并添加一个属性。

Extending layout: 扩展布局

{%highlight xml%}
	<referenceBlock name="page.main.title">
		<arguments>
		    <argument name="css_class" xsi:type="string">product</argument>
		    <argument name="add_base_attribute" xsi:type="string">itemprop="name"</argument>
		</arguments>
	</referenceBlock>
{%endhighlight xml%}

Example 2: Set a page title using `<action>`.  使用action设置页面标题

<div class="bs-callout bs-callout-warning" id="info">
<span class="glyphicon-class">
 <p>Do not use <code>&lt;action&gt;</code>, if the method implementation allows calling it using <code>&lt;argument&gt;</code></a> for <code>&lt;block&gt;</code> or <code>&lt;referenceBlock&gt;</code>.
 <br/>
 如果<code>&lt;block&gt;</code> or <code>&lt;referenceBlock&gt;</code>允许使用<code>&lt;argument&gt;</code>调用方法实现，就不要使用action
 </p></span>
</div>


Extending layout:

{%highlight xml%}
	...
	<referenceBlock name="page.main.title">
	    <action method="setPageTitle">
	        <argument translate="true" name="title" xsi:type="string">Catalog Advanced Search</argument>
	    </action>
	</referenceBlock>
	...
{%endhighlight xml%}

<h2 id="layout_markup_rearrange">Rearrange elements 重新排列元素</h2>

In layout files you can change the elements order on a page. This can be done using one of the following:

在布局文件中你可以改变一个页面中元素的顺序。可以使用如下任意一种方式实现：

* <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_mv" target="_blank">`<move>` instruction</a>: allows changing elements' order and parent.
<br/>move指令允许改变元素顺序和父级
* <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_xml-instrux_before-after" target="_blank">`before` and `after` attributes of `<block>`</a>: allows changing elements' order within one parent.
<br/> `<block>`的`before` and `after`属性：改变同一个父级内的元素顺序

<p></p>
Example of `<move>` usage:
put the stock availability and SKU blocks next to the product price on a product page.

 `<move>`示例使用：在产品页面把库布可用性和SKU区块放到产品价格边上。

In the Magento Blank theme these elements are located as follows: 在blank主题这些元素定义如下：

<img src="{{ site.baseurl }}common/images/layout_image1.png" />

Let's place the stock availability and SKU blocks after product price block on a product page, and move the review block out of the product-info-price container.
To do this, add the extending `catalog_product_view.xml` in the `app/design/frontend/OrangeCo/orange/Magento_Catalog/layout/` directory:

让我们在产品页面把库量和SKU区块放到产品价格区块之后，然后把 review 区块移到product-info-price容器外面。要实现这些：在`app/design/frontend/OrangeCo/orange/Magento_Catalog/layout/`目录添加扩展`catalog_product_view.xml`

{%highlight xml%}
<page layout="1column" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        <move element="product.info.stock.sku" destination="product.info.price" after="product.price.final"/>
        <move element="product.info.review" destination="product.info.main" before="product.info.price"/>
    </body>
</page>

{%endhighlight xml%}

This would make the product page look like following: 修改的产品页面外观如下：

<img src="{{ site.baseurl }}common/images/layout_image2.png" />

<div class="bs-callout bs-callout-info" id="info">
<span class="glyphicon-class">
  <p>To learn how to locate the layout file you need to customize, see <a href="{{page.baseurl}}frontend-dev-guide/themes/debug-theme.html" target="_blank">Locate templates, layouts, and styles</a>.
  <br/>
  学习如何定位你要自定义的布局文件查看定位模板、布局和样式
  </p></span>
</div>

<h2 id="layout_markup_remove_elements">Remove elements 移除元素</h2>

Elements are removed using the `remove` attribute for the `<referenceBlock>` and `<referenceContainer>`. 

元素移除使用`<referenceBlock>` and `<referenceContainer>`的remove属性

**Example**: remove the Compare Products sidebar block from all store pages. 

示例： 从所有商店页面移除产品对比工具条

This block is declared in `app/code/Magento/Catalog/view/frontend/layout/default.xml`:

这个区块定义在`app/code/Magento/Catalog/view/frontend/layout/default.xml`:

{%highlight xml%}
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
...
        <referenceContainer name="sidebar.additional">
            <block class="Magento\Catalog\Block\Product\Compare\Sidebar" name="catalog.compare.sidebar" template="product/compare/sidebar.phtml"/>
        </referenceContainer>
...
    </body>
</page>
{%endhighlight xml%}


To remove the block, add the extending `default.xml` in your theme:
`<theme_dir>/Magento_Catalog/layout/default.xml`

要移除区块，在你的主题添加`default.xml`扩展

In this file, reference the element having added the `remove` attribute:

在这个文件引用元素并添加remove属性

{%highlight xml%}

<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
...
        <referenceBlock name="catalog.compare.sidebar" remove="true" />
...
    </body>
</page>

{%endhighlight xml%}


<h2 id="layout_markup_replace_elements">Replace elements 替换元素</h2>

To replace an element, <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_rem" target="_blank">remove it</a> and add a new one.

要替换元素，移除它然后再添加一个新的


#### Related topics:

*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html" target="_blank">Layout instructions</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">Extend a layout</a>


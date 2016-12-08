---
layout: default
group: fedg
subgroup: B_Layouts
title: 覆写主题
menu_title: 覆写主题
menu_order: 5
version: 2.0
github_link: frontend-dev-guide/layouts/layout-override.md
redirect_from: /guides/v1.0/frontend-dev-guide/layouts/layout-override.html
---

<h2 id="fedg_layout_override_overview">What's in this topic 此专题讲什么</h2>

Not all layout customizations can be performed by <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">extending</a> existing layouts. If the amount of customizations is large, you can use the overriding function for the needed layout file. This means that the new file that you place in the theme will be used instead of the parent <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#layout-loc" target="_blank">theme</a> layout file of <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#layout-loc" target="_blank">base</a> layout file.

不是所有的布局自定义可以通过扩展布局来实现。如果定制量很大，你可以对需要的布局文件使用覆写功能。意味着你在主题放的新文件会替换父主题基础布局文件

In this article, <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html#layout-types-page" target="_blank">page layouts</a>, <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html#layout-types-conf" target="_blank">page configurations</a>, and <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html#layout-types-gen" target="_blank">generic layouts</a> are referred to as *layout files*, as the mechanism of overriding is similar for all of them.

本文，页面布局、页面配置、和通用布局都是指布局文件。因为他们的覆写机制都是一样的。


Layout files with instructions that override the default or parent theme files are referred to as *overriding layout files*.

具有覆写默认或父主题文件的指令布局文件称为覆写布局文件

<h2>Examples of customizations that involve overriding layouts 包含覆写主题的定制示例</h2>
Examples of customizations that involve overriding layouts:

*	Suppressing method invocation. 禁止方法调用

	<div class="bs-callout bs-callout-info" id="info">
		<p>Overriding is not necessary if a block has a method that cancels the effect of the originally invoked method. In this case, you can customize the layout by adding a layout file where the canceling method is invoked.
		<br/>
		如果区块具有取消最被调用的方法的效果，则覆写是不必要的。在这种情况，你可以通过添加执行取消方法的布局文件来自定义布局
		</p>
	</div>

*	Modifying method arguments.修改方法参数
*	Canceling block/container removal using the `remove` attribute. 使用remove属性取消block或container移除
*	Setting XML attributes of blocks and containers.设置区块和容器的xml属性

	<div class="bs-callout bs-callout-info" id="info">
		<p>Certain attributes, like <code>htmlClass</code>, <code>htmlId</code>, <code>label</code> attributes can be changed in <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">extending layouts</a>.
		</br/>
		确定的属性像htmlClass、ID/label 属性可以在扩展布局被修改
		</p>
	</div>
*	Removing block arguments. 移除区块参数 
*	Modifying and suppressing <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#handle" target="_blank">handles</a> inclusion.
修改和禁止handles包含
*	Removing all handle instructions by declaring an overriding layout file with an empty handle.
通过定义有一个空handle的覆写文件移除所有handle指令

<h2 id="fedg_layout_override_howto">How to override a layout 如何覆写布局</h2>

This section discusses how to override:

*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#layout-loc" target="_blank">Base layout 基础布局</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#layout-loc" target="_blank">Theme layout 主题布局</a>

<h3 id="fedg_layout_override_default">Override base layouts 覆写基础布局</h3>

To add an overriding base layout file (to override a base layout provided by the module):
要覆写基础布局文件（覆写模块提供的基础布局）

2.	Put a layout file with the same name in the following location:

<pre>
&lt;theme_dir&gt;
&nbsp;&nbsp;|__/&lt;Namespace_Module&gt;
&nbsp;&nbsp;&nbsp;&nbsp;|__/layout
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|__/override
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|__/base
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--&lt;layout1&gt;.xml
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--&lt;layout2&gt;.xml

</pre>

These files override the following layouts: 这些文件覆写如下布局

<ul>
<li><code>&lt;module_dir&gt;/view/frontend/layout/&lt;layout1&gt;.xml</code></li>
<li><code>&lt;module_dir&gt;/view/frontend/layout/&lt;layout2&gt;.xml</code></li>
</ul>

<h3 id="fedg_layout_override_theme">Override theme layouts 覆写主题布局</h3>

To add an overriding theme file (to override a parent theme layout):

要覆写主题文件

2.	Put a layout file with the same name in the following location:

<pre>
&lt;theme_dir&gt;
&nbsp;&nbsp;|__/&lt;Namespace_Module&gt;
&nbsp;&nbsp;&nbsp;&nbsp;|__/layout
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|__/override
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|__/theme
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|__/&lt;Parent_Vendor&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|__/&lt;parent_theme&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--&lt;layout1&gt;.xml
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|--&lt;layout2&gt;.xml
</pre>

These files override the following layouts:

<ul>
<li><code>&lt;parent_theme_dir&gt;/&lt;Namespace&gt;_&lt;Module&gt;/layout/&lt;layout1&gt;.xml</code></li>
<li><code>&lt;parent_theme_dir&gt;/&lt;Namespace&gt;_&lt;Module&gt;/layout/&lt;layout1&gt;.xml</code></li>
</ul>

<div class="bs-callout bs-callout-info" id="info">
<span class="glyphicon-class">
  <p>To override page layout files, use 'page_layout' directory name instead of 'layout'
	<br/>
	要覆写页面布局文件，使用page_layout目录名替换layout 
	</p></span>
</div>


<h2 id="override-mistake">Customization mistakes 定制的错误</h2>

Although the layout overriding mechanism provides great customization flexibility, it's possible to use it to add logically irrelevant changes. We strongly recommend you not make the following changes:

虽然布局覆写机制提供了强大灵活的自定义，有可能用它来添加逻辑不相关的修改。我们强列建议不要做如下修改：

*	Changing block name or alias. The name of a block should not be changed, and neither should the alias of a block remaining in the same parent element.<br/>
修改区块名或别名。区块的名称不应该被修改且它的别名也要和父元素保持一致
*	Changing handle inheritance. For example, you should not change the page type parent handle.
<br/>修改句柄继承。如你不应该修改页面类型的父句柄

#### Related topics:

*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">Extend a layout</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/themes/theme-create.html" target="_blank">Create a theme</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html" target="_blank">Layout instructions</a>

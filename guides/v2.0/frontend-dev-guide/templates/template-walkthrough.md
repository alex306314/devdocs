---
layout: default  
group: fedg
subgroup: C_Templates
title: 模板定制演练
menu_title: 模板定制演练
menu_order: 2
version: 2.0
github_link: frontend-dev-guide/templates/template-walkthrough.md
redirect_from: /guides/v1.0/frontend-dev-guide/templates/template-walkthrough.html
---

## What's in this topic
This topic walks you through how to customize a template.

本主题引导你如何定制模板

## Prerequisites 先决条件

[Set]({{page.baseurl}}config-guide/cli/config-cli-subcommands-mode.html) your Magento application to the developer [mode]({{page.baseurl}}config-guide/bootstrap/magento-modes.html). The application mode influences the way static files are cached by Magento. The recommendations about theme development we provide in this chapter are developer/default-mode specific.

设置为开发者模式。模式影响静态文件缓存方式。在本章节我们提供的关于主题开发者的建议特指开发者/默认模式

## Template customization walkthrough 模板定制演练

To customize a template: 要定制一个模板：

1. Locate the template which is associated with the page/block you want to change using <a href="{{page.baseurl}}frontend-dev-guide/themes/debug-theme.html#debug-theme-templ" target="_blank">template hints</a>.
<br/>使用模板提示定位有关你想要修改的页面/区块模块

2. Copy the template to your theme folder according to the <a href="{{page.baseurl}}frontend-dev-guide/templates/template-override.html#template-convention" target="_blank">template storing convention</a>.<br/>参考模板存储规则复制模板到你的主题目录。

3. Make the required changes. 做需要的修改

To add a new template in a theme: 在主题添加新模板

1. Add a template in your theme directory according to the template storing convention. 
<br/>依照模板存储规则在你的主题目录添加一个模板

2. Assign your template to a block in the <a href="{{page.baseurl}}frontend-dev-guide/templates/template-override.html#template-layout" target="_blank">corresponding layout file</a>. 
<br/>在对应的布局文件指定你的模板到一个区块

<div class="bs-callout bs-callout-info" id="info">
<p>If you add a new <code>.html</code> template, and then edit it, the changes will not apply until you do the following: delete all files in the <code>pub/static/frontend</code> and <code>var/view_preprocessing</code> directories, then reload the pages. You can delete the files manually or run the <code>grunt clean:&lt;theme_name&gt;</code> command in CLI. For details about using Grunt in Magento see <a href="{{page.baseurl}}frontend-dev-guide/css-topics/css_debug.html#grunt_prereq">Installing and configuring Grunt</a>.
<br/>
如果你添加一个新的.html模板，然后编辑它，在你做如下操作前修改不会生效： 删除 <code>pub/static/frontend</code>和<code>var/view_preprocessing</code>目录中的所有文件，然后重载页面。你可手动删除文件或运行<code>grunt clean:&lt;theme_name&gt;</code>命令。更多关于grunt查看安装和配置Grunt
</p>
</div>

## Walkthrough illustration: adding a message to the customer review form 演练示例：添加信息到客户评论表单
A small customization to illustrate the walkthrough: in their Orange theme, the OrangeCo company wants to add a short text to the product review form to encourage customers to write reviews. 

一个小的自定义演练演示：在Orange主题中，OrangeCo公司想在产品评论表单添加一个简短的文本来鼓励客户写评论。

The following image illustrates how the default review form looks like: 
下图说明默认的评论表单外观：

<img src="{{site.baseurl}}common/images/template_walk_without_text.png" alt="a default review form">

To add the text, OrangeCo needs to override the default review form template in the Orange theme. 

要添加文本，OrangeCo需要在Orange主题覆写默认的评论表单模板。

First, they copy the `form.phtml` template from `<Magento_Review_module_dir>/view/frontend/templates` to the corresponding subdirectory in the Orange theme directory: `app/design/frontend/OrangeCo/orange/Magento_Review/templates`.

首先从`<Magento_Review_module_dir>/view/frontend/templates`复制 `form.phtml` 模板到Orange主题目录`app/design/frontend/OrangeCo/orange/Magento_Review/templates`的对应子目录

In the theme `form.phtml` file they add the HTML snippet with the message before the <code>&lt;form&gt;</code>:

在主题 `form.phtml` 文件他们在表单之前添加信息HTML片段

<img src="{{site.baseurl}}common/images/template-sample-code.png" alt="a HTML snippet you need to add">

Here's how the form will look when the Orange theme is applied in a store: 下面是Orange主题应用后表单样式

<img src="{{site.baseurl}}common/images/template_with_text.png" alt="Review form with the new message added">






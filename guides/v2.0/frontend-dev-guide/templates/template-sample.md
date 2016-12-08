---
layout: default  
group: fedg
subgroup: C_Templates
title: 自定义模板演示
menu_title: 自定义模板演示
menu_order: 3

version: 2.0
github_link: frontend-dev-guide/templates/template-sample.md
redirect_from: /guides/v1.0/frontend-dev-guide/templates/template-sample.html
---
<h2>What's in this topic</h2>
This topic contains a step-by-step illustration of solving a typical design customization task using templates.

本专题包含逐步讲解使用模板解决典型的设计自定义任务

<h2>Sample template customization: changing a layout of the mini shopping cart模块自定义示例：改变微型购物车的布局</h2>
In the Magento basic Blank theme, in the mini shopping cart, products are listed under the **Go to Checkout** button, like following:

在blank主题中， 微型购物车中，产品列表显示在结算按钮下面， 如：

<img src="{{ site.baseurl }}common/images/inherit_mini1.png" alt="An image of a mini shopping cart where products are listed under the **Go to Checkout** button">

OrangeCo decided they want to change this and display the product list before the **Go to Checkout** button.

OrangeCo决定它们想改变这种然后显示产品列表到结算铵钮之前
 
The template responsible for displaying the mini-shopping cart items and controls is [`<Magento_Checkout_module_dir>/view/frontend/web/template/minicart/content.html`]({{site.mage2000url}}app/code/Magento/Checkout/view/frontend/web/template/minicart/content.html).
Here is the part of the code OrangeCo worked with:

负责显示和控制微型购物车项目的模板是{site.mage2000url}}app/code/Magento/Checkout/view/frontend/web/template/minicart/content.html。这是OrangeCo工作的一部分代码

<img src="{{site.baseurl}}common/images/templ_overview_code1.png" alt="code">


They created a new Orange theme and copied the `content.phtml` to the theme directory:
`app/design/frontend/OrangeCo/orange/Magento_Checkout/web/template/minicart/content.html`
In their copy of the templates, they changed the order of the blocks as follows:

他们创建一个新的Orange主题然后复制 `content.phtml` 到主题目录：`app/design/frontend/OrangeCo/orange/Magento_Checkout/web/template/minicart/content.html`。在他们复制的模块它们修改区块顺序如下：

<img src="{{site.baseurl}}common/images/templ_overview_code2.png" alt="code">

When the Orange theme was applied, the mini shopping cart with products looked like following:

当Orange主题被应用，有产品的微型购物车看起来像这样：

<img src="{{site.baseurl}}common/images/inherit_mini2.png" alt="In the minishopping cart products are listed before the Go to Checkout button ">



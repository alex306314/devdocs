---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: 店面定制策略
menu_title: 店面定制策略
menu_order:
version: 2.0
github_link: architecture/storefront_customization.md

---

<h2>店面定制策略</h2>

We can generalize about the range of storefront customizations that the Magento supports. This range spans the simplest customizations, which involve only small additions to the default Magento storefront settings, to a complete replacement of Magento-provided HTML and CSS.

我们可以概括关于Magento支持的店面定制范围。这个范围包括从最简单的附加店面设置到完整的HTML、css替换。

These four levels of potential storefront customization are listed in order to increase complexity.

按复杂度的增加列出这四种层次的潜在店面定制

<h3>Extend Magento-Provided CSS 扩展Magento提供的CSS</h3>
Magento supplies a default theme and a LESS-based CSS set of styles. You can substantially change a storefront using CSS only.  This uncomplicated strategy might suit projects with a limited budget, or might interest developers who create different skins for a site. A small business enter this process of storefront customization by buying a third-party developed theme from Magento Marketplace to extend the default values.

Magento提供了一个默认主题和一组基于LESS的样式。你可以只使用CSS来修改店面。 这个简单的策略或许适用于预算紧张的项目，或是有兴趣的开发者想创建一个不同的皮肤。要开始这种方式的店面定制可以通过从市场购买第三方开发好的主题来扩展默认值。

<h3>Replace PHTML template files修改PHTML模板文件</h3>
In addition to extending the default CSS, you can generate different HTML markup. For example, you might need to add a missing CSS class name, or an add an extra `<div>` tag to achieve some visual effect. You might also need to tweak some JavaScript to cope with different HTML markup. This change is more demanding than simply extending Magento CSS, but is still within the grasp of smaller projects and leaner teams.

除了扩展默认的CSS， 你也可以生成不同的HTML标签。比如你可能需要添加一个缺少的CSS类名，或添加一个额外的div标签来获得视觉效果。你也有可能需求调整一些JS来处理不同的HTML标记。这些修改比起简单的扩展CSS要求更高，但这个还是在小的项目和小团队可以掌控。

<h3>Replace Magento-Provided CSS修改Magento提供的CSS</h3>
Rather than edit the default CSS provided by Magento, you might decide to replace all the default storefront CSS code with your own. This strategy avoids tying a project to the Magento-provided CSS, but puts a greater burden on project development and integration. It also allows use of different CSS tools or technologies not provided with Magento. Partners who build their own set of CSS libraries could reuse these libraries on different customer projects. (These unique CSS libraries may help differentiate a partner from others in the market.)

胜于修改Magento提供的默认CSS，你可能会考虑用你自己的CSS代码替换整个默认店面CSS。这种策略避免把Magento提供的CSS绑到一个系统，而把更大的负担放到系统开发和集成上。它也允许使用不是Magento提供的不同的CSS工具或技术。创建了自己的CSS库可以在不同的客户项目上重用。（那些独特的CSS库在市场会帮助区分合伙人）

In addition to replacing CSS files, you might need to replace small amounts of HTML and JavaScript.

除了修改CSS文件之外，你可能需要替换小部分HTML和JS

<h3>Replace Magento-Provided CSS, HTML, and JavaScript替换Magento提供的CSS、HTML和JS</h3>
Delivering a sharply different shopping experience than the default Magento installation provides is a more substantial task. However, the tradeoff might be a more complicated experience integrating additional extensions into your installation in the future.

提供一种和默认安装的Magento系统完全不同的购物体验是更实质性的任务。而在未来集成附加扩展到你的系统，如何权衡是一种更复杂的经验

<div class="bs-callout bs-callout-info" id="info">
  <p>Note: Any customization of your storefront will work optimally, and provide the easiest path for later upgrades, if you follow the best practice of consistently compartmentalizing code by type. For example, keep all HTML in PHTML files; keep all JavaScript in JavaScript files.</p>
  <p>注意：如果你遵循始终按类型区分代码的最佳实践， 任何店面的修改都会很好的工作，并为后期升级提供最简单的方式。比如， 保持所有HTML都在PHTML文件里， 保持所有JS都在JS文件里</p>
</div>

<h3>Related topics相关主主题</h3>

<a href="{{page.baseurl}}frontend-dev-guide/bk-frontend-dev-guide.html">Frontend Developer Guide前端开发者指南</a>


<a href="{{page.baseurl}}javascript-dev-guide/bk-javascript-dev-guide.html">JavaScript Developer GuideJS开发者指南</a>

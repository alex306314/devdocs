---
layout: default
group: arch-guide
subgroup: Logical View
title: 第三方库
menu_title: 第三方库
menu_order: 5
version: 2.0
github_link: architecture/archi_perspectives/third-party-libs.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/third-party-libs.html
---


<h2>Third-party libraries第三方库</h2>

Magento depends on a set of external libraries. You can use Composer to manage these dependencies. Composer downloads all of the external libraries that are included in its main configuration file and installs them under its default installation directory (`vendor/`). Third-party libraries  include Zend framework files and Symfony libraries.   

Magento基于一组外部库。你可以使用composer管理这些依赖。Composer下载所有外部库包含它们的主配置文件并安装它们到默认安装目录（vendor）。第三方库包括zend框架文件和symfony库

There are some required libraries that Composer does not load. These reside in `lib/` and include JavaScript libraries (none of which are loaded by Composer) and a few PHP libraries. (You can also use Composer  to manage dependencies between various components within Magento.)

还有一些需要的库Composer没有加载。这些在lib目录包括JS库和一小部分PHP库（你也可以使用Composer来管理各种组件之间的依赖）

If you are extending your Magento storefront to interact with third-party applications, you might need to include additional external libraries. These external libraries can be as simple as a wrapper for an API of a third-party product you are integrating with your Magento storefront, or an entire framework. 

如果你在扩展你的店面来和第三方应用程序交互，你或许需要包含附加外部库。这些外部库可以被简单的用作你和网店集成的第三方系统API的包装，或整个框架


<h3>Related topics</h3>

<a href="{{page.baseurl}}architecture/archi_perspectives/LogicalView_intro.html">Logical view</a>


<a href="https://getcomposer.org/doc/00-intro.md" target="_blank">Composer</a> 

---
layout: default
group: arch-guide
subgroup: Logical View
title: Magento 库
menu_title: Magento 库
menu_order: 3
version: 2.0
github_link: architecture/archi_perspectives/components/arch_libraries.md
redirect_from: /guides/v1.0/architecture/arch_libraries.html
---

<h2 id="m2arch-libraries-overview">Overview 概览</h2>
Magento uses the following types of libraries:
<br/>Magento使用以下类型的库：

*	Magento PHP libraries, which are discussed in the next section
* MagentoPHP库， 下一部分讨论
*	Magento UI libraries, which are located in the <a href="{{ site.mage2000url }}lib/web" target="_blank">lib/web</a> directory
* Magento UI库， 在lib/web目录

	For more information, see <a href="{{ site.mage2000url }}lib/web/css/docs/source/README.md" target="_blank">library documentation on GitHub</a> and <a href="{{page.baseurl}}architecture/view/view-lib.html">View Library</a>.
	<br/>更多信息查看github库文档和视图库
	
*	<a href="{{page.baseurl}}architecture/archi_perspectives/third-party-libs.html">Third-party libraries</a>. These libraries include JavaScript libraries as well as PHP-based ones (including the Zend libraries).
* 第三方库。这些库包含JS库以及基于PHP的（包括zend库）

	Third-party libraries are organized by vendor to be PSR-0 compliant.
  <br/>第三方库通过vendor组织符合PSR-0.

<h2 id="m2arch-libraries-mage">Magento PHP libraries</h2>
<a href="{{ site.mage2000url }}lib/internal/Magento/Framework" target="_blank">Magento PHP libraries</a> include independent libraries of code useful to a Magento application. Each library has minimal dependencies on other library.
<br/>Magento PHP 库包括对Magento应用程序有用的独立库代码。每一个库对其它库拥有最小依赖。

For example:

*	<a href="{{ site.mage2000url }}lib/internal/Magento/Framework/Filesystem" target="_blank">Magento\Framework\Filesystem</a> has PHP libraries for file system operations such as read, write, and directory listing. We provide drivers for <a href="{{ site.mage2000url }}lib/internal/Magento/Framework/Filesystem/Driver/File.php" target="_blank">file</a>, <a href="{{ site.mage2000url }}lib/internal/Magento/Framework/Filesystem/Driver/Http.php" target="_blank">HTTP</a>, <a href="{{ site.mage2000url }}lib/internal/Magento/Framework/Filesystem/Driver/Https.php" target="_blank">HTTPS</a>, and <a href="{{ site.mage2000url }}lib/internal/Magento/Framework/Filesystem/Driver/Zlib.php" target="_blank">Zlib</a>.

* Magento\Framework\Filesystem使用PHP库进行文件系统操作如读、写和列出目录。我们为文件、HTTP、HTTPS和Zlib提供驱动。

*	<a href="{{ site.mage2000url }}lib/internal/Magento/Framework/App" target="_blank">Magento\Framework\App</a> is a special PHP library that is aware of Magento as an application. It represents a greater level of abstraction and provides the following:
* Magento\Framework\App是一个特殊的PHP库它知道Magento作为一种应用程序。它作为更高层抽象提供如下：

	* <a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_and_areas.html">Application areas区域</a>
	* <a href="{{page.baseurl}}extension-dev-guide/routing.html">Routing requests路由请求</a>
	* Application state 应用程序状态


<div class="bs-callout bs-callout-info" id="info">
  <p>Other Magento libraries do not reference <code>Magento\Framework\App</code>.
	<br/>其它库不引用 <code>Magento\Framework\App</code>.
	</p>
</div>

<h2 id="m2arch-related">Related topics</h2>


<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_intro.html">Modules</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_themes.html">Themes</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_translations.html">Language packages</a>


<a href="{{page.baseurl}}architecture/archi_perspectives/third-party-libs.html">Third-party libraries</a>

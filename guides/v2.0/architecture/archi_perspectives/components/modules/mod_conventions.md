---
layout: default
group: arch-guide
subgroup: Components
title: 
menu_title: 模块约定
menu_order: 5
level3_menu_node: level3child
level3_subgroup: modules
version: 2.0
github_link: architecture/archi_perspectives/components/modules/mod_conventions.md
redirect_from: 
  - /guides/v1.0/architecture/modules/mod_conventions.html
  - /guides/v2.0/architecture/modules/mod_conventions.html
---

<h2 id="m2arch-module-conventions-overview"> 概览</h2>


Modules must conform to Magento conventions regarding code location and file names. Keep these conventions in mind when working with or developing modules. 

模块必须符合关于代码位置和文件名称的Magento约定。在使用或开发模块时要记住这些约定

Be sure to research additional Magento conventions, beyond those applicable to modules. For  more information, see <a href="{{page.baseurl}}coding-standards/bk-coding-standards.html">Coding Standards</a>.

研究除了适用于模块的附加Magento约定的更多信息查看<a href="{{page.baseurl}}coding-standards/bk-coding-standards.html">编码标准</a>

<h2 id="m2arch-module-conventions-location"> Module location conventions模块位置约定</h2>

The following table shows the *recommended* location within the Magento file system for specific components.

下面的表格显示在Magneto文件系统特定组件*推荐*的位置

(A module must include a `registration.php` file in its root folder.) 

(一个模块必须在它的根目录包括registration.php文件) 

We refer to a component’s root directory as the top-level directory in which you develop component code. Typically, this directory is located in one of the following directories relative to the Magento root directory:

我们涉及的组件根目录做为你开发组件的顶级目录，特别地这个目录存在于以下相于对Magento根目录的目录

<table>
	<tbody>
		<tr>
			<th>Entity</th>
			<th>Location</th>
		</tr>
		<tr>
			<td>Code base of your custom module</td>
			<td><p><code>&lt;your Magento install dir>/app/code/&lt;Vendor&gt;/&lt;Module&gt;</code></p></td>
		</tr>
		<tr>
			<td colspan="1">Your custom theme files</td>
			<td colspan="1"><code>&lt;<your Magento install dir>/app/design/frontend (storefront themes) or &lt;Module&gt;/&lt;theme&gt;</code></td>
		</tr>
		<tr><td colspan="1">If you want to use a library</td>
			<td colspan="1"><code>&lt;your Magento install dir>/lib/&lt;Vendor_Library&gt;</code></td>
		</tr>
	</tbody>
</table>
<br>
<table>
	<tbody>
		<tr>
			<th>实体</th>
			<th>位置</th>
		</tr>
		<tr>
			<td>你的自定义模块代码基础</td>
			<td><p><code>&lt;你的Magento安装目录>/app/code/&lt;Vendor&gt;/&lt;Module&gt;</code></p></td>
		</tr>
		<tr>
			<td colspan="1">你的自定义主题文件</td>
			<td colspan="1"><code>&lt;<your Magento install dir>/app/design/frontend (storefront themes) or &lt;Module&gt;/&lt;theme&gt;</code></td>
		</tr>
		<tr><td colspan="1">如果你想使用一个库</td>
			<td colspan="1"><code>&lt;your Magento install dir>/lib/&lt;Vendor_Library&gt;</code></td>
		</tr>
	</tbody>
</table>




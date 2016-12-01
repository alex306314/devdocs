---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: 安全概览Security overview
menu_title: 安全
menu_order:
version: 2.0
github_link: architecture/security_intro.md
---

<h2 id="security_intro">安全概览</h2>

Magento 2.0 包含以下安全性的增强：

* <b>Enhanced password management</b>. Magento has strengthened the hashing algorithms (SHA-256) used in password management.

* <b>增加的密码管理</b>。 Magento在密码管理使用了增强的哈希算法(SHA-256)

* <b>Improved prevention of cross-site scripting (XSS) attacks by making escaped data the default</b>. The Magento Framework has adopted conventions that regulate the escaping of data in output. These conventions include the ability to escape  output for HTML pages (HTML, JSON, and JavaScript) and email. Where possible, escaping is transparent to client code. See <a href="{{page.baseurl}}frontend-dev-guide/templates/template-security.html">Security measures against XSS attacks</a> in the Frontend Developer Guide.

* <b>通过默认使用转义数据改进防止跨站脚本攻击</b>。 Magneto框架已经采用控制的数据输出转义约定。这种约定包括转义输出到HTML页面（HTML，JSON和Javascript）和邮件的能力。在可能的情况下，转义代码对客户端代码是透明的。在前端开发者指南查看<a href="{{page.baseurl}}frontend-dev-guide/templates/template-security.html">防止XSS攻击的安全措施</a>

*	<b>More flexible file system ownership and permissions</b>. Starting in version 2.0.6, Magento no longer explicitly sets file system permissions. Instead, we recommend that certain files and directories be writable in a development environment and read-only in a production environment.

* <b>更灵活的文件系统所有权和权限</b>。从版本2.0.6开始，Magento不再明确指定文件系统权限。而我们鼓励某些文件和目录在开发环境可写同时在生产环境只读。

	To provide you with a simple way to restrict access to the file system in production, we provide the flexibility for you to further restrict those permissions using a [umask](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html){:target="_blank"}.

	为了在发布环境给你提供一种简单的方式来限制读取文件系统， 我们提供灵活的深层次控制这些权限通过使用[文件权限掩码](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html){:target="_blank"}.

	查看 [所有权和权限概览]({{page.baseurl}}install-gde/prereq/file-sys-perms-over.html).

	关于详细的在开发和生产环境有关所有权和权限的详细信息查看[在生产和开发环境Magento所有权和权限]({{page.baseurl}}).



* <b>Improved prevention of clickjacking exploits</b>. Magento safeguards your store from clickjacking attacks by using an X-Frame-Options HTTP request header. For more information, see <a href="{{page.baseurl}}config-guide/secy/secy-xframe.html"> X-Frame-Options header</a>.

* <b>增强的防止点击劫持的开发</b>。 Magento通过使用X-Frame-Options HTTP请求头保护你的网店名受clickjacking attacks。详细信息查看<a href="{{page.baseurl}}config-guide/secy/secy-xframe.html"> X-Frame-Options头</a>.

* <b>Use of non-default Magento Admin URL</b>. A simple Magento Admin URL (like `admin` or `backend`) makes it easy to target attacks on specific locations using automated password guessing. To prevent against this type of attack, Magento by default creates a random Admin URI when you install the product. The CLI is provided so that you can  see the password if you forget it. You can also use the CLI to change this URI.  Although the use of a non-default admin URL will not secure the site, its use will help prevent large-scale automated attacks. See <a href="{{page.baseurl}}install-gde/install/cli/install-cli-adminurl.html">Display or change the Admin URI</a> in Configuration Guide for more information.

* <b>使用非默认Magento后台访问URL</b>。使用简单的后台链接（如admin或backend）会比较容易受到指定地址自动密码猜测攻击。为防止这种攻击，在安装系统时Magento默认创建随机的后台URI。如果你忘记了密码可以使用CLI查看，也可以使用CLI修改后台URI。虽然使用非默认后台RUI不会确保站点的安全，但它的使用会帮助防止大规模的自动攻击。在配置指南查看<a href="{{page.baseurl}}install-gde/install/cli/install-cli-adminurl.html">显示或修改后台URI</a>更多信息




<h2>相关主题</h2>
<a href="{{page.baseurl}}config-guide/bk-config-guide.html">配置指南</a>

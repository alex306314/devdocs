---
layout: default
group: arch-guide
subgroup: Components
title: Magento 主题 
menu_title: 主题 
menu_order: 8
version: 2.0
github_link: architecture/arch_perspectives/components/arch_themes.md
redirect_from: /guides/v1.0/architecture/arch_perspectives/themes_intro.html
---

<h2>Magento themes主题</h2>

A <i>theme</i> is a core Magento component whose primary purpose is to control the appearance of your storefront.  Themes use a combination of application elements, such as templates, layouts, styles, and images, and are highly extensible. 

主题是一种核心Magento组件， 主要目的是控制店面外观。主题使用应用程序元素的组合，如模板、布局、样式和图片，都具有高可扩展性。

<b>Custom theme development is one of two main methods of modifying Magento behavior and storefront appearance</b>. (Extending modules is the other primary way, and the main way to tailor Magento behavior.) Themes are the primary way to customize your Magento storefront appearance. Unlike modules, themes do not provide new business features (other than branding and web user experience).

<b>自定义主题开发是修改Magento行为和店面外面的两种主要方式之一</b>（另一种方式是扩展模块，这是剪裁Magento行为的主要方式。） 主题是定制Magento网店外观的主要方式。不同于模块，主题不提供新的业务特征（除了品牌和网站用户体验）

Themes within a Magento installation relate to each other through <i>inheritance</i>, allowing you to customize an existing theme by defining it as a parent theme whose settings can be inherited by any designated child themes. Themes are also divided by area, allowing you to define themes that customize either the storefront or Magento Admin.

Magento系统的主题是通过<i>继承</i>相互联系，允许你定制已经存在的主题通过定义它为父主题，它的配置可以被任何指定的子主题继承。主题也按区域划分，允许你定义主题来定制店面或后台。

Magento 2.0 themes are also characterized by responsive web design. For more information on responsive design, see <a href="{{page.baseurl}}frontend-dev-guide/responsive-web-design/rwd_overview.html">Overview of responsive web design in Magento</a>.

Magento2.0 主题也有自适应网站设计的特点。更多关于自适应设计查看<a href="{{page.baseurl}}frontend-dev-guide/responsive-web-design/rwd_overview.html">Magento自适应网站设计概览</a>.

For detailed information about working with themes, refer to  <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-general.html">Themes</a> in the Frontend Developers Guide.
更多主题信息在前端开发者指南查看<a href="{{page.baseurl}}frontend-dev-guide/themes/theme-general.html">主题</a>

<h3>Theme location主题位置</h3>
 The location of a theme in your Magento installation depends upon how you installed your theme. Magento knows to look in both `vendor` and  `app/design` for themes. In Magento 2.0, each module and theme contain a `registration.php` file, which defines location information. 

在你的Magento系统主题的目录取决于你怎么安装你的主题。Magento知道在vendor和app/design查找主题。在Magento2.0里，每个模块都包含一个定义位置信息的registration.php文件，

 <i>Areas</i> also determine a theme's location. Themes that affect the storefront are placed in the `frontend` area, while themes that affect the Admin panel are placed in `adminhtml` directory. 

 <i>区域</i>也会决定主题的位置。影响店面前端的主题放在frontend区域， 同时影响后台界面的主题放在adminhtml目录。

 <h4>Location of themes in GitHub repository在github仓库主题的目录</h4>
 In the Magento repository on GitHub, themes exist under `app/design/frontend`. For example, you can find the Magento Blank theme at https://github.com/magento/magento2/tree/develop/app/design/frontend/Magento/blank. 

在github Magento仓库里，主题存放在app/design/frontend. 你可以找到blank主题在https://github.com/magento/magento2/tree/develop/app/design/frontend/Magento/blank. 

<h4>Location of themes when installing with Composer 当使用composer安装时主题的位置</h4>

 We recommend using Composer to install your Magento application and components such as modules or themes. Composer places the theme you are installing under  `/vendor`. For example, `vendor/Magento/theme-frontend-blank` is the root directory of the Composer package holding the Blank theme. 

 我们推荐使用Composer来安装你的Magento应用程序和组件如模块或主题。Composer把你安装的主题放在/vendor下面。如vendor/Magento/theme-frontend-blank是Composer包获取的blank主题的根目录。

<h4>Location of custom themes自定义主题的目录</h4>
While developing a theme, place it under `app/design`.  If you've defined the theme for a local project (that is, you intend to install it in one project only),  place it under `app/design`. However, if you decide to sell the theme on Magento Marketplace, follow the instructions given there for uploading. When users download your theme from Magento Marketplace, they will use Composer to install the theme package, and Composer will automatically place it in `vendor`. (Essentially, `/vendor` holds all code that you have not written.)

开发一个主题时把它放在app/design下。如果你是为本地项目定义的主题（也就是你只想装他安装在一个项目），把它放到app/design下， 如果你决定在市场卖你的主题，上传时遵循那的说明。当用户从市场下载你的主题，他们会使用Composer安装主题包，Composer就会自动把它放到vendor里（本质上vendor保存不是你写的所有的代码）

<h3>Default Magento themes 默认Magento主题</h3>

The standard Magento installation provides two default themes: Luma theme (demonstration only) and Blank theme (boilerplate for theme customization).

标准Magento系统提供两个默认主题：Luma主题（仅演示）和Blank主题（定制主题的样板）

* <b>Luma theme</b> is for demonstration purposes only. Do not use it as a parent theme in your installation.  Explore it to better understand Magento themes, but do not base customizations on it. 
* <b>Luma theme</b>仅用于演示目的。在你的系统不要将它做为父主题。探索它来更好的理解Magento主题，但不要基于它进行定制
* <b>Blank theme</b> is provided as a tool to aid your theme development. Use the Magento Blank theme as a basis for custom theme creation. Because Blank theme is built on principles of responsive web design, it makes an excellent starting point for developing responsive Magento themes.
* <b>Blank theme</b> 被提供为一个工具来指定你的主题开发。使用Blank主题做为基础来自定义主题创建。因为Blank主题是构建在自适应网站设计准则上的，它创造了一个开发自适应主题很不错的起点。
    


<h2 id="m2arch-related">相关专题</h2>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_intro.html">Modules</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_libraries.html">Libraries</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_translations.html">Language packages</a>

<a href="{{page.baseurl}}frontend-dev-guide/themes/theme-structure.html">Magento theme structure</a>

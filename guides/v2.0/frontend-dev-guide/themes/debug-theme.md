---
layout: default  
group: fedg
subgroup: A_Themes
title: 定位模板、布局和样式
menu_title: 定位模板、布局和样式
menu_order: 6
version: 2.0
github_link: frontend-dev-guide/themes/debug-theme.md
redirect_from: /guides/v1.0/frontend-dev-guide/themes/debug-theme.html
---

<h2 id="debug-theme-intro">What's in this topic 本主题讲什么</h2>

When you create a Magento theme, you might need to create override files for default theme and module view files. To do so, you must determine which template, layout, and style files Magento uses. This topic describes how to do this.

当你创建一个magento主题，你可能需要为默认主题和模块视图文件创建覆写文件。为了做这些，你必须判断哪个模板、布局和样式文件在使用。此专题详解如何做这些。

**Contents**

* TOC
{:toc}


## Locate templates {#debug-theme-templ} 定位模板

To locate the template that is responsible for a specific part of the storefront or Admin, you can use Magento built-in template hints.

要定位特定部分前端或后台模板，你可以使用内建的模板提示。

To enable template hints: 启用模板提示

1. Click **Stores** > **Configuration** > ADVANCED > **Developer**.

2. In the **Scope** dropdown in the upper-left corner select the view for which you want the template hints.

3. In the **Debug** tab, set **Template Path Hints for storefront** to **Yes**. To enable path hints for Admin set **Template Path Hints for Admin** to **Yes**.
4. To save the changes, click **Save Config** in the upper-right corner.
<p><img src="{{ site.baseurl }}common/images/fdg_debug_theme.png" alt="Enabling template hints"></p>

Now that you have enabled template hints, reload the page that you want to modify, and review the path for the template file or files that template hints show.

现在你已经启用模板提示，重载要修改的页面，查看模板文件或模板提示显示文件

For example, here is how a storefront category page looks with enabled template hints:
<p><img src="{{ site.baseurl }}common/images/theme_debug2.png" alt="A storefront page with enabled template hints"></p>

例如这是店面分类页在启用模板提示后：

In this example mini shopping cart page element is defined by the `<Magento_Checkout_module_dir>/view/frontend/templates/cart/minicart.phtml` template:

在这个示例购物车页元素被定义在`<Magento_Checkout_module_dir>/view/frontend/templates/cart/minicart.phtml`模板

<p><img src="{{ site.baseurl }}common/images/theme_debug3.png" alt="A hint with template name for minishopping cart"></p>
(the template name is above the element模板名称在元素上面)

Here is how Customers page looks with enabled template hints in Admin:
这是在后台开启模板提示的样式。
<p><img src="{{ site.baseurl }}common/images/theme_debug5.png" alt="Admin page with enabled template hints"></p>

Alternatively, you can perform a text search in the file system by using system generated titles, CSS class names, block titles, labels, or links text as search terms.
For example, using a browser debug tool, you can define that the minicart block css class is `minicart-wrapper`.
或者你可以在文件系统使用系统生成的标题、CSS类名执行文本搜索，使用一个浏览器调试工具，你可以确定购物车模块CSS类是`minicart-wrapper`.
<p><img src="{{ site.baseurl }}common/images/theme_debug4.png" alt="Firebug displaying html"></p>

A search through the app directory for occurrences of "minicart-wrapper" in `.phtml` files returns the `app/code/Magento/Checkout/view/frontend/templates/cart/minicart.phtml` template.

搜索app目录发现"minicart-wrapper"在 `.phtml`文件返回`app/code/Magento/Checkout/view/frontend/templates/cart/minicart.phtml`模板

Since it is not recommended to edit the default files, you need to add overriding files if you want to customize the template. For details about overriding templates please refer to <a href="{{page.baseurl}}frontend-dev-guide/templates/template-walkthrough.html">Customizing Theme Template</a>.

不推荐直接修改默认文件。如果你想定制模板需要添加覆写文件。关于覆写模板详情查看定制主题模板。

## Locate layouts {#debug-theme-layout} 定位布局
Just like templates, layouts are saved on a per-module basis. You can easily locate the layout file by determining in which module the templates for the element you are interested in reside in. To locate the template, you can use Template Hints or text search in the app directory, as described previously .

像模板一样，布局保存在每个模块基础。你可很容易定位布局通过确定你感兴趣的元素在哪个模块模板。要定位模板，你可使用模板提示或在app目录文本搜索像之前提到过的。

After you have determined the module, you can search for the layout in the following locations:
在确定了模块后，可以在以下位置搜索布局：

1. `<current_theme_dir>/<Namespace>_<Module>/layout/`
2. `<parent_theme(s)_dir>/<Namespace>_<Module>/layout/`
3. `<module_dir>/frontend/layout/`
4. `<module_dir>/view/base/layout/`

There is no straightforward algorithm how to define at once the exact layout file, but in most cases layout file names are self descriptive. Also you can search them for mentions of the corresponding templates.

没有直接的算法来一次确定准确的布局文件，但大多数情况布局文件的名称是自描述的。当然你可以搜索他们使用对应的模板。

Example:

Let's say you need to locate the layout that is responsible for displaying mini shopping cart on the storefront, when the Blank theme by Magento is applied for the store view.

假设你需要定位负责显示购物车的布局文件，当blank主题被应用。

Using the Template Hints we determine that the template is `app/code/Magento/Checkout/view/frontend/templates/cart/minicart.phtml`, and in the path, we see that it belongs to the `Magento_Checkout` module.

使用模板提示我们确定模板是`app/code/Magento/Checkout/view/frontend/templates/cart/minicart.phtml`在路径中我们可看到它属于Magento_Checkout模块

Let's search for the layout following the fallback scheme: 让我们按回调机制查找布局

1. Check the `app/design/frontend/Magento/blank/Magento_Checkout/` layout. To locate the required layout, search this directory for occurrences of the template name, " minicart.phtml ". No matching file is found, so we proceed to the next fallback level, which is the parent theme layouts.
<br/>
检查 `app/design/frontend/Magento/blank/Magento_Checkout/`布局。定位需要的布局，搜索这个目录中符合模板名称" minicart.phtml "。没查到对应的文件，所以我们进入下一级回调，父主题布局
2. We can find the info about parent theme in a theme configuration file `theme.xml`, the parent theme name is specified there in the `<parent></parent>` node. In the `app/design/frontend/Magento/blank/theme.xml` there's no `<parent>` node, which means the Blank theme has no parents. So we should search on the next fallback level which is the module layouts.
<br/>
我们可以在theme.xml文件找到关于父主题的信息。父主题名称被指定在 `<parent></parent>`节点。在blank没有parent节点，意味着blank没有父主题。所以我们应该查找下一级模块布局
3. The Magento_Checkout layouts are located in `app/code/Magento/Checkout/view/frontend/layout/`. After searching this directory for occurrences of "`minicart.phtml`", we define that the layout we are looking for is `app/code/Magento/Checkout/view/frontend/layout/default.xml`.
<br/>
Magento_Checkout布局定位在`app/code/Magento/Checkout/view/frontend/layout/`。 在搜索符合"`minicart.phtml`"之后。确定我们要找的布局是`app/code/Magento/Checkout/view/frontend/layout/default.xml`.

After you located the necessary layout file, you can create your custom layout file with the corresponding name in your theme folder to add <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">extending</a> or <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-override.html" target="_blank">overriding</a> content. Please see <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html">Customizing Theme Layouts</a> for more details.

在定位需要的布局文件之后，你在以在你们主题目录创建对应的名称的自定义布局文件，来添加扩展或覆写内容，更多信息请查看定制主题布局

## Locate styles {#debug-theme-style} 定位样式
To locate a CSS rule that is applied to a certain element, find the template for the page that contains the element. Or you can use browser debugging tools, to locate the class name.
After you find the class name, use text search in the theme and module styles directories to locate the `.less` or `.css` file that defines the class. Perform the search according to the following fallback scheme:

要定位一个CSS应用到确定元素的规则，查找包含那个元素的页面模板。或你可以使用浏览器调试工具，来定位类名。之后使用文件搜索在主题和模块样式目录来定位.less或.css文件，根据如下回调机制执行检索：

2. Theme styles `<current_theme_dir>/web/css/`
2. Module theme styles `<current_theme_dir>/<Namespace>_<Module>/web/css/`
3. Parent theme styles `<parent_theme_dir>/web/css/`
4. Parent theme Module styles `<parent_theme_dir>/<Namespace>_<Module>/web/css/`
5. Module styles for the `frontend` area `<module_dir>/view/frontend/web/css/`
6. Module styles for the `base` area `<module_dir>/view/base/web/css/`

Example:

Let's find the file defining on the CSS classes used for displaying the mini shopping cart on the storefront, when the Blank theme by Magento is applied for the store view.

让我们查找用来显示购物车定义在CSS类上的文件，当blank主题用于店面视图。

In the mini shopping cart template `app/code/Magento/Checkout/view/frontend/templates/cart/minicart.phtml` the top level element has `minicart-wrapper` class.
在购物车模板顶层元素有类`minicart-wrapper` 

So, let's search for occurrences of "`minicart-wrapper`" in according to the fallback scheme:

让我们查询符合"`minicart-wrapper`"的文件根据回调机制：

1. Search in `app/design/frontend/Magento/blank/web/css`, the search returns no results.
2. Search in `app/design/frontend/Magento/blank/Magento_Checkout/web/css`.The "`minicart-wrapper`" style is defined in `app/design/frontend/Magento/blank/Magento_Checkout/web/css/source/module/_minicart.less`

<p>After you determine which <code>.css</code> or <code>.less</code> file defines the class, you can override the default class definition in your custom <code>.css</code> or <code>.less</code> files.  For details, see <a href="{{page.baseurl}}frontend-dev-guide/css-topics/css-themes.html">CSS in themes</a>.
<br/>
在你确定哪个.css或less文件定义了类，你可以在你的自定义css或less文件覆写默认的类定义。
</p>

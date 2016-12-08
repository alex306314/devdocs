---
layout: default
group: fedg
subgroup: A_Themes
title: 应用和设置网店主题
menu_title:应用和设置网店主题
version: 2.1
menu_order: 4
github_link: frontend-dev-guide/themes/theme-apply.md
---

<h2 id="theme-apply-overview">What's in this topic 这个专题有什么？</h2>

The topic describes how to apply a theme for your store. This is a required step if you want a theme to be used on a storefront. 
Also, it gives information how to add a theme independent logo for your store.

此专题描述如何给你的网店应用主题。如果你想让网店应用主题这就是必需的步骤。同时它提供信息如何向网店添加主题独立的LOGO

**Contents**:

* TOC
{:toc}


## Prerequisites 预备知识

Make sure that you [set](#{{site.gdeurl21}}config-guide/cli/config-cli-subcommands-mode.html) your Magento application to the developer [mode]({{site.gdeurl21}}config-guide/bootstrap/magento-modes.html).

确保你设置了系统为开发者模式

## Apply a theme {#theme-apply-apply} 应用一个主题
After you <a href="{{site.gdeurl21}}frontend-dev-guide/themes/theme-create.html">add your theme to the file system</a>, you can apply it to your store. You apply a theme in Admin.

在添加你的主题到文件系统后，你可以为网店应用它，你在后台管理界面应用一个主题。

To apply a theme:应用一个主题：

1. In Admin, go to **CONTENT** > **Design** > **Configuration**. A Design Configuration page opens. It contains a grid with the available configuration scopes. For example: <br><img src="{{site.baseurl}}common/images/design_conf1.png" alt="Design Configuration page"><br/>
在管理界面，到**CONTENT** > **Design** > **Configuration**。开打Design Configuration页面。它包含可使用配置范围表格。如<br><img src="{{site.baseurl}}common/images/design_conf1.png" alt="Design Configuration page">
2. In the configuration record corresponding to your store view, click **Edit**.<br/>
在你的网店视图对应配置记录，点击 **Edit**
4. On the **Default Theme** tab, in the **Applied Theme** drop-down, select your newly created theme.<br/>在标签 **Default Theme**，在下拉**Applied Theme**中，选择你的新主题。
5. Click **Save**. 点**Save**
6. If caching is enabled, <a href="#theme-apply-clear">clear the cache</a>. <br/>如果开启了缓存，清空缓存 
6. To see your changes applied, reload the store front pages.<br>重载网店页面查看应用的修改


## Add a design exception {#theme-apply-except} 添加一个设计例外
Design exceptions enable you to specify an alternative theme for particular user-agents, instead of creating a separate store views for them.
To add a design exception:

设计异常使你可以为特定用户媒介指定供选择的主题，而不是创建分开的店面视图。来添加一个设计异常：


2. In Admin, go to **CONTENT** > **Design** > **Configuration**
2. In the configuration record corresponding to your store view, click **Edit**. 
4. On the **Design Rule** tab, click **Add New User Agent Rule**.
5. In the **Search String** box specify the user-agent using either normal strings or regular exceptions (PCRE). In the **Theme Name** drop-down list select the theme to be used for matching agent.
6. Click **Save**.
7. If caching is enabled, <a href="#theme-apply-clear">clear the cache</a>. 
6. To see your changes applied, reload the store front pages.


## Add a theme-independent logo {#theme-apply-logo} 添加主题独立的LOGO
You might want to set a permanent store logo that displays on the store front no matter what theme is applied.
To add a permanent theme-independent logo:

你可能想设置一个永久的网店LOGO显示在店面而不管应用哪个主题。来添加一个主题独立的永久LOGO：

2. In Admin, go to **CONTENT** > **Design** > **Configuration**
2. In the configuration record corresponding to your store view, click **Edit**. 
3. Expand the **Header** tab.
4. In the **Logo Image** field browse to the logo file saved in your file system.
6. Upload the file.
5. Optionally, specify the desired width, height, and the alternative text for the logo in the corresponding fields.
7. Click **Save**.
7. If caching is enabled, <a href="#theme-apply-clear">clear the cache</a>. 
8. To see your changes applied, reload the store front pages.

The logo you add here is stored in the `/pub/media/logo/default/` directory.
你在这添加的LOGO被保存在`/pub/media/logo/default/` 目录

<div class="bs-callout bs-callout-warning" id="warning">
  <p>To delete the permanent logo, go to the same location, and click the "Delete image" icon in the bottom left corner of the logo preview.<br>相删除永久LOGO，到相同位置点击左下角LOGO预览的"Delete image"图标</p>
</div>

## Clear the cache {#theme-apply-clear} 清除缓存
If caching is enabled in Magento Admin, you must clear the cache after you apply the theme, add a design exception, add a logo, and perform other tasks.

如果后台启用了缓存，在应用主题、添加设计例外、添加LOGO和执行其它任务后必须清除缓存，

A system message notifies you that invalidated cache types must be refreshed.

系统信息提示你无效缓存类型就必须刷新

1.	Click **System** > **Cache Management**.
2.	Clear the invalid cache types.

## Troubleshooting (if the changes do not get applied) 问题（如果修改没生效）

If the changes you configure in the Admin are not applied after you clear the cache and reload the page, delete all files in the `pub/static/frontend` and `var/view_preprocessing` directories, then reload the pages. You can delete the files manually or run the `grunt clean:<theme_name>` command in CLI. For details about using Grunt in Magento see [Installing and configuring Grunt]({{site.gdeurl21}}frontend-dev-guide/css-topics/css_debug.html#grunt_prereq).

如果你在后台做的设置修改在你清除了缓存并重新加载页面之后没有生效，删除`pub/static/frontend` and `var/view_preprocessing`目录所有文件，然后重载页面。你可以手动删除或运行命令`grunt clean:<theme_name>`。更多关于grunt查看[安装和配置Grunt]({{site.gdeurl21}}frontend-dev-guide/css-topics/css_debug.html#grunt_prereq).


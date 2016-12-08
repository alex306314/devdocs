---
layout: default
group: fedg
subgroup: A_Themes
title: 设置产品视频
menu_title: 设置产品视频
menu_order: 8
version: 2.0
github_link: frontend-dev-guide/themes/product-video.md
---


## What's in this topic 本专题讲什么

In Magento 2 on product pages you can add video from external resources (currently, from [YouTube](https://youtube.com) and [Vimeo](https://vimeo.com/)). Video is [added in Admin](http://docs.magento.com/m2/2.0/ee/user_guide/catalog/product-video.html?Highlight=product%20video) when creating or editing a product. 
Certain product video options can be set in the `config.xml` configuration file. These settings are not theme-specific.

在Magento2 产品页面可以从外部资源（youtube和vimeo）添加视频。视频是在后台添加当新建或编辑产品时。指定产品视频参数可以在config.xml配置文件设置。这些配置不是主题特有的。

## Configure product video options 配置产品视频的参数

You can set the following product video options:
你可以设置以下产品视频参数 

<table>
  <tbody>
    <tr>
      <th>Option</th>
      <th>Description</th>
      <th colspan="1">Type</th>
      <th>Default</th>
    </tr>
    <tr>
      <td colspan="1">
        <code>play_if_base</code>
      </td>
      <td colspan="1">Play automatically on page load.页面加载自动播放</td>
      <td colspan="1">
        Boolean
      </td>
      <td colspan="1">
        0 <br>
(video is not played on page load)
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>show_related</code>
      </td>
      <td colspan="1">Display related videos.</td>
      <td colspan="1">
Boolean
           
      </td>
<td>
0 <br>
(related videos are not displayed)
</td>
    </tr>
    <tr>
      <td colspan="1">
        <code>video_auto_restart</code>
      </td>
      <td colspan="1">Auto re-play video.</td>
      <td colspan="1">
Boolean
           
      </td>
<td>
0 <br>
(video is not automatically replayed)
</td>
    </tr>
  </tbody>
</table>

The options are set in the `config.xml` of you custom module. 
参数被设定在你的自定义模块的config.xml文件

Example:

{%highlight xml%}
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <catalog>
            <product_video>
                <play_if_base>1</play_if_base>
                <show_related>1</show_related>
                <video_auto_restart>1</video_auto_restart>
            </product_video>
        </catalog>
    </default>
</config>
{%endhighlight%}

For the sake of compatibility, upgradability and easy maintenance, do not edit the default Magento code. Instead add your customizations in a separate module.

为了兼容性、升级性和易于维护。不要编辑默认代码。而是在单独的模块添加自定义。
---
layout: default
group: fedg
subgroup: A_Themes
title: 设置主题图片属性
menu_title: 设置主题图片属性
menu_order: 4
version: 2.0
github_link: frontend-dev-guide/themes/theme-images.md
---

## What's in this topic 这个专题讲什么##

The properties of product images used on the storefront are stored in the `view.xml` configuration file. This topic provides all details about what properties are available and how to configure them.

在店页使用的系统图片属性被存储在view.xml配置文件。这个专题提供所有关于有哪些可用属性和如何设置他们。

The properties for the images displayed on the product pages are defined by the gallery widget options. The options of the widget can be configured in the theme `view.xml` as well. For more details, view the [Gallery widget]({{page.baseurl}}javascript-dev-guide/widgets/widget_gallery.html) topic.

在系统页面上显示的图片属性被部件库属性定义。部件属性也可以在view.xml配置，更多信息查看部件库

<h2 id="view_xml_structure">Configure image properties in view.xml 在view.xml配置图片属性</h2>

The conventional location of `view.xml` for a theme is: 一般主题的view.xml文件的目录在：
{% raw %}
	<theme_dir>/etc/view.xml
{% endraw %}

For example, here is the `view.xml` of the Magento Blank theme: <a href="{{site.mage2000url}}app/design/frontend/Magento/blank/etc/view.xml" target="_blank"><code>app/design/frontend/Magento/blank/etc/view.xml</code></a>.

如这是Blank主题的view.xml文件app/design/frontend/Magento/blank/etc/view.xml

In `view.xml`, image properties are configured in the scope of `<images module="Magento_Catalog">` element:

在view.xml图片属性在`<images module="Magento_Catalog">`元素内设置

{% highlight xml %}
<images module="Magento_Catalog">
...
<images/>
{% endhighlight xml %}

Image properties are configured for each image type defined by the `id` and `type` attributes of the `<image>` element:

每种图片类型通过定义`<image>`元素的id和type属性设置图片属性

{% highlight xml %}
<images module="Magento_Catalog">
	<image id="unique_image_id" type="image_type">
	...
	</image>
<images/>
{% endhighlight xml %}

<br>
The following table describes the attributes in detail:

下面详细介绍属性：
<table>
  <tbody>
    <tr>
      <th>Attribute</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>
        <code>
          id
        </code>
      </td>
      <td>
        string
      </td>
      <td>
        <p>Image identifier. Unique in the scope of theme. 图片标识符。在主题范围内唯一</p> <p>
Can have any value, but in out-of-the- box Magento themes <code>id</code>'s are meaningful and describe the location of an image. <br/>可以是任何值，但在Magento默认主是id是有意义的描述图片的位置</p><p> For example, the <code>id</code> value for images of cross-sell products displayed in a shopping card is <code>cart_cross_sell_products</code>.
<br/>如：交叉销售产品的图片ID值显示在购物卡上是<code>cart_cross_sell_products</code>.
</p> <p><code>id</code>'s are used in <code>.phtml</code> templates for defining the type and properties of images displayed in each particular location on a particular page.<br/>ID被用在.phtml模板文件来定义显示在指定页面的每个指定位置的图片类型和属性</p>
      </td>
    </tr>
    <tr>
      <td>
        <code>
          type
        </code>
      </td>
      <td>
        string
      </td>
      <td>
        The type of the images defined by the specified <code>id</code>. Allowed values:
<ul>
<li><code>image</code> - corresponds to the Base Image role in the Magento Admin</li>
<li><code>small_image</code> - corresponds to the Small Image role in the Magento Admin</li>
<li><code>swatch_image</code> - corresponds to the Swatch Image role in the Magento Admin</li>
<li><code>swatch_thumb</code> - corresponds to the Swatch Image role in the Magento Admin. </li>
<li><code>thumbnail</code> - corresponds to the Thumbnail Image role in the Magento Admin</li>
</ul>

      </td>
    </tr>
</tbody>
</table>

The following picture illustrates how image roles for product images are specified in the Magento Admin:<br/>下图显示在后台怎么指定产品图片的图片角色：
<img src="{{site.baseurl}}common/images/fdg_theme_bck.png" alt="Setting image role in Magento Admin">


Image properties are defined by the corresponding elements, for example:图片通过对应元素定义如：

{% highlight xml %}
<images module="Magento_Catalog">
    <image id="unique_image_id" type="image">
        <width>100</width> <!-- Image width in px --> 
        <height>100</height> <!-- Image height in px -->
    </image>
</images>
{% endhighlight xml %}

<br>

The following table contains the list of all properties which can be configured:下表包含所有可配置属性列表：
<table>
  <tbody>
    <tr>
      <th>
        Element
      </th>
      <th>
        Type
      </th>
      <th>
        Description
      </th>
      <th>
        Required
      </th>
    </tr>
    <tr>
      <td>
        <code>width</code>
      </td>
      <td>
        integer
      </td>
      <td>
        Image width in pixels.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>height</code>
      </td>
      <td>
        integer
      </td>
      <td>
        Image height in pixels.
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>constrain 约束</code>
      </td>
      <td>
        boolean
      </td>
      <td>
        If set to <code>true</code>, images that are smaller than
        required by the configuration, are not enlarged. Default
        value: <code>true</code>.
        如果设为true, 需要的图片比设置小，则不会放大。默认为true
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>aspect_ratio 长宽比</code>
      </td>
      <td>
        boolean
      </td>
      <td>
        If set to <code>true</code>, proportions of images are not
        changed even if required by the configuration. Default
        value: <code>true</code>.
        如果为true, 图片比例不会改变即使是配置参数需要，默认为true
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>frame</code>
      </td>
      <td>
        boolean
      </td>
      <td>
        If set to <code>true</code>, images are not cropped.
        Default value: <code>true</code>. Applied only if
        <code>aspect_ratio</code> is set to <code>true</code>.
        如果为true图片不会被裁切。默认true. 仅当aspect_ratio长宽比为true时才生效
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>transparency 透明度</code>
      </td>
      <td>
        boolean
      </td>
      <td>
        If set to <code>true</code>, the transparent background of
        images is saved. If is set to <code>false</code>, images
        have the white background (by default). You can set the
        color for the background using the <code>background</code>
        parameter. Default value: <code>true</code>.
        如果设为true. 图片透明背景被保存。如果false，默认的图片有白色背景。你可使用background设定背景色。默认true
      </td>
      <td>
        Optional
      </td>
    </tr>
    <tr>
      <td>
        <code>background 背景</code>
      </td>
      <td>
        string
      </td>
      <td>
        The color for the images background. Not applied to images
        with transparency, if <code>transparency</code> is set to
        <code>true</code>. Format: "[, , ]", e.g.: "[255,
        255, 255]".
        图片背景色。如果图片是透明的就不会生效。格式"[, , ]"，如"[255,
        255, 255]"
      </td>
      <td>
        Optional
      </td>
    </tr>
  </tbody>
</table>

#### Resize catalog images 调整产品目录图片
Generally, product images are cached while saving the product. However, the `magento catalog:images:resize` command enables you to resize all images for display on your storefront. Situations where this could be necessary might be:

一般在保存产品时产品图片会被缓存。而`magento catalog:images:resize`这个命令使你可以调整所有店面显示的图片大小。以下情形有必要的：

* After you import products, which might have images of various sizes当你导入可能会有多种尺寸的图片的产品后
* If images were resized or deleted manually from cache  如果图片被手动调整大小或从缓存删除

Each image assigned to a product must be resized in accordance with image metadata defined in a module's <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-create.html#fedg_create_theme_how-to-images">`view.xml`</a> configuration file. After resizing an image, its resized copy is stored in the cache (`/pub/media/catalog/product/cache` directory). Magento serves storefront images from cache.

每个指定到产品的图片都必须调整大小和模块的view.xml配置文件定义的图片元数据一致。调整图片大小后，调整过的副本会被保存在缓存(`/pub/media/catalog/product/cache` 目录)。Magento从缓存给店面提供图片。

Command usage: 命令使用

`php <magento install dir>/bin/magento catalog:images:resize`

This command has no arguments or options. A progress indicator displays while the command runs.

这个命令没有参数或属性。运行这个命令时会显示一个进度指示器

The message `Product images resized successfully` displays to confirm the command succeeded.

显示`Product images resized successfully`信息来确认命令运行成功。
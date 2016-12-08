---
layout: default
group: fedg
subgroup: B_Layouts
title: 布局指令
menu_title: 布局指令
menu_order: 2
version: 2.0
github_link: frontend-dev-guide/layouts/xml-instructions.md
---

<h2 id="fedg_layout_xml-instruc_overview">What's in this topic专题内容</h2>


Changing layout files is one of the two possible ways to customize page layout in Magento (the second way is altering templates). 
To change the page wireframe, modify the <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html#layout-types-page" target="_blank">page layout</a> files; all other customizations are performed in the <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html#layout-types-conf" target="_blank">page configuration</a> or <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html#layout-types-gen" target="_blank">generic layout</a> files. 

修改布局文件是两种自定义页面布局的方式之一（第二种是改变模板）
改变页面线框，修改页面布局文件，所有其它定制在页面配置中执行或一般的布局文件

Use layout instructions to: 使用布局指令来：


*  move a page element to another parent element移动页面元素到另一个父元素
*  add content 添加内容
*  remove a page element 移除页面元素
<p></p>

The basic set of instructions is the same for all types of layout files. This article describes these basic instructions; for details about how they are used in particular layout file type, please refer to the <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html" target="_blank">Layout file types</a> article.

基本的指令集对所有布局类型文件是一样的。此文描述这些基本指令，关于在特定布局文件类型它们如何被使用详细信息，请查看布局文件类型文章

<h2 id="fedg_layout_xml-instruc_ex">Common layout instructions 通用布局指令</h2>

Use the following layout instructions to customize your layout:
使用下面的布局指令来自定义你的布局：

*  <a href="#fedg_layout_xml-instruc_ex_block"><code>&lt;block></code></a>
*  <a href="#fedg_layout_xml-instruc_ex_cont"><code>&lt;container></code></a>
*  <a href="#fedg_xml-instrux_before-after"><code>before</code> and <code>after</code> attributes</a>
*  <a href="#fedg_layout_xml-instruc_ex_act"><code>&lt;action></code></a>
*  <a href="#fedg_layout_xml-instruc_ex_ref"><code>&lt;referenceBlock></code> and <code>&lt;referenceContainer></code></a>
*  <a href="#fedg_layout_xml-instruc_ex_mv"><code>&lt;move></code></a>
* <a href="#fedg_layout_xml-instruc_ex_rmv"><code>&lt;remove&gt;</code></a>
*  <a href="#fedg_layout_xml-instruc_ex_upd"><code>&lt;update&gt;</code></a>
*  <a href="#argument"><code>&lt;argument&gt;</code></a>

<h3 id="fedg_layout_xml-instruc_ex_block">&lt;block 区块></h3>

Defines a block. 定义一个区块

<p><b>Details:</b> A block is a unit of page output that renders some distinctive content – a piece of information, a user interface element – anything visually tangible for the end-user.
Blocks employ templates to generate HTML. Examples of blocks include a category list, a mini cart, product tags, and product listing.
<br>
一个区块是页面输出的一个单位渲染一些不同的内容-一块信息、一个用户界面元素——任何对终端用户看得见的。区块使用模板生成HTML。区块实例包括分类列表、微型购物车、产品标签、产品列表
</p>

<table>
   <tbody>
      <tr>
         <th>Attribute</th>
         <th>Description</th>
         <th>Values</th>
         <th>Required?</th>
      </tr>
      <tr class="even">
         <td>class</td>
         <td>Name of a class that implements rendering of a particular block. An object of this class is responsible for actual rendering of block output.
         <br/>
         实现渲染特定区块的类名。这个类的一个对象负责实际的区块输出渲染
         </td>
         <td>class name</td>
         <td>yes</td>
      </tr>
      <tr class="odd">
         <td>name</td>
         <td>Name that can be used to address the block to which this attribute is assigned. The name must be unique per generated page. If not specified, an automatic name will be assigned in the format <code>ANONYMOUS_<em>n</em></code>
         <br>
         名称可用于寻址分配此属性的区块。每个生成的页面这个名称必须唯一。如果未指定，将会分配一个<code>ANONYMOUS_<em>n</em></code>格式的自动名称
         </td>
         <td>0-9, A-Z, a-z, underscore (_), period (.), dash (-). Should start with a letter. Case-sensitive.</td>
         <td>no</td>
      </tr>
      <tr class="even">
         <td>before</td>
         <td><p>Used to position the block</p> before an element under the same parent. The element name or alias name is specified in the value. Use dash (-) to position the block before all other elements of its level of nesting. See <a href="#fedg_xml-instrux_before-after">before and after attributes</a> for details.
         <br/>
         用来放置一个区块到相同父级元素之前。被指定的值是元素名称或别名。使用破折号将区块放置到基嵌套层级所有其它元素之前。详细查看before 和 after属性
         </td>
         <td>Possible values: element name or dash (-)</td>
         <td>no</td>
      </tr>
      <tr class="odd">
         <td>after</td>
         <td>Used to position the block after an element under the same parent. The element name or alias name is specified in the value. Use dash (-) to position the block after all other elements of its level of nesting. See <a href="#fedg_xml-instrux_before-after">before and after attributes</a> for details.
         <br>   
         用于放置一个区块到一个相同父级元素之后。值是元素名或别名。使用破折号将区放置到嵌套层级所有其它元素之后。
         </td>
         <td>Possible values: element name or dash (-)</td>
         <td>no</td>
      </tr>
      <tr class="even">
         <td>template</td>
         <td>A template that represents the functionality of the block to which this attribute is assigned.
         一个模板代表此属性被分配到的区块的功能
         </td>
         <td>template file name</td>
         <td>no</td>
      </tr>
      <tr class="odd">
         <td>as</td>
         <td>An alias name that serves as identifier in the scope of the parent element.
         <br/>
        别名用作在父元素范围内的标识符。
         </td>
         <td>0-9, A-Z, a-z, underscore (_), period (.), dash (-). Case-sensitive.</td>
         <td>no</td>
      </tr>
      <tr class="odd">
         <td>cacheable</td>
         <td>Defines whether a block element is cacheable. This can be used for development purposes and to make needed elements of the page dynamic. 
         <br/>
         定义区块元素是否可缓存。这个可用于开发目的，使页面所需元素动态。
         </td>
         <td><code>true</code> or <code>false</code></td>
         <td>no</td>
      </tr>
   </tbody>
</table>

To pass parameters use the <a href="#argument">`<argument></argument>`</a> instruction. 

传递参数使用<argument></argument>指令

<h3 id="fedg_layout_xml-instruc_ex_cont">&lt;container 容器></h3>
A structure without content that holds other layout elements such as blocks and containers.
<p><b>Details:</b> A container renders child elements during view output generation. It can be empty or it can contain an arbitrary set of <code>&lt;container></code> and <code>&lt;block></code> elements.

没有包含其它布局元素如区块和容器的内容的结构。<p>详细：一个容器在视图输出生成时渲染子元素。它可以是空或可以包含任意容器和区块元素集合</p>

<table>
   <tbody>
      <tr>
         <th>Attribute</th>
         <th>Description</th>
         <th>Values</th>
         <th>Required?</th>
      </tr>
      <tr class="even">
         <td>name</td>
         <td>A name that can be used to address the container in which this attribute is assigned. The name must be unique per generated page.
         <br/>
         名称可用于确定分配到此属性的容器是哪一个。每个生成的页面名称必须是唯一的。
         </td>
         <td>A-Z, a-z, 0-9, underscore (_), period (.), dash (-). Should start with a letter. Case-sensitive.</td>
         <td>yes</td>
      </tr>
      <tr class="odd">
         <td>label</td>
         <td>An arbitrary name to display in the web browser.显示到网页浏览器的任意名称</td>
         <td>any</td>
         <td>no</td>
      </tr>
      <tr class="even">
         <td>before</td>
         <td>Used to position the container before an element under the same parent. The element name or alias name is specified in the value. Use dash (-) to position the block before all other elements of its level of nesting. See <a href="#fedg_xml-instrux_before-after">before and after attributes</a> for details.
         <br/>
         放置容器到一个相同父级元素之前。值是元素名或别名。使用破折号放置区块到它的嵌套层次所有其它元素之前。
         </td>
         <td>Possible values: element name or dash (-).</td>
         <td>no</td>
      </tr>
      <tr class="odd">
         <td>after</td>
         <td>Used to position the container after an element under the same parent. The element name or alias name is specified in the value. Use dash (-) to position the block after all other elements of its level of nesting. See <a href="#fedg_xml-instrux_before-after">before and after attributes</a> for details.</td>
         <td>Possible values: element name or dash (-).</td>
         <td>no</td>
      </tr>
      <tr class="even">
         <td>as</td>
         <td>An alias name that serves as identifier in the scope of the parent element.</td>
         <td>0-9, A-Z, a-z, underscore (_), period (.), dash (-). Case-sensitive.</td>
         <td>no</td>
      </tr>
      <tr class="odd">
         <td>output</td>
         <td>Defines whether to output the root element. If specified, the element will be added to output list. (If not specified, the parent element is responsible for rendering its children.)
         <br/>
         定义是否输出根元素。如果已设置， 这个元素会被添加到输出列表。（如果没有设置。父元素负责渲染它的子级）
         </td>
         <td>Any value except the obsolete <code>toHtml</code>. Recommended value is <code>1</code>.</td>
         <td>no</td>
      </tr>
      <tr class="even">
         <td>htmlTag</td>
         <td>Output parameter. If specified, the output is wrapped into specified HTML tag.
         <br/>
         输出参数。如果设置。输出会被包进指定HTML标签
         </td>
         <td>Any valid HTML 5 tag.</td>
         <td>no</td>
      </tr>
      <tr class="odd">
         <td>htmlId</td>
         <td>Output parameter. If specified, the value is added to the wrapper element. If there is no wrapper element, this attribute has no effect.
         <br/>
         输出参数，如果设置。这个值会被添加到包装元素。如果没有设置包装元素，这个属性不起作用
         </td>
         <td>Any valid HTML 5 <code>&lt;id></code> value.</td>
         <td>no</td>
      </tr>
      <tr class="even">
         <td>htmlClass</td>
         <td>Output parameter. If specified, the value is added to the wrapper element. If there is no wrapper element, this attribute has no effect.
         <br/>
         输出参数。如果设置。这个值会被添加到包装元素。如果没有包装元素，这个属性不起作用
         </td>
         <td>Any valid HTML 5  <code>&lt;class></code> value.</td>
         <td>no</td>
      </tr>
   </tbody>
</table>

Sample of usage in layout: 布局使用示例：
{%highlight xml%}
...
<container name="div.sidebar.additional" htmlTag="div" htmlClass="sidebar sidebar-additional" after="div.sidebar.main">
    <container name="sidebar.additional" as="sidebar_additional" label="Sidebar Additional"/>
</container>
...
{%endhighlight xml%}

This would add a new column to the page layout. 这样会在页面布局添加一个新列。


<h3 id="fedg_xml-instrux_before-after">before and after attributes</h3>
<p>To help you to position elements in a specific order suitable for design, SEO, usability, or other requirements, Magento software provides the <code>before</code> and <code>after</code> layout attributes.
<br/>
为了适应设计、SEO、使用性或其它需要帮助你按指定顺序放置元素，Magento软件提供before和after布局属性
</p>
<p>These optional attributes can be used in layout XML files to control the order of elements in their common parent.

这些可选属性可用在布局xml文件来控制有共同父级的元素的顺序。

The following tables give a detailed description of the results you can get using the <code>before</code> and <code>after</code> attributes. The first table uses a block a as positioned element.

下表是使用before和after属性你可获得的结果的详细介绍。每一个表使用区块a作为定位元素

<table>
   <tbody>
      <tr>
         <th>Attribute</th>
         <th>Value</th>
         <th>Description</th>
      </tr>
      <tr class="even">
         <td>before</td>
         <td>Dash (-)</td>
         <td>The block displays before all other elements in its parent node.区块显示在它父节点里所有其它元素之前</td>
      </tr>
      <tr class="odd">
         <td>before</td>
         <td>[element name]</td>
         <td>The block displays before the named element.区块显示在指定名称元素之前</td>
      </tr>
      <tr class="even">
         <td>before</td>
         <td>empty value or [element name] is absent</td>
         <td>Use the value of <code>after</code>. If that value is empty or absent as well, the element is considered as non-positioned.
         使用after的值。如果那个值是空或也不存在，元素被判定为不放置
         </td>
      </tr>
      <tr class="even">
         <td>after</td>
         <td>Dash (-)</td>
         <td>The block displays after all other elements in its parent node.区块显示在它的父节点下所有其它元素之后</td>
      </tr>
      <tr class="odd">
         <td>after</td>
         <td>[element name]</td>
         <td>The block displays after the named element.区块显示在指定名称元素之后</td>
      </tr>
      <tr class="even">
         <td>after</td>
         <td>empty value or [element name] is absent 空值或元素名称不存在</td>
         <td>Use the value of <code>before</code>. If that value is empty or absent as well, the block is considered as non-positioned.
         使用before的值。如果那个值是空或也不存在，区块被判定为不放置
         </td>
      </tr>
   </tbody>
</table>
<h3 id="examples">Examples</h3>
<table>
   <tbody>
      <tr>
         <th>Situation</th>
         <th>Result</th>
      </tr>
      <tr class="even">
         <td>Both <code>before</code> and <code>after</code> attributes are present
         <br/>
         before和after属性同时存在
         </td>
         <td><code>after</code> takes precedence. after具有优先权</td>
      </tr>
      <tr class="odd">
         <td>Both <code>before</code> and <code>after</code> attributes are absent or empty
          <br/>
          两个属性同时为空或不存在
         </td>
         <td>The element is considered as non-positioned. All other elements are positioned at their specified locations. The missing element displays at a random position that doesn't violate requirements for the positioned elements.
         元素被当作不放置。所有其它元素被放置在它们指定的位置。缺少的元素显示在不违反定位元素需求的随机位置
         </td>
      </tr>
      <tr class="even">
         <td>Several elements have <code>before</code> or <code>after</code> set to dash (-)
         多个元素的before或after设置为破折号
         </td>
         <td>All elements display at the top (or bottom, in case of the after attribute), but the ordering of group of these elements is undefined.
         所有元素显示在顶部（或底部，在after属性的情况下），但这些元素的组的顺序是未定义的
         <br/>

         </td>
      </tr>
      <tr class="odd">
         <td>The <code>before</code> or <code>after</code> attribute's value refers to an element that is not located in the parent node of the element being defined.
         <br/>
         before和after属性的值是不位于正在定义的元素的父节点中的元素
         </td>
         <td>The element displays at a random location that doesn't violate requirements for the correctly positioned elements.
         <br/>
         元素显示在不违反正确定位元素需求的随机位置
         </td>
      </tr>
   </tbody>
</table>

<h3 id="fedg_layout_xml-instruc_ex_act">&lt;action 动作></h3>

<div class="bs-callout bs-callout-warning" id="info">
<span class="glyphicon-class">
 <p>The <code>&lt;action&gt;</code> instruction is deprecated. If the method implementation allows, use the <a href="#argument"><code>&lt;argument&gt;</code></a> for <a href="#fedg_layout_xml-instruc_ex_block"><code>&lt;block&gt;</code></a> or <a href="#fedg_layout_xml-instruc_ex_ref"><code>&lt;referenceBlock&gt;</code></a> to access block public API.
 <br/>
 action指令已被弃用。如果方法实现允许，为block或referenceBlock使用argument来访问区块公共API
 </p></span>
</div>

Calls public methods on the block API. 调用区块API上的公共方法
<p><b>Details:</b> Used to set up the execution of a certain method of the block during block generation; the <code>&lt;action></code> node must be located in the scope of the <code>&lt;block></code> node.
详细： 用来设定在区块生成时执行指定的区块方法；action节点必须放在block节点范围内
</p>


Example:

{%highlight xml%}
<block class="Magento\Module\Block\Class" name="block">
    <action method="setText">
        <argument name="text" translate="true" xsi:type="string">Text</argument>
    </action>
    <action method="setEnabled">
        <argument name="enabled" xsi:type="boolean">true</argument>
    </action>
</block>
{%endhighlight xml%}


<p><code>&lt;action></code> child nodes are translated into block method arguments. Child nodes names are arbitrary. If there are two or more nodes with the same name under <code>&lt;action></code>, they are passed as one array.
<br/>
action子节点被转换为区块方法的参数。子节点名称是任意的。如果在action下有两个或多个相同名称的节点，它们会作为一个数组传递
</p>

<table>
   <tbody>
      <tr>
         <th>Attribute</th>
         <th>Description</th>
         <th>Values</th>
         <th>Required?</th>
      </tr>
      <tr class="even">
         <td>method</td>
         <td>Name of the public method of the block class this tag is located in that is called during block generation.在区块生成期间调用此标签所在的区块类的公共方法的名称</td>
         <td>block method name区块方法名</td>
         <td>yes</td>
      </tr>
   </tbody>
</table>

To pass parameters, use the <a href="#argument"><code>&lt;argument&gt;&lt;/argument&gt;</code></a> instruction.

要传递参数使用argument 指定

<h3 id="fedg_layout_xml-instruc_ex_ref">&lt;referenceBlock> and &lt;referenceContainer></h3>
<p>Updates in <code>&lt;referenceBlock></code> and <code>&lt;referenceContainer></code> are applied to the corresponding <code>&lt;block></code> or <code>&lt;container></code>.
<br/>
在<code>&lt;referenceBlock></code> and <code>&lt;referenceContainer>的更新被应用到对应的<code>&lt;block></code> or <code>&lt;container></code>
</p>

<p>For example, if you make a reference by <code>&lt;referenceBlock name="right"></code>, you're targeting the block <code>&lt;block name="right"></code>.
<br/>
例如，如果你通过<code>&lt;referenceBlock name="right"></code>进行引用，则你定位的是<code>&lt;block name="right"></code>.
</p>

To pass parameters to a block use the <a href="#argument"><code>&lt;argument>&lt;/argument></code></a> instruction.

<table>
   <tbody>
      <tr>
         <th>Attribute</th>
         <th>Description</th>
         <th>Values</th>
         <th>Required?</th>
      </tr>
      <tr class="even">
         <td>remove</td>
         <td>Allows to remove or cancel the removal of the element. When a container is removed, its child elements are removed as well.
         <br/>
         允许移除或取消移除元素。当一个元素被移除了，它的子元素也会移除
         </td>
         <td>true/false</td>
         <td>no</td>
      </tr>
      <tr class="even">
         <td>display</td>
         <td>Allows you to disable rendering of specific block or container with all its children (both set directly and by reference). The block's/container's and its children' respective PHP objects are still generated and available for manipulation.
         <br/>
         允许你禁用特定区块或容器及其子代（直接和通过引用设置）的渲染。区块的/容器的和它的子代各自的PHP对象依然生成且可被操作
         </td>
         <td>true/false</td>
         <td>no</td>
      </tr>
   </tbody>
</table>

<ul>
<li>The <code>remove</code> attribute is optional and its default value is false.
remove属性是可选的它的默认值是false
</li>

    This implementation allows you to cancel removal of a block or container in your layout by setting remove attribute value to false.
    
    这种实现允许在你的布局通过设置remove属性值为false来取消移除区块或容器

    Example: 
    
    <pre>&lt;referenceBlock name="block.name" remove="true" /&gt;</pre>

<li>The <code>display</code> attribute is optional and its default value is true.
    display属性是可选的且默认值是true
    <br/>

    You are always able to overwrite this value in your layout.
    In situation when remove value is true, the display attribute is ignored.

    你总是可以在你的布局覆写这个值。当remove为true时display属性则被忽略
    
    Example: 
    
    <pre>&lt;referenceContainer name="container.name" display="false" /&gt;</pre>
    </li>
</ul>  

<h3 id="fedg_layout_xml-instruc_ex_mv">&lt;move></h3>
Sets the declared block or container element as a child of another element in the specified order.

设置指定区块或容器元素按指定顺序作为另一个元素的子代

<p><b>Example:</b></p>

{%highlight xml%}
<move element="name.of.an.element" destination="name.of.destination.element" as="new_alias" after="name.of.element.after" before="name.of.element.before"/>
{%endhighlight xml%}


<ul>
   <li><code>&lt;move></code> is skipped if the element to be moved is not defined.
   如果要被移动的元素未定义则move 被跳过
   </li>
   <li>If the <code>as</code> attribute is not defined, the current value of the element alias is used. If that is not possible, the value of the <code>name</code> attribute is used instead.
   <br/>
   如果as属性没有定义，使用元素别名的当前值。如果不可能则使用name属性
   </li>
  <li>During layout generation, the <code>&lt;move&gt;</code>
  instruction is processed before the removal (set using the <code>
    remove</code> attribute). This means if any elements are moved
    to the element scheduled for removal, they will be removed as
    well.
    <br/>
    在布局生成期间，move指令在移除之前处理。意味着如果任何元素被移动到计划要移除，它们也会被移除
  </li>
</ul>
<table>
   <tbody>
      <tr>
         <th>Attribute</th>
         <th>Description</th>
         <th>Values</th>
         <th>Required?</th>
      </tr>
      <tr class="even">
         <td>element</td>
         <td>Name of the element to move.要移动的元素名</td>
         <td>element name</td>
         <td>yes</td>
      </tr>
      <tr class="odd">
         <td>destination</td>
         <td>Name of the target parent element.目标父元素名</td>
         <td>element name</td>
         <td>yes</td>
      </tr>
      <tr class="even">
         <td>as</td>
         <td>Alias name for the element in the new location.元素在新位置的别名</td>
         <td>0-9, A-Z, a-z, underscore (_), period (.), dash (-). Case-sensitive.</td>
         <td>no</td>
      </tr>
      <tr class="odd">
         <td>after | before</td>
         <td>Specifies the element's position relative to siblings. Use dash (-) to position the block before or after all other siblings of its level of nesting. If the attribute is omitted, the element is placed after all siblings.</td>
         <td>element name</td>
         <td>no</td>
      </tr>
   </tbody>
</table>

<h3 id="fedg_layout_xml-instruc_ex_rmv">&lt;remove&gt;</h3>

Is used only to remove the static resources linked in a page <code>&lt;head&gt;</code> section.
For removing blocks or containers, use the <code>&lt;remove&gt;</code> attribute for <a href="#fedg_layout_xml-instruc_ex_ref"><code>&lt;referenceBlock&gt;</code> and <code>&lt;referenceContainer&gt;</code></a>.

仅用来移除在页面head区域链接的静态资源。要移除区块或容器，使用<code>&lt;referenceBlock&gt;</code> and <code>&lt;referenceContainer&gt;</code>的remove属性。

Example of usage:

{%highlight xml%}
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
   <head>
        <!-- Remove local resources -->
        <remove src="css/styles-m.css" />
        <remove src="my-js.js"/>
        <remove src="Magento_Catalog::js/compare.js" />
								
	<!-- Remove external resources -->
        <remove src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap-theme.min.css"/>
        <remove src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/js/bootstrap.min.js"/>
        <remove src="http://fonts.googleapis.com/css?family=Montserrat" /> 
   </head>
{%endhighlight xml%}

<h3 id="fedg_layout_xml-instruc_ex_upd">&lt;update&gt;</h3>

Includes a certain layout file. 包含一个指定布局文件

Used as follows: 如

{%highlight xml%}
<update handle="{name_of_handle_to_include}"/>
{%endhighlight xml%}

The specified <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#handle" target="_blank">handle</a> is "included" and executed recursively.

指定的handle会被包含并递归执行

<h3 id="argument">&lt;argument&gt;</h3>
Used to pass an argument. 传递参数

<table>
   <tbody>
      <tr>
         <th>Attribute</th>
         <th>Description</th>
         <th>Values</th>
         <th>Required?</th>
      </tr>
      <tr class="even">
         <td>name</td>
         <td>Argument name.</td>
         <td>unique</td>
         <td>yes</td>
      </tr>
      <tr class="odd">
         <td>xsi:type</td>
         <td>Argument type.</td>
         <td>string | boolean | object | number | null | array</td>
         <td>yes</td>
      </tr>
      <tr class="even">
         <td>translate</td>
         <td></td>
         <td>true | false</td>
         <td>no</td>
      </tr>

   </tbody>
</table>

To pass multiple arguments use the following construction: 传递多个参数如下：
{%highlight xml%}
<arguments>
   <argument></argument>
   <argument></argument>
   ...
</arguments>
{%endhighlight xml%}

To pass an argument that is an array use the following construction:
传递一个数组参数如下

{%highlight xml%}
<argument>
   <item></item>
   <item></item>
   ...
</argument>
{%endhighlight xml%}

<p id="getter">Arguments values set in a layout file can be accessed in <a href="{{page.baseurl}}frontend-dev-guide/templates/template-overview.html" target="_blank">templates</a> using the <code>get{ArgumentName}()</code> and <code>has{ArgumentName}()</code> methods. The latter returns a boolean defining whether there's any value set. 
<br/>
布局文件设置的参数值可以在模板使用<code>get{ArgumentName}()</code> and <code>has{ArgumentName}()</code>方法获取。后面的返回一个布尔值定义是否有值被设置

<code>{ArgumentName}</code> is obtained from the <code>name</code> attribute the following way: for getting the value of <code>&lt;argument name="some_string"&gt;</code> the method name is <code>getSomeString()</code>.
<br/>
<code>{ArgumentName}</code>用如下方式从<code>name</code>属性获取：为获取<code>&lt;argument name="some_string"&gt;</code>的值的方法名是<code>getSomeString()</code>.<br/>

Example:
Setting a value of <code>css_class</code> in the <code><a href="{{site.mage2000url}}app/code/Magento/Theme/view/frontend/layout/default.xml" target="_blank">app/code/Magento/Theme/view/frontend/layout/default.xml</a></code> layout file:
<br/>
例如在app/code/Magento/Theme/view/frontend/layout/default.xml布局文件设置<code>css_class</code>值：
<br/>
{%highlight xml%}
...
<arguments>
    <argument name="css_class" xsi:type="string">header links</argument>
</arguments>
...
{%endhighlight xml%}


Using the value of <code>css_class</code> in <code><a href="{{site.mage2000url}}app/code/Magento/Theme/view/frontend/templates/html/title.phtml" target="_blank">app/code/Magento/Theme/view/frontend/templates/html/title.phtml</a></code>:
<br/>
在app/code/Magento/Theme/view/frontend/templates/html/title.phtml这个文件使用<code>css_class</code>值：
{%highlight php%}
...
$cssClass = $this->getCssClass() ? ' ' . $this->getCssClass() : '';
...
{%endhighlight %}




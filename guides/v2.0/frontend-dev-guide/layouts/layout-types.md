---
layout: default
group: fedg
subgroup: B_Layouts
title: 布局文件类型
menu_title: 布局文件类型
menu_order: 3
version: 2.0
github_link: frontend-dev-guide/layouts/layout-types.md
redirect_from: /guides/v1.0/frontend-dev-guide/layouts/layout-types.html
---
<head>
	<style>
		table tr td, table tr th {border: 1px solid #ABABAB}
	</style>
</head>
<h2>What's in this topic 本专题讲什么？</h2>
For a particular page, its layout is defined by two major layout components: *page layout* file and *page configuration* file. 

对一个特定页面，它的布局主要由两种布局组件定义：页面布局文件和页面配置文件

A page layout file defines the page wireframe, for example, one-column layout. Technically page layout is an .xml file defining the structure inside the `<body>` section of the HTML page markup. Page layouts feature only <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#layout_overview_blocks" target="_blank">containers</a>. 
All page layouts used for page rendering should be declared in the page layout declaration file.

页面布局文件定义页面线框，如一列布局。技术上页面布局是一个.xml文件定义HTML页面标签里的body区域的结构。页面布局仅包含容器。所有用于页面渲染的页面布局必须声明在页面布局声明文件中

Page configuration is also an .xml file. It defines the detailed structure (page header, footer, etc.), contents and page meta information, including the page layout used. Page configuration features both main elements, <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html#layout_overview_blocks" target="_blank">blocks of particular classes</a> and containers.

页面配置也是.xml文件。它定义详细结构（head/footer等）、内容和页面元信息、包括页面布局用到的。页面配置包含两种主要元素，特定类区块和容器。

We also distinguish the third type of layout files, *generic layouts*. They are .xml files which define the contents and detailed structure inside the <code>&lt;body&gt;</code> section of the HTML page markup. These files are used for pages returned by AJAX requests, emails, HTML snippets and so on.

我们还区分第三种布局文件，*通用布局*。他们是定义HTML页面标签的body区域内的内容和详细结构。这些文件用于被AJAX请求返回、emails、HTML片断等页面

This article gives a comprehensive description of each layout file type.此文提供每种布局文件类型的全面描述

<h2 id="layout-types-page">Page layout页面布局</h2>
Page layout declares the wireframe of a page inside the <code>&lt;body&gt;</code> section, for example one-column layout or two-column layout. 

页面布局声明一个页面body区域内的线框，如一列布局或两列布局。

Allowed layout instructions: 允许的布局指令

* <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_cont" target="_blank">&nbsp;&lt;container&gt;</a>
* <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_ref" target="_blank">&nbsp;&lt;referenceContainer&gt;</a>
* <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_mv" target="_blank">&nbsp;&lt;move&gt;</a>
* <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#fedg_layout_xml-instruc_ex_upd" target="_blank">&nbsp;&lt;update&gt;</a> 

Sample page layout: 页面布局示例

`<Magento_Theme_module_dir>/view/frontend/page_layout/2columns-left.xml`

{%highlight xml%}
<layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_layout.xsd">
    <update handle="1column"/>
    <referenceContainer name="columns">
        <container name="div.sidebar.main" htmlTag="div" htmlClass="sidebar sidebar-main" after="main">
            <container name="sidebar.main" as="sidebar_main" label="Sidebar Main"/>
        </container>
        <container name="div.sidebar.additional" htmlTag="div" htmlClass="sidebar sidebar-additional" after="div.sidebar.main">
            <container name="sidebar.additional" as="sidebar_additional" label="Sidebar Additional"/>
        </container>
    </referenceContainer>
</layout>
{%endhighlight xml%}

<h3 id="layout-types-page-conv">Page layout files conventional location页面布局文件常规位置</h3>

Conventionally page layouts must be located as follows:
常规页面布局必须在以下位置：

* Module page layouts: `<module_dir>/view/frontend/page_layout` 模块页面布局
* Theme page layouts: `<theme_dir>/<Namespace>_<Module>/page_layout` 主题页面布局

<h3 id="layout-types-page-dec">Page layouts declaration页面布局声明</h3>

To be able to use a layout for actual page rendering, you need to declare it in `layouts.xml`.

为真实页面渲染能使用布局，你需要在layouts.xml里声明

Conventionally layout declaration file can be located in one of the following locations: 

常规布局声明文件可以在下面的一个位置：

<ul>
<li>Module layout declarations: <code>&lt;module_dir&gt;/view/frontend/layouts.xml</code></li>
<li>Theme layout declaration: <code>&lt;theme_dir&gt;/&lt;Namespace&gt;_&lt;Module&gt;/layouts.xml</code></li>

</ul>

<br>
<p>Declare a layout file using the <code>&lt;layout&gt;&lt;/layout&gt;</code> instruction, for which specify the following:<br/>
声明一个布局文件使用<code>&lt;layout&gt;&lt;/layout&gt;</code>指令，如下
</p>


<ul>
 <li><code>&lt;layout&nbsp;id=&quot;layout_file_name&quot;&gt;</code>. For example, the <code>2columns-left.xml</code> page layout is declared like following: <code>&lt;layout&nbsp;id&nbsp;=&nbsp;&quot;2columns-left&quot;/&gt;</code></li>

<li><code>&lt;label&nbsp;translate=&quot;true|false&quot;&gt;{Label_used_in_Admin}&lt;/label&gt;</code></li>
</ul>

Sample page layout declaration file:示例页面布局声明文件：

    <Magento_Theme_module_dir>/view/frontend/layouts.xml

{%highlight xml%}
<page_layouts xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/PageLayout/etc/layouts.xsd">
    <layout id="1column">
        <label translate="true">1 column</label>
    </layout>
    <layout id="2columns-left">
        <label translate="true">2 columns with left bar</label>
    </layout>
    <layout id="2columns-right">
        <label translate="true">2 columns with right bar</label>
    </layout>
    <layout id="3columns">
        <label translate="true">3 columns</label>
    </layout>
</page_layouts>
{%endhighlight xml%}

<h2 id="layout-types-conf">Page configuration页面配置</h2>

The page configuration adds content to the wireframe defined in a page layout file. A page configuration also contains page meta-information, and contents of the <code>&lt;head&gt;</code> section.

页面配置添加内容到页面布局文件定义的线框里。一个页面配置也包含页面元信息、和head区域内容。

<h3 id="layout-type-conf-loc">Page configuration file conventional location页面配置文件常规位置</h3>

Conventionally page configuration files must be located as follows:

<ul>
<li> Module page configurations: <code>&lt;module_dir&gt;/view/frontend/layout</code></li>
<li> Theme page configurations: <code>&lt;theme_dir&gt;/&lt;Namespace&gt;_&lt;Module&gt;/layout</code></li>
</ul>


<h3>Page configuration structure and allowed layout instructions页面配置结构和允许的布局指令</h3>

The following table describes the instructions specific for page configuration files. For the descriptions of common layout instructions see the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html" target="_blank">Layout instructions</a> article.

下表描述特定于页面配置文件的指令。对于通用布局指令说有查看布局指令一文

<table>
  <tbody>
    <tr>
      <th>Element</th>
      <th colspan="1">Attributes</th>
      <th colspan="1">Parent of</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>
        <code><span>&lt;page&gt;&lt;/page&gt;</span></code>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <code>layout = {layout}</code>
          </li>
          <li>
            <code>xsi:noNamespaceSchemaLocation ="{path_to_schema}"</code>            
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li><code>&lt;html&gt;</code></li>
          <li><code>&lt;head&gt;</code></li>
          <li><code>&lt;body&gt;</code></li>
          <li><code>&lt;update&gt;</code></li>
        </ul>
      </td>
      <td>Mandatory root element. 强制根元素</td>
    </tr>
    <tr>
      <td colspan="1"><code>&lt;html&gt;&lt;/html&gt;</code></td>
      <td colspan="1">
        <p>none</p>
      </td>
      <td colspan="1">
        <ul>
          <li><code>&lt;attribute&gt;</code></li>
        </ul>
      </td>
      <td colspan="1">
        <span>Mandatory element.强制元素</span>
      </td>
    </tr>
    <tr>
      <td colspan="1"><code>&lt;head&gt;&lt;/head&gt;</code></td>
      <td colspan="1">none</td>
      <td colspan="1">
        <ul>
          <li><code>&lt;title&gt;</code></li>
          <li><code>&lt;meta&gt;</code></li>
          <li><code>&lt;link&gt;</code></li>
          <li><code>&lt;css&gt;</code></li>
          <li><code>&lt;script&gt;</code></li>
        </ul>
      </td>
      <td colspan="1"></td>
    </tr>
    <tr>
      <td colspan="1"><code>&lt;body&gt;&lt;/body&gt;</code></td>
      <td colspan="1">none</td>
      <td colspan="1">
        <ul>
          <li><code>&lt;block&gt;</code></li>
          <li><code>&lt;container&gt;</code></li>
          <li><code>&lt;move&gt;</code></li>
       <li><code>&lt;attribute&gt;</code></li>
          <li><code>&lt;referenceBlock&gt;</code></li>
          <li><code>&lt;referenceContainer&gt;</code></li>
          <li><code>&lt;action&gt;</code></li>
        </ul>
      </td>
      <td colspan="1"></td>
    </tr>
    <tr>
      <td colspan="1"><code>&lt;attribute&gt;</code></td>
      <td colspan="1">
        <ul>
          <li><code>name = {arbitrary_name}</code>
          </li>
          <li><code>value = {arbitrary_value}</code>
          </li>
        </ul>
      </td>
      <td colspan="1"></td>
      <td colspan="1">
        <p>Specified for <code>&lt;html&gt;</code>, rendered like following:</p>
        <p><code>&lt;html name="value'&gt;</code></p>
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <p><code>&lt;title&gt;</code></p>
      </td>
      <td colspan="1">none</td>
      <td colspan="1">none</td>
      <td colspan="1">Page title</td>
    </tr>
    <tr>
      <td colspan="1">
        <p><code>&lt;meta&gt;</code></p>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <span><code>content</code></span>
          </li>
          <li>
            <span><code>charset</code></span>
          </li>
          <li>
            <span><code>http-equiv</code></span>
          </li>
          <li>
            <span><code>name</code></span>
          </li>
          <li>
            <span><code>scheme</code></span>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <span>none</span>
      </td>
      <td colspan="1"></td>
    </tr>
    <tr>
      <td colspan="1">
        <p><code>&lt;link&gt;</code></p>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <span><code>src</code></span>
          </li>
          <li>
            <span><code>defer</code></span>
          </li>
          <li>
            <span><code>ie_condition</code></span>
          </li>
          <li>
            <span><code>charset</code></span>
          </li>
          <li>
            <span><code>hreflang</code></span>
          </li>
          <li>
            <span><code>media</code></span>
          </li>
          <li>
            <span><code>rel</code></span>
          </li>
          <li>
            <span><code>rev</code></span>
          </li>
          <li>
            <span><code>sizes</code></span>
          </li>
          <li>
            <span><code>target</code></span>
          </li>
          <li>
            <span><code>type</code></span>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <span>none</span>
      </td>
      <td colspan="1"> </td>
    </tr>
    <tr>
      <td colspan="1">
        <span><code>&lt;css&gt;</code></span>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <span><code>src</code></span>
          </li>
          <li>
            <span><code>defer</code></span>
          </li>
          <li>
            <span><code>ie_condition</code></span>
          </li>
          <li>
            <span><code>charset</code></span>
          </li>
          <li>
            <span><code>hreflang</code></span>
          </li>
          <li>
            <span><code>media</code></span>
          </li>
          <li>
            <span><code>rel</code></span>
          </li>
          <li>
            <span><code>rev</code></span>
          </li>
          <li>
            <span><code>sizes</code></span>
          </li>
          <li>
            <span><code>target</code></span>
          </li>
          <li>
            <span><code>type</code></span>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <span>none</span>
      </td>
      <td colspan="1"></td>
    </tr>
    <tr>
      <td colspan="1">
        <p><code>&lt;script&gt;</code></p>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <span><code>src</code></span>
          </li>
          <li>
            <span><code>defer</code></span>
          </li>
          <li>
            <span><code>ie_condition</code></span>
          </li>
          <li>
            <span><code>async</code></span>
          </li>
          <li>
            <span><code>charset</code></span>
          </li>
          <li>
            <span><code>type</code></span>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <span>none</span>
      </td>
      <td colspan="1"></td>
    </tr>
  </tbody>
</table>

<h2 id="layout-types-gen">Generic layout 通用布局</h2>

Generic layouts define the contents and detailed structure inside the <code>&lt;body&gt;</code> section of the HTML page markup. 

通用布局定义HTML页面标签body区域内的内容和详细结构

<h3 id="layout-type-gen-loc">Generic layout file conventional location</h3>

Conventionally generic layout files must be located as follows:

<ul>
<li>Module generic layouts: <code>&lt;module_dir&gt;/view/frontend/layout</code></li>
<li>Theme generic layouts: <code>&lt;theme_dir&gt;/&lt;Namespace&gt;_&lt;Module&gt;/layout</code></li>
</ul>


<h3>Generic layout structure and allowed layout instructions通用布局结构和允许的布局指令</h3>

The following table describes the instructions specific for generic layout files. For the descriptions of common layout instructions see the <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html" target="_blank">Layout instructions</a> article.

下表描述通用布局特定文件的指定。常用布局指令查看布局指令一文

<table>
  <tbody>
    <tr>
      <th>Element</th>
      <th colspan="1">Attributes</th>
      <th colspan="1">Parent of</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>
        <code> &lt;layout&gt;&lt;/layout&gt; </code>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <code >
              xsi:noNamespaceSchemaLocation="{path_to_schema}"
</code>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li><code>&lt;container&gt;</code></li>
          <li><code>&lt;update&gt;</code></li>

        </ul>
      </td>
      <td>Mandatory root element.</td>
    </tr>
    <tr>
      <td>
        <code> &lt;update&gt; </code>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <code>handle="{name_of_handle_to_include}"</code>
          </li>
        </ul>
      </td>
      <td colspan="1">
none
      </td>
<td></td>
    </tr>
    <tr>
      <td colspan="1"><code>&lt;container&gt;</code></td>
      <td colspan="1">
<ul>
<li><code>name="root"</code></li>
<li>For complete list of attributes, see <a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html#container" target="_blank">Layout instructions</a></li>
</ul>
</td>
      <td colspan="1">
        <ul>
          <li><code>&lt;block&gt;</code></li>
          <li><code>&lt;container&gt;</code></li>
          <li><code>&lt;referenceBlock&gt;</code></li>
          <li><code>&lt;referenceContainer&gt;</code></li>
          
        </ul>
      </td>
      <td colspan="1"> Mandatory element</td>
    </tr>


  </tbody>
</table>

Sample generic layout:

{%highlight xml%}
<layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/layout_generic.xsd">
    <update handle="formkey"/>
    <update handle="adminhtml_googleshopping_types_block"/>
    <container name="root">
        <block class="Magento\Backend\Block\Widget\Grid\Container" name="googleshopping.types.container" template="Magento_Backend::widget/grid/container/empty.phtml"/>
    </container>
</layout>
{%endhighlight xml%}


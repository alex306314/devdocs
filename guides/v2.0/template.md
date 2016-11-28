---
layout: default
group:
subgroup: A_Introduction
title: template (generic)
menu_title: template (generic)
menu_order: 1
---
*这是一个那些还没有被Magneto开发者文档组编写的主题的模板*

我们鼓励我们的社区成员来添加内容；可以添加一个全新的主题、添加一部分到已有主题或是仅一句话和某个主题有关的。不要担心最佳语法或形式；仅展示你的才华（just get your brilliance down）

开始编辑你的本地版本文件，使用markdown语言（有的地方需要HTML）。然后创建一个Pull Request让你的贡献可以被文档组浏览到。

你对我们文档的贡献及使用Magento的经验都非常有价值和宝贵。如果有任何问题请让我们知道

<h2 id="overview">综述</h2>
主题综述写在这里

<h2 id="H2">标题2</h2>
第一部分的文字

<div class="bs-callout bs-callout-info" id="info">

  <p>这里添加注解笔记</a>.</p>

</div>

<h3 id="H3">标题3</h3>
下一个区块的内容

超链接到另一个主题 <a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">主题或书的名称</a>.



<h2 id="H2">标题 2</h2>
另一个区域正文

添加图表或插图 <p><img src="{{ site.baseurl }}common/images/NAME_OF_IMAGEjpg" alt="提示文字"></p>

<h2 id="book-related">相关主题</h2>

* <a href="{{page.baseurl}}_____/_____.html">相关主题标题</a>
* <a href="{{page.baseurl}}_____/_____.html">相关主题标题</a>

## 可折叠正文

### 例如
{% collapsible 点击显示/隐藏内容 %}
为了使用可折叠内容功能你可以使用`collapsible`块标签。任何内容在这个块内会隐藏，直到点击标题文字

查看这个文件的markdown版本示例
{% endcollapsible %}

{% collapsible 点击显示/隐藏内容 %}
![这是一个图片]({{ site.baseurl }}common/images/connect_keys2.png)
{% endcollapsible %}

{% collapsible HTML Table %}
<table>
  <tbody>
    <tr>
      <th>Col 1</th>
      <th>Col 2</th>
      <th>Col 3</th>
    </tr>
    <tr>
      <td>Data 1</td>
      <td>Data 2</td>
      <td>Data 3</td>
    </tr>
    <tr>
      <td>Data 4</td>
      <td>Data 5</td>
      <td>Data 6</td>
    </tr>
    <tr>
      <td>Data 7</td>
      <td>Data 8</td>
      <td>Data 9</td>
    </tr>
  </tbody>
</table>
{% endcollapsible %}

{% collapsible Markdown Table %}
| Col 1  | Col 2  | Col 3  |
| :----: | :----: | :----: |
| Data 1 | Data 2 | Data 3 |
| Data 4 | Data 5 | Data 6 |
| Data 7 | Data 8 | Data 9 |
{% endcollapsible %}

{% collapsible Click to show/hide list %}
* List Item 1
* List Item 2
* List Item 3
{% endcollapsible %}

{% collapsible 点击显示/隐藏include内容 %}
{% include mtf/page-generator.html %}
{% endcollapsible %}

{% collapsible 可折叠代码块示例%}

**正常markdown**

~~~
<div class="collapsible">
  <h4 class="collapsible-title">可折叠标题</h4>
  <div class="collapsible-content">
    <p>可折叠正文</p>
  </div>
</div>
~~~

**主亮代码**

{% highlight html %}
<div class="collapsible">
  <h4 class="collapsible-title">可折叠标题</h4>
  <div class="collapsible-content">
    <p>可折叠正文</p>
  </div>
</div>
{% endhighlight %}
{% endcollapsible %}


### 可折叠组

<div class="collapsible">
  <b class="collapsible-title">可折叠主题1</b>
  <div class="collapsible-content">
    <p>你可以在可折叠容器中有多个 标题-正文 对</p>
  </div>
  <b class="collapsible-title">可折叠主题2</b>
  <div class="collapsible-content">
    <p>每一块内容都是由它之前的标题控制</p>
  </div>
  <b class="collapsible-title">可折叠主题3</b>
  <div class="collapsible-content">
    <p>点击标题会打开折叠的内容并关闭其它打开的内容</p>
  </div>
</div>

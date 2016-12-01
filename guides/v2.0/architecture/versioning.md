---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: 版本控制策略
menu_title: 版本控制策略
menu_order: 4
version: 2.0
github_link: architecture/versioning.md
redirect_from: /guides/v1.0/architecture/versioning.html
---

<h2 id="verpol">Versioning policy overview版本控制策略概览</h2>

The Magento system and its components use the software (or "platform") version to indicate the compatibility of changes in the implementation (on the code level). By comparing two versions of the same component, one can tell whether it has any <a href="{{page.baseurl}}architecture/back-compatibility.html">backward-incompatible</a> changes in the public API or other significant code changes.

Magneto系统和组件使用软件版本来表明实现的修改（代码层）的向后兼容性。通过对比同一个组件的不同版本号，可以知道是否它在公共API或其它重大代码修改上有任何向后不兼容的改动。

Magento software versioning complies with the following specifications:

Magneto软件版本遵从如下规格：

* [Semantic Versioning 2.0.0](http://semver.org/)
* [Versioning specification of Composer system](https://getcomposer.org/doc/04-schema.md#version)
* [PHP version_compare()](http://php.net/version_compare)


<h3>版本格式</h3>


稳定发布版格式是`MAJOR.MINOR.PATCH`, 其中:

* MAJOR 指不兼容API修改

* MINOR 指添加了向后兼容的功能

* PATCH 指向后兼容的BUG修复


The pre-release version format is: `MAJOR.MINOR.PATCH-<alpha | beta | rc>n`, where `alpha`, `beta` or `rc` are stability indications, as described in the `version_compare()` specification, and
`n` is an increment number to distinguish releases of the non-stable versions.

预览版版本格式是: `MAJOR.MINOR.PATCH-<alpha | beta | rc>n`, 其中`alpha`、`beta` 或 `rc`代表稳定性，正如`version_compare()`说明描述的，`n`是一个增加的数字来区分不稳定版本

<h3>Public APIs公共API</h3>

Source code is considered public API only if it is explicitly marked as such using the `@api` docblock tag. This designation indicates the code can be used or customized by other components, such as formal interfaces and dependency injection points.

只有使用`@api`文件块标签明确标记了的源代码才是公共API。这种指定表明这些代码可以被其它组件使用或自定义，如正式接口和依赖注入点。

For PHP code, compatibility of `@api` may be tracked on the level of structural elements (class signatures, interfaces, methods, etc.). For other source code, compatibility is tracked only on file level (for example, the file has been deleted or renamed).

对于PHP代码， `@api`的兼容性会追踪到结构元素层（类标记、接口、方法等）。对其它源代码兼容性可能只追踪到文件层（如文件已经删除或重命名）

<h3>哪些地方使用了版本</h3>
The software version can be found in the source code of any Magento component or bundle, inside the `composer.json` file.

软件版本可以在Magento组件或包中的`composer.json`文件源代码找到

它可以定义为组件版本:

{% highlight JSON %}
"name": "acme/foo",
"version": 1.2.0
{% endhighlight %}

或定义为依赖特定版本的组件:

{% highlight JSON %}
"require": {
    "acme/foo": "1.2.*",
    "acme/bar": "2.2.0"
}
{% endhighlight %}


<h3>发布类型</h3>
This section describes how exactly and when the software version numbers will be changed with releases.

这一部分描述发布版本时如何准确和什么时候修改软件版本数字

The software version will always change with any release of Magento source code.

在任何Magento源代码发布软件版本都一直会修改

<h3>Development releases开发释出版</h3>
In every development release ("pre-release" version), **the same value of version number will be propagated in all Magento components and their dependencies**.

在每一个开发版（"预发布" 版）所有Magento组件和它们的依赖都有相同的版本号值

Magento may update the `x.y.z` version in way perscribed by Semantic Versioning, but also could release the same `x.y.z` with different stability and/or index numbers, For example, `0.1.0-alpha1 -> 0.1.0-alpha2`, `0.1.0-alpha3` or `2.0.0-alpha3 -> 2.1.0-beta1 -> 2.1.0-beta2`

Magneto会按Semantic Versioning规定的方式更新 `x.y.z` 版本号，也可以发布相同的`x.y.z`后加不同稳定性或序号，如：`0.1.0-alpha1 -> 0.1.0-alpha2`, `0.1.0-alpha3` 或 `2.0.0-alpha3 -> 2.1.0-beta1 -> 2.1.0-beta2`

<table>
<tbody>
<tr>
<th></th>
<th>上一次发布</th>
<th>下一次发布</th>
</tr>
<tr>
<td>组件版本</td>
<td><pre>
"name": "magento/foo",
"version": 0.1.0-alpha87</pre></td>
<td><pre>
"name": "magento/foo",
"version": 0.1.0-alpha88</pre></td></tr>
<tr>
<td>依赖其它组件</td>
<td><pre>"require": {
    "magento/foo": "0.1.0-alpha87"
}
</pre></td>
<td><pre>"require": {
    "magento/foo": "0.1.0-alpha88"
}
</pre></td></tr>
</tbody>
</table>

<h3>Stable releases稳定发布版</h3>

In every stable release, the same value of version number will be propagated in all components, but dependencies will have a wildcard (*) pattern.

在每一个稳定发布版，所有组件使用相同的版本号值，但依赖会使用一个通配符 (*) 格式

The `x.y.z` numbers will change according to Semantic Versioning policy provisions. For example, `1.0.0 -> 1.0.1 -> 1.1.0 -> 1.5.0 -> 1.5.1 -> 2.0.0 -> 2.1.0`. Also, Magento may decide to change the "minor" version instead of the "patch" version.

`x.y.z`版本号会按Semantic Versioning策略规定做修改，如：`1.0.0 -> 1.0.1 -> 1.1.0 -> 1.5.0 -> 1.5.1 -> 2.0.0 -> 2.1.0。 同时Magneto也会考虑修改 "minor"版本而不是"patch"版本号

<table>
<tbody>
<tr>
<th></th>
<th>上一次发布</th>
<th>下一次发布</th>
</tr>
<tr>
<td>组件版本</td>
<td><pre>"name": "magento/foo",
"version": ~1.2
</pre>
<p>相当于 &gt;= 1.2 &lt; 2.0.0.</p></td>
<td><pre>"name": "magento/foo",
"version": 1.3.0
</pre></td></tr>
<tr>
<td>依赖其它组件</td>
<td><pre>"require": {
    "magento/foo": "1.2.*"
}
</pre></td>
<td><pre>"require": {
    "magento/foo": "1.3.*"
}
</pre></td>
</tr>
</tbody>
</table>


<h3>Example lifecycle生命周期示例</h3>
The following steps demonstrate the packaging and backward compatibility story from the view of Magento, system integrators, and extension developers. This example uses several composer packages on the public github to simulate a merchant site, 2 core Magento modules, and a third-party extension.

下面的步骤从Magento、系统集成和扩展开发者的角度演示打包和向后兼容方法。这个示例使用了一些github上公开的composer包来模拟一个网店、2核心Magento模块和一个第三方扩展

<ol>
<li>Start by cloning the master branch from github. This sample in <code>composer.json</code> states this site is dependent on a release candidate of a simulated Magento 2.0 release.
<br/>
从github克隆master分支开始。这个示例在<code>composer.json</code>说明这个网站依赖于模拟Magento2.0版本的发布候选版


{% highlight JSON %}
{
  "name": "myexamplestore/sample-site",
  "description": "A sample site",
  "type": "project",
  "version": "1.0.0",
  "require": {
    "myexamplestore/product-bundle": "2.0.0-RC1"
    }
}
{% endhighlight %}
</li>

<li>Run the <code>composer update</code> command. Core modules a & b are pulled down from the repository.
<br>
运行<code>composer update</code>命令。核心模块a & b会从仓库进行下载
</li>


<li>Now the SI includes a third-party extension by adding the composer dependency. This extension trusts our BC and sets the appropriate version on the module-a core dependency.

<br>
现在SI通过添加composer依赖包含一个第三方扩展。这个扩展相信我们的BC并在模块a核心依赖上设置合适的版本

{% highlight JSON %}
{
  "name": "myexamplestore/sample-site",
  "description": "A sample site",
  "type": "project",
  "version": "1.0.0",
  "require": {
    "myexamplestore/product-bundle": "2.0.0-RC1",
    "myexamplestore/acme-extension": "~1.0"
    }
}
{% endhighlight %}
</li>

<li>Run <code>composer update</code> and see the new extension downloaded.
<br>
运行<code>composer update</code>并查看新扩展已经下载
</li>

<li>When Magento releases 2.0 GA, the SI updates the site <code>composer.json</code> to the release version.
<br>
当Magento发布2.0GA, SI更新网站<code>composer.json</code>到发布的版本。

{% highlight JSON %}{
  "name": "myexamplestore/sample-site",
  "description": "A sample site",
  "type": "project",
  "version": "1.0.0",
  "require": {
    "myexamplestore/product-bundle": "2.0.0",
    "myexamplestore/acme-extension": "~1.0"
    }
}
{% endhighlight %}
</li>

<li>Run <code>composer update</code> and notice the core modules were updated since RC1, but the extension remains unchanged because of BC policy.
<br>
运行<code>composer update</code>并注意核心模块已经从RC1版本更新了，但由于BC策略扩展会保持不变

   This step repeats with each subsequent release of Magento (2.1, 2.2, 2.3, etc.). Deprecation strategy and community communication happens in 2.3.
   <br>
   每个随后的Magento（2.1，2.2，2.3等）发布版都会重复这一步。弃用策略和社区通信会在2.3
</li>

<li>Magento decides backward incompatible changes are allowed and does this as part of the upcoming release 2.4.
<br>
Magento决定在未来的2.4版本允许改动向后不兼容

   {% highlight JSON %}
{
  "name": "myexamplestore/sample-site",
  "description": "A sample site",
  "type": "project",
  "version": "1.0.0",
  "require": {
    "myexamplestore/product-bundle": "2.4.0-RC1",
    "myexamplestore/acme-extension": "~1.0"
    }
}
{% endhighlight %}
</li>

<li>Run <code>composer update</code> and notice that <code>acme-extension</code> is marked as incompatible.
<br>
运行<code>composer update</code>会提示<code>acme-extension</code>被标记为不兼容
 </li>

<li>Based upon previous communication, the developer has updated the extension so the SI updates to the new extension version.
<br>
基于之前的交流，开发者已经更新了扩展，所以IS也更新到新的扩展版本号

{% highlight JSON %}
{
  "name": "myexamplestore/sample-site",
  "description": "A sample site",
  "type": "project",
  "version": "1.0.0",
  "require": {
    "myexamplestore/product-bundle": "2.4.0-RC1",
    "myexamplestore/acme-extension": "~2.0"
    }
}
{% endhighlight %}
</li>

<li>Run <code>composer update</code>. Updates to core modules are returned as third-party extensions.
<br>
运行<code>composer update</code>。 核心模块的更新是作为第三方扩展返回
</li>

</ol>

<h3>Related topics</h3>
<a href="{{page.baseurl}}architecture/backward-compatibility.html">Backward compatibility</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/ABasics_intro.html">Architectural basics</a>

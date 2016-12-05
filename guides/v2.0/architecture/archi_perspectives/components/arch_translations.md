---
layout: default
group: arch-guide 
subgroup: Components 
title: 语言包
menu_title: 语言包
menu_order: 9
version: 2.0
github_link: architecture/components/arch_translations.md
redirect_from: /guides/v1.0/architecture/components/arch_translations.html
---

<h2 id="m2arch-translations-overview">Language packages and translation语言包和翻译 </h2>

Any text that is presented to the user can have several captions or labels on the control elements, notifications, and error messages.  By default, Magento renders all these phrases in English (`US`) language (`en_US`). But if you deploy a storefront in a different language (or use the Magento Admin panel in a different language), you can incorporate other dictionaries for translations. 

任何显示给用户的文本在控制元素、通知、错误信息上都会有一些标题或标签。默认地Magento使用英文（US）语言（en_US）渲染所有这些短语。但如果你在不同的语言布署网店（或在不同的语言使用管理后台界面），你可以合并其它字典进行翻译

You can use the language packages provided with Magento, create your own, or obtain packages from the community. Check out the language packages, modules, and themes available on Magento Marketplace. 

你可以使用Magento提供的语言包、创建你自己的、或从社区获得包。在Magento市场购买可获得的语言包、模块和主题

Creating a language package is part of the process of <i>localizing</i> your storefront. 

创建一个语言包是<i>本地化</i>你的网店的处理的一部分。

<h3>Magento language packages 语言包</h3>

A <i>language package</i> is  a collection of translation dictionaries for a particular language together with additional information that tells Magento how to process the information, including:

<i>语言包</i>是特定语言的一组翻译字典，加上告诉Magento如何处理信息的附加信息，包括：

* `.csv` file contains the actual strings that comprise the language dictionary. A translation dictionary is a comma-separated value (`.csv`) file with at least two columns: the original phrase in the `en_US` locale and a translation of that phrase to another locale.
* `.csv`文件包含实际的由语言字典组成的字符串。翻译字典是逗号分隔的数据（.CSV）文件有最少两列：en_US本地化的原始短语和另一个本地化翻译的短语。
* `composer.json` file contains any dependencies for the language package and a mapping to its defined locale.
* `composer.json` 文件包含任何语言包的依赖和它定义的本地化映射
* `language.xml` file, where you declare a language package and establish any inheritance rules, if you are installing multiple language packages. 
* `language.xml` 文件，如果你安装的是多语言包，它是你定义一个语言包和建立任何继承规则的文件。

<h3>About localization and internationalization 关于本地化和国际化</h3>
<i>Localization</i>  is the process of adapting a product or service to a particular language, culture, and preferred local display characteristics.  Ideally, a product or service is developed so that localization is relatively easy to implement.  For example, you might design technical illustrations for manuals in which the text can easily be changed to another language. 

<i>本地化</i> 是处理系统或服务适应于特定语言、文件和首先的地方显示特点。理想地，一个系统或服务是被开发的便于本地化。如你想为文本可很容易切换到另一个语言的手册设计工程说明图，

The process of structuring an application to support localization is termed <i>internationalization</i>. An internationalized product or service is easier to localize for a particular language than a product that has not been internationalized. The process of first enabling a product to be localized and then localizing it for different national audiences is also known as <i>globalization</i>.

组织一个应用程序支持本地方的处理的术语叫<i>国际化</i>.一个国际化的系统或服务比没有国际化的理容易为特定语言本地化。处理的第一步是开启一个产品可以被本地化然后为不同国家观众本地化它，也叫做<i>全球化</i>

For an overview of Magento translation-related issues,翻译相关问题查看 see <a href="{{page.baseurl}}frontend-dev-guide/translations/xlate.html">Translations overview</a>. 

Procedures for creating language packages and dictionaries are described in 创建语言包和字典的步骤描述于<a href="{{page.baseurl}}config-guide/cli/config-cli-subcommands-i18n.html#config-cli-subcommands-xlate-dict-trans">Translation dictionaries and language packages翻译字典和语言包</a>.

<h2 id="m2arch-related">相关专题</h2>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_intro.html">Modules</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_libraries.html">Libraries</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_themes.html">Themes</a>




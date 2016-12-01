---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: 技术栈
menu_title: 技术栈
menu_order: 2
version: 2.0
github_link: architecture/tech-stack.md
redirect_from: /guides/v1.0/extension-dev-guide/tech-stack.html
---

## Magento technology stack Magento技术栈

本页简要说明我们使用的技术。更多信息查看系统需求：

*	[Version 2.0.x]({{ site.gdeurl }}install-gde/system-requirements.html)
*	[Version 2.1.x]({{ site.gdeurl21 }}install-gde/system-requirements-tech.html)

Magento的高度模块化结构包括以下开源技术：

### Web服务

*	Apache
*	nginx

### PHP
*	Composer (PHP依赖包管理器)

### 数据库

*	MySQL
*	MySQL Percona

### HTTP加速器

*	Varnish

### 缓存存储

*	Redis
*	Memcache

### 搜索

* Solr (仅限Magento企业版)
* Elasticsearch (仅限Magento 企业版2.1.x )

### 其它技术

*	HTML5
*	CSS3 (LESS CSS 预编译器)
*	jQuery (主JavaScript库)
*	RequireJS (帮助按需加载JavaScript资源文件)
*	Knockout.js (使用MVC模式简化JavaScript UIs)
*	第三方库 (Zend Framework 1, Zend Framework 2, Symfony)
*	编码规范 PSR-0 (自动加载标准), PSR-1 (基本编码规范), and PSR-2 (代码风格指南), PSR-3, PSR-4

### Optional stack components附加栈组件

*	Varnish (缓存)
*	Redis (用于页面缓存)
*	Solr (搜索引擎)
*	Elasticsearch (搜索引擎)

Magento *compatible with but not supported兼容但不做支持* for:

*	HHVM 3.9 PHP 解释器

Magento also provides automated testing suites that include unit, integration, functional and performance test scripts, as well as JavaScript tests and tools for static code analysis. Components include PHPUnit for the unit test framework and Selenium for the functional test framework.

Magento也提供自动化测试组件包括单元、集成、功能和性能测试脚本，还有JS测试和表态代码分析工具。组件包括PHPUnit单元测试框架和Selenium功能测试框架

This framework is located in the `dev/tests` directory. The functional testing framework `mtf` can be found in a [separate repository](https://github.com/magento/mtf). For more information, see the [Functional Testing Framework]({{page.baseurl}}mtf/mtf_introduction.html) guide.

这个框架放在`dev/tests`目录。功能测试框架`mtf`可以 [分开的仓库](https://github.com/magento/mtf)找到。更多信息查看[功能测试框架]({{page.baseurl}}mtf/mtf_introduction.html)

#### 相关主题
<a href="{{page.baseurl}}architecture/archi_perspectives/ABasics_intro.html">Architectural basics</a>

---
layout: default
group: fedg
title: 本指南常用标记
menu_title: 本指南常用标记
menu_order: 2
version: 2.0
github_link: frontend-dev-guide/conventions.md
---

## Conventional notations for paths to modules and themes<br/>模块和主题常用标记

Magento application components, including modules, themes, and language packages technically can be located anywhere under the Magento root directory. This refers to both, Magento default and custom components. 

Magento应用程序组件，包括模块、主题和语言包从技术上讲可以放到根目录下任何位置。这里找到两个，Magento默认和自定义组件。

The following relative paths are used for modules and themes:

以下相对路径用于模块和主题：

**- `<theme_dir>`**

Theme directory. Usually used when talking about custom themes, or any theme in general.

主题目录。通常被使用是当提及自定义主题或任何普通主题。

For Magento out of the box frontend themes, the absolute path usually is one of the following:

对于Magento创建性的前端主题，绝对路径一般是下面的一个：

 - `app/design/frontend/Magento/<theme>`
 - `vendor/magento/theme-frontend-<theme>`

**- `<module_dir>`**

Module directory. When talking about a particular Magento module, also notation similar to the following is used: `<Magento_Checkout_module_dir>`

模块目录。当提及一个指定Magento模块，也使用符号类似如下：`<Magento_Checkout_module_dir>`

For Magento modules, usually one of the following:

对于Magento模块，通过使用：

 - `app/code/Magento/<Module>`
 - `vendor/magento/module-<module>-<name>`

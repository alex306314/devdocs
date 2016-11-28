---
layout: default
group: release-notes
subgroup: Release Notes
title: Magento CE 2.0.8 Release Notes
menu_title: Magento CE 2.0.8 Release Notes
menu_order: 15
version: 2.0

github_link: release-notes/ReleaseNotes2.0.8CE.md
---
*	TOC
{:toc}


## Magento Community Edition 2.0.8
We are pleased to present Magento Community Edition 2.0.8. This release includes  several functional fixes.


Backward-incompatible changes are documented in <a href="{{ page.baseurl }}release-notes/changes_2.0.html" target="_blank">Magento 2.0 Backward Incompatible Changes</a>.



### Fixed issues

#### Installation and upgrade

<!--- 51440 -->* Magento no longer throws a fatal error when you run the `setup upgrade` command in environments running PHP 7.0.5. 


#### Product creation
<!--- 53342 -->* Magento  no longer duplicates URL keys during the creation of a configurable product.

<!--- 50076 -->* Magento now supports GLOB_BRACE on non-GNU Linux systems. <a href="https://github.com/magento/magento2/issues/3490" target="_blank">(GITHUB-3490)</a> 



#### Miscellaneous
<!--- 50507 -->* You can now successfully reset the Product Attributes mass update Admin form.

<!--- 49212 -->* We've improved the implementation of the `Magento\Sales\Model\OrderRepository::getList()` function.  <a href="https://github.com/magento/magento2/issues/3018" target="_blank">(GITHUB-3018)</a> 

<!--- 46014 -->* Magento now displays error messages on the page where the error occurred. Previously, error messages invoked by actions on the login page were not displayed until you left that page.

<!--- 53814 -->* Magento now sends email using a store's specific email address when an Admin sends email. Previously, Magento would send email from the default instance email address instead of the store address.

<!--- 52448 -->* Magento now correctly displays the customer address on the storefront. Previously,  when you selected a default billing address when creating a new customer account, Magento would not display the  address.




### System requirements
Our technology stack is built on PHP and MySQL. Magento 2.0.1 and later supports:

* PHP 5.5.x, where x is 22 or greater

* PHP 5.6.x

* PHP 7.0.2 up to 7.1.0, except for 7.0.5

* MySQL 5.6 

For more information, see
[System Requirements]({{ site.baseurl }}magento-system-requirements.html){:target="_blank"}.

{% include install/releasenotes/ce_install_20.md %}


## Migration toolkits
The <a href="{{ page.baseurl }}migration/migration-migrate.html" target="_blank">Data Migration Tool</a> helps transfer existing Magento 1.x store data to Magento 2.x. This command-line interface includes verification, progress tracking, logging, and testing functions. For installation instructions, see  <a href="{{ page.baseurl }}migration/migration-tool-install.html" target="_blank">Install the Data Migration Tool</a>. Consider exploring or contributing to the <a href="https://github.com/magento/data-migration-tool" target="_blank"> Magento Data Migration repository</a>.

The <a href="https://github.com/magento/code-migration" target="_blank">Code Migration Toolkit</a> helps transfer existing Magento 1.x store extensions and customizations to Magento 2.0.x. The command-line interface includes scripts for converting Magento 1.x modules and layouts.

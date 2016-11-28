# Magento Developer Documentation 开发者文档

Welcome! This site contains the latest Magento developer documentation for ongoing Magento 2.x releases.

欢迎！ 这个网站包含magento 2.x 版本开者发文档

To contribute, please fork the `develop` branch.  

想做贡献， 请fork分支develop。

# Building this site 编译这个网站
To check your work before submitting a pull request, you can build this site locally using Jekyll.

在提交一个pull request前检查你的工作，可以在本地使用jekyll编译这个站点

*	Windows users _must_ build the site in a Vagrant container running on Virtual Box as discussed in more detail in the [Vagrant README](vagrant/README.md).

* Windows用户_必须_在VBox上跑的Vagrant容器中编译这个站点， 更多详细信息在[Vagrant README](vagrant/README.md)

	We use symbolic links (symlinks) in the `guides/v2.1` directory to link to topics that haven't changed since the 2.0.x release. Because symlinks aren't supported by Windows, you _cannot_ use the Windows environment; you must use a Linux environment.

  从2.0.x版我们在`guides/v2.1`目录使用符号链接链接到主题， 而windows不支付符号链接， 所以不能使用win环境，必须使用linux环境

*	Mac and Linux users can build this site locally using Jekyll or you can use Vagrant.

* Mac 和 Linux用户可以在本地使用jekyll编译这个站点或也可以用vagrant.

	Vagrant might be easier because the software runs in a container that isn't dependent on, and cannot conflict with, any other software installed on your computer.

  Vagrant或许更容易，因为运行在容器中的软件不会依赖或是与你的电脑原有软件冲突

## Build using Vagrant 使用Vagrant编译
For more information, see the [Vagrant README](vagrant/README.md). 更多信息查看[Vagrant README](vagrant/README.md)

## Requirements
## 需求
Currently, building this site requires:

当前编译这个站点需要：

*	Ruby 2.2
*	Jekyll 3.1

Use the Ruby bundler to get compatible versions of other dependencies.

使用Ruby bundler来获取其它依赖的兼容版本

## Build locally in Mac or Linux
## 在Mac或Linux本地编译

To build this site locally:

开始本地编译：

```bash
# Install dependencies
$ bundle install

# Visit http://localhost:4000 in your favorite browser!
$ bin/jekyll serve
```

If you have questions, open an issue and ask us. We're looking forward to hearing from you!

如果有问题可以新增一个issue来问我们， 我们很期待听到你的声音

*	<a href="https://twitter.com/MagentoDevDocs" class="twitter-follow-button" data-show-count="false">Follow @MagentoDevDocs</a>

*	<a href="mailto:DL-Magento-Doc-Feedback@magento.com">给我们发邮件E-mail</a>

*	<a href="http://devdocs.magento.com">访问我们文档网站</a>, 使用 [Jekyll](http://jekyllrb.com/)在github上编译的.

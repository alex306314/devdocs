# Magento开发者文档

欢迎！ 这个网站包含magento 2.x 版本开者发文档

想做贡献， 请fork分支develop。

# Building this site 编译这个网站

在提交一个pull request前检查你的工作，可以在本地使用jekyll编译这个站点

* Windows用户_必须_在VBox上跑的Vagrant容器中编译这个站点， 更多详细信息在[Vagrant README](vagrant/README.md)

  从2.0.x版我们在`guides/v2.1`目录使用符号链接链接到主题， 而windows不支付符号链接， 所以不能使用win环境，必须使用linux环境

*	Mac and Linux users can build this site locally using Jekyll or you can use Vagrant.

* Mac 和 Linux用户可以在本地使用jekyll编译这个站点或也可以用vagrant.

  Vagrant或许更容易，因为运行在容器中的软件不会依赖或是与你的电脑原有软件冲突

## Build using Vagrant 使用Vagrant编译
更多信息查看[Vagrant README](vagrant/README.md)

## Requirements
## 需求
Currently, building this site requires:

当前编译这个站点需要：

*	Ruby 2.2
*	Jekyll 3.1

使用Ruby bundler来获取其它依赖的兼容版本

## 在Mac或Linux本地编译

开始本地编译：

```bash
# Install dependencies
$ bundle install

# Visit http://localhost:4000 in your favorite browser!
$ bin/jekyll serve
```

如果有问题可以新增一个issue来问我们， 我们很期待听到你的声音

*	<a href="https://twitter.com/MagentoDevDocs" class="twitter-follow-button" data-show-count="false">Follow @MagentoDevDocs</a>

*	<a href="mailto:DL-Magento-Doc-Feedback@magento.com">给我们发邮件E-mail</a>

*	<a href="http://devdocs.magento.com">访问我们文档网站</a>, 使用 [Jekyll](http://jekyllrb.com/)在github上编译的.

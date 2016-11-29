# 本地布署devdocs

你可以使用这个Vagrant项目布署devdocs站点到本地。Vagrant使你可以在独立的虚拟主机中运行编译这个devdocs项目需要的所有软件。然后你可以从`/vagrant/devdoc`项目根目录运行Jekyll

# 重点

如果你之前使用Vagrant来克隆和更新devdocs站点， 我们_强烈建议_你在做更新前再次使用这个Vagrant项目克隆。最近我们把2.0分支重命名为`develop`。我们相信如果存在老的2.0分支会在你的git历史产生一些问题

## 安装需要的软件

在你的系统安装VBox和Vagrant软件

1. [Install VirtualBox](https://www.virtualbox.org/wiki/Downloads).
3. [Install Vagrant](https://www.vagrantup.com/).

## 定制项目

你可以在`Vagrantfile`修改如下参数：

- `NAME` 是虚拟主机的名称（默认：`magento-devdocs`）
- `HOST_PORT` 是本地端口， 让你可以从主机观察生成的站点
- `RAM` 是虚拟主机的内存容量（默认：1024M）
- `CPU` 是虚拟主机可以使用的最大CPU百分比（默认：50%）

## 仅限windows: 以超级管理员的身份运行Unix脚本和VBox

为了让符号链接起作用， win用户必须以超级管理员同时运行UNIX shell（如果git bash）和VBox。最简单的方式是如下修改应用程序快捷方式

1. 在你的桌面或**开始** > **所有程序**下右键你的应用
2. 弹出菜单点击**属性**
3. 属性面板点击*高级*
4. 勾选筛选框**以管理员身份运行**
5. 同意显示的提示保存更改

## 创建VM和环境

1. 使用终端， 进入目录`devdocs/vagrant`(也就是这个readme文件所在的目录)

 例如: `cd ~/vagrant/devdocs`

2. 输入`vagrant up`
3. 等待项目初始化及克隆仓库

    如果第一次运行这个命令会花费一些时间

## 输入Git命令并运行Jekyll

在Vagrant项目启动后，输入`vagrant ssh`使用SSH链接到你的项目。然后你可以fork devdocs仓库或使用任何编辑器作修改

当你准备好要预览你的修改时继续下一部分：

## 运行 Jekyll
使用下面的命令运行Jekyll:

    bin/jekyll serve --host=0.0.0.0

更多命令选项查看[Basic Usage](https://jekyllrb.com/docs/usage).

启动jekyll后在浏览器输入`http://127.0.0.1:4000`


## 有用的CLI脚本和命令

在终端所有命令都必须从包含Vagrantfile的目录运行

### 脚本

- 停止jekyll服务器（停止devdocs站点生成）

        vagrant ssh -c "kill $(ps aux | grep '[j]ekyll' | awk '{print $2}')"

- 运行Jekyll服务器. (生成devdocs站点.)

        vagrant ssh -c 'cd /vagrant/devdocs; jekyll serve --host=0.0.0.0'

- 重载Jekyll服务器. (生成devdocs站点.)

        vagrant ssh -c "kill $(ps aux | grep '[j]ekyll' | awk '{print $2}'); cd /jekyll/devdocs;jekyll serve --host=0.0.0.0"


### 命令

- 链接运行中的虚拟主机。你可以从`/vagrant/devdocs`目录在虚拟主机运行jekyll命令

        vagrant ssh

  中止链接输入：

        exit

- 中止运行的虚拟主机

        vagrant halt

- 启动和配置虚拟主机

        vagrant up

停止和移除虚拟主机

        vagrant destroy

- 重新加载虚拟主机使`Vagrantfile`参数修改生效

        vagrant reload

- 重新加载虚拟并使`Vagrantfile` 和 `bootstrap.sh`修改的参数都生效

        vagrant reload --provision

- 重新加载虚拟主机使`bootstrap.sh`修改参数生效

        vagrant provision

[更多 Vagrant 指令](https://www.vagrantup.com/docs/cli/up.html).

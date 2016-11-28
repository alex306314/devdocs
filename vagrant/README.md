# Deploy devdocs locally

# 本地布署devdocs

You can deploy devdocs site locally using this Vagrant project. Vagrant enables you to run the software needed to build the devdocs project in a self-contained virtual machine (VM). Our Vagrant project clones the devdocs repository. You can then run Jekyll from the `/vagrant/devdocs` project root.

你可以使用这个Vagrant项目布署devdocs站点到本地。Vagrant使你可以在独立的虚拟主机中运行编译这个devdocs项目需要的所有软件。然后你可以从`/vagrant/devdoc`项目根目录运行Jekyll

# IMPORTANT
# 重点
If you previously used Vagrant to clone and update the devdocs site, we _strongly recommend_ you clone it again using this Vagrant project before making further updates. We recently renamed the `2.0` branch to `develop`. We believe that having the old `2.0` branch in your Git history will cause issues.

如果你之前使用Vagrant来克隆和更新devdocs站点， 我们_强烈建议_你在做更新前再次使用这个Vagrant项目克隆。最近我们把2.0分支重全名为`develop`。我们相信如果存在老的2.0分支会在你的git历史产生一些问题

## Install required software
## 安装需要的软件
Install the VirtualBox and Vagrant software for your operating system:

在你的系统安装VBox和Vagrant软件

1. [Install VirtualBox](https://www.virtualbox.org/wiki/Downloads).
3. [Install Vagrant](https://www.vagrantup.com/).

## Customize the project
## 定制项目

You can change the following parameters in `Vagrantfile`:

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
 Example: `cd ~/vagrant/devdocs`
2. 输入`vagrant up`
3. 等待项目初始化及克隆仓库

    如果第一次运行这个命令会花费一些时间

## 输入Git命令并运行Jekyll
After your Vagrant project has started, enter `vagrant ssh` to connect to the project using SSH. From there, you can fork the devdocs repository and use any editor to make your changes.


When you're ready to preview your changes, continue with the next section.

## Run Jekyll
Use the following command to run Jekyll:

    bin/jekyll serve --host=0.0.0.0

For additional command options, see [Basic Usage](https://jekyllrb.com/docs/usage).

After Jekyll has started, go to `http://127.0.0.1:4000` in a web browser.


## Useful CLI scripts and commands

All commands must be run in the terminal from the directory that contains `Vagrantfile`.

### Scripts

- Stop Jekyll server. (Stops devdocs site generation.)

        vagrant ssh -c "kill $(ps aux | grep '[j]ekyll' | awk '{print $2}')"

- Run Jekyll server. (Generates devdocs site.)

        vagrant ssh -c 'cd /vagrant/devdocs; jekyll serve --host=0.0.0.0'

- Reload Jekyll server. (Regenerates devdocs site.)

        vagrant ssh -c "kill $(ps aux | grep '[j]ekyll' | awk '{print $2}'); cd /vagrant/devdocs; jekyll serve --host=0.0.0.0"


### Commands

- Connect to the running virtual machine. You can run Jekyll commands inside the virtual machine from the `/vagrant/devdocs` directory.

        vagrant ssh

  To terminate the connection, run the command:

        exit

- Shut down the running virtual machine

        vagrant halt

- Start and configure the virtual machine

        vagrant up

- Stop and remove the virtual machine

        vagrant destroy

- Reload virtual machine to apply changes in `Vagrantfile`

        vagrant reload

- Reload virtual machine to apply changes in `Vagrantfile` and `bootstrap.sh`

        vagrant reload --provision

- Reload virtual machine to apply changes in `bootstrap.sh`

        vagrant provision

[More Vagrant commands](https://www.vagrantup.com/docs/cli/up.html).

# WSL中运行Arch Linux
在所有官方支持得wsl Linux系统中，Arch使用起来是我感觉最完美的。目前Arch官方未支持wsl，但是我们可以自定义添加任意linux系统发行版（理论上）。
通过docker拉取官方linux系统镜像运行并导出，再导入wsl，从而实现任意Linux系统的添加。这是[微软官方教程链接](https://docs.microsoft.com/zh-cn/windows/wsl/use-custom-distro)。
# 以下是教程（docker）
也可以使用podman，效果一样
## 拉取Arch Linux 镜像
```
docker pull archlinux
```
## 创建容器，
```
docker run -it archlinux 
```
## 退出容器
```
exit
```
## 列出所有容器并找到Arch Linux 的容器ID
```
docker container ls -a
```
## 导出Arch Linux发行版
```
docker export c9e89339e9d2 > /home/ArchLinux.tar
```
## 导入发行版到wsl，命令格式:wsl --import <Distro> <InstallLocation> <FileName> 
## 记得创建对应文件夹（位置自定义）
```
wsl --import ArchLinux D:\ArchLinux\ D:\ArchLinux\ArchLinux.tar
```
## 查看安装的wsl 
```
wsl -l -v
```
## 启动并进入该系统
```
wsl -d ArchLinux
```
## 完成
## 扩展下，指定默认的分发版， wsl --setdefault(-s) <DistributionName> 
``` 
wsl -s ArchLinux
```
## 指定默认分发版之后，可以直接输入，wsl 命令默认就会进入ArchLinux这个分发版。
## 同理我们可以自定义制作其他linux发行版，因为缺少官方支持，可能会存在很多bug，目前使用最完美的是Arch Linux。这是Ubuntu官方的[Ubuntu22.04包](https://cloud-images.ubuntu.com/releases/22.04/release/ubuntu-22.04-server-cloudimg-arm64-wsl.rootfs.tar.gz),导入方式同理。这是我制作的tar文件：[Arch Linux](https://gxmwxhn-my.sharepoint.com/:u:/g/personal/gxm_mengying_tk/ERP5TJZ7SSlKmsLXFEVlltcBzga1MBH3wPrPY0eC-LxuCQ?e=EqJp5e)
ps:wsl可以和IntelliJ IDEA用来开发，减少了很多的复杂环境搭建。目前使用一切完美。

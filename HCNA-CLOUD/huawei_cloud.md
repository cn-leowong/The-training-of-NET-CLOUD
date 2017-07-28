## 华为云计算解决方案配置案例

> FusionSpher FusionCompute  FusionAccess FusionMana
FusionLogger FusionBackup

#### 服务器CNA搭建

1. 笔记本使用fusionCompute 配置网络安装服务端环境 加载cna镜像（基础代理服务==vmware esx）

2. 服务器重启 进入bios 开启cpu虚拟化 配置管理ip  选择网络引导pxe
raid1进入网络引导

3. 安装完成   root/Huawei@CLOUD8!
gandalf/Huawei@CLOUD8   212.201

#### 服务器VRM安装

205

1. 笔记本使用安装向导工具 加载ovf VRM模板 安装模板

2. 原始服务器存在逻辑分区 要删除相应的分区

#### 虚拟机创建


win

1. 配置参数 4411  disk01  精简 50

2. 放入iso镜像  安装操作系统 （不可关闭浏览器窗口）

3. ip 207

linux

1. 30GiB

2. iso 镜像安装   （不可关闭浏览器窗口）

3. ip 206

#### 虚拟机配置

```

一、windows2008：207
  1.安装pv驱动，关闭防火墙，配置固定ip地址
  2.安装AD活动目录，执行命令“dcpromo”,安装DNS，安装DHCP服务，配置DHCP服务。
  3.创建域用户：vdsadmin，加入域管理员组，创建itauser用户，创建vds组，把用户加入到组，创建vds OU。
  4.安装ITA组件，放入光盘：FusionAccess_Installer_Win_V100R005C20SPC100.iso，安装linux之后完成。
  5.添加linux主机DNS配置信息
  6.配置组策略

二、linux配置：206
  1.安装pv驱动
  2.执行“startTools”命令，安装gaussdb，wi，HDC，license软件，配置gaussDB，HA，浮动ip。

三、win7模板安装
  1.安装pv驱动，关闭防火墙，启用administrator用户
  2.放入光盘：FusionAccess_Mirror_V100R005C20SPC100
封装完整克隆模板 Huawei12#$
  3.链接克隆模板虚拟机制作：
    （1）：将虚拟机加入域，然后用本地用户administrator登录虚拟机。
    （2）：设置用户权限，将vds组加入users组，将vdsadmin用户加入administrators组
    （3）：封装链接克隆模板虚拟机环境
    （4）：设置组策略，允许users组本地登录

四、配置FusionAccess：
  1.登录：http://207:8081，默认账号密码
admin/Huawei123#,修改密码
  2.配置系统管理，进行初始化配置
  3.配置虚拟化环境，添加FusionComputer VRM主机地址，输入用户名密码vdisysman/VdiEnginE@234
  4.配置域环境，输入域名，ip地址，账号密码
  5.配置桌面环境：所有密码统一是：Huawei@123
    （1）：配置数据库信息，linux的ip地址
    （2）：配置ITA信息和DNS地址，windows2008地址
    （3）：配置License服务器地址：linux的ip地址
    （4）：配置Desktop信息：数据库ip地址：linux的ip，输入HDC的域名和ip，要求DNS中有解析信息
    （5）：WI配置：输入ip地址：linux的ip
  6.创建虚拟机组和桌面组，选择正确的虚拟机模板类型
  7.快速发放桌面虚拟主机


```


#### 测试与巡检

1. 使用wi地址登陆

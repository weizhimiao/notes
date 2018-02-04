## 系统要求

CentOS 6+ / Debian 6+ / Ubuntu 14.04 +

推荐 Debian 7 x64，这个是我一直使用的系统，我的脚本在这个系统上面出错率最低。


**Tips:**
> 注意：本脚本只是安装Aria2后端，安装后默认会启动，但是还需要前端面板配合使用，如 Aria2 Web UI 或 AriaNG


## 脚本版本

Ver: 1.1.4

## 安装步骤

执行下面的代码下载并运行脚本。

```
wget -N --no-check-certificate https://softs.fun/Bash/aria2.sh && chmod +x aria2.sh && bash aria2.sh
 
# 如果上面这个脚本无法下载，尝试使用备用下载：
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/aria2.sh && chmod +x aria2.sh && bash aria2.sh
```

运行脚本后会出现脚本操作菜单，选择并输入 1 就会开始安装。

## 使用说明

进入下载脚本的目录并运行脚本：
```
./aria2.sh
```

然后选择你要执行的选项即可。
```
Aria2 一键安装管理脚本 [vx.x.x]
-- Toyo | doub.io/shell-jc4 --
 
0. 升级脚本
————————————
1. 安装 Aria2
2. 卸载 Aria2
————————————
3. 启动 Aria2
4. 停止 Aria2
5. 重启 Aria2
————————————
6. 修改 配置文件
7. 查看 配置信息
8. 查看 日志信息
————————————
 
当前状态: 已安装 并 已启动
 
请输入数字 [0-8]:
```

## 其他操作

启动：`/etc/init.d/aria2 start`

停止：`/etc/init.d/aria2 stop`

重启：`/etc/init.d/aria2 restart`

查看状态：`/etc/init.d/aria2 status`

配置文件：`/root/.aria2/aria2.conf` （配置文件包含中文注释，但是一些系统可能不支持显示中文）

默认密匙：`doub.io`（如果你是从镜像域名doub.bid进来的，这个密匙会被镜像替换为 .bid ,自己改成 .io 即可）

下载目录：`/usr/local/caddy/www/aria2/Download`


## 其他说明

> 注意：本脚本只是安装Aria2后端，安装后默认会启动，但是还需要前端面板配合使用，如 Aria2 Web UI 或 AriaNG 


### 提示wget: unknown host “softs.fun” 之类的错误

这是无法解析我的域名，多半是DNS的问题，请更换DNS为谷歌DNS(以下两行一起复制 一起执行)。

```
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" > /etc/resolv.conf
```

### 提示 wget: command not found 的错误
这是你的系统精简的太干净了，wget都没有安装，所以需要安装wget。


```
# CentOS系统:
yum install -y wget
 
# Debian/Ubuntu系统:
apt-get install -y wget
```


### 升级脚本
升级脚本只需要运行脚本，然后选择并输入 0 回车即可，会自动检测最新版本并下载，当然重新下载脚本文件也可以，会自动覆盖原文件。

## 更新日志

### 2018年01月25日，版本 v1.1.4
- 1. 修复 当配置文件丢失时，无法卸载 Aria2 的问题。

### 2018年01月22日，版本 v1.1.3
- 1. 新增 一键修改 RPC密码、RPC端口 以及 文件下载位置 的功能（6. 修改 配置文件）。

- 2. 新增 查看 配置信息 功能（7. 查看 配置信息）。

### 2018年01月18日，版本 v1.1.2
- 1. 修复 Aria2 卸载不完全的问题（会导致下次安装提示已安装）。

### 2018年01月17日，版本 v1.1.1
- 1. 新增 Vim编辑器安装代码（6. 修改 配置文件 选项会用到，考虑到一些人服务器没安装，所以特别加上）。

### 2017年11月24日，版本 v1.1.0
- 1. 新增 启动/查看 Aria2 运行状态是会显示 Aria2 的简单配置信息。

- 2. 更新 Aria2安装方式为 预编译 安装方式。

- —— 以前是通过包管理器方式安装的Aria2，基本都是旧版本的包，这次改成 预编译 方式安装，就能直接安装最新的 Aria2 版本了，并且 CentOS 6 系统也支持安装了。

### 2017年09月05日，版本 v1.0.4
- 1. 优化 CentOS7系统 Aria2安装步骤，提高成功率。

### 2017年08月28日，版本 v1.0.3
- 1. 修复 上个版本 CentOS 系统判断不准确的问题。

### 2017年08月24日，版本 v1.0.2
- 1. 新增 CentOS 系统判断（CentOS6因为源没有Aria2包，所以不支持安装）。

### 2017年05月09日，版本 v1.0.1
- 1. 修复 检测安装状态的问题。

- 2. 修复 安装Aria2后，检测是否安装成功的问题。

### 2017年05月07日，版本 v1.0.0
- 1. 推出 正式版。


[转自：https://doub.io/shell-jc4/](https://doub.io/shell-jc4/)



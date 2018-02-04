


## 目录
- 介绍
- 先决条件
- 创建 `Password` 文件
- 配置 HTTP Basic Authentication 认证
- Basic Authentication 与 IP地址访问限制 相结合
- 完整示例

## 介绍
我们可以通过 用户名/密码 认证来限制对我们的网站或其某些部分的访问。 用户名和密码来自于一个由密码文件创建工具创建和填充的文件，例如 `apache-2 utils`。

HTTP基本认证还可以与其他访问限制方法结合使用，例如限制IP地址或地理位置访问。

## 先决条件

- NGINX Plus 或 NGINX
- 密码文件创建工具，例如 apache2-utils

## 创建 `Password` 文件

要创建 用户名 - 密码 对，请使用密码文件创建实用程序，例如 apache2-utils。

1、 安装 apache2-utils 工具
2、 创建密码文件 
```
$ sudo htpasswd -c /etc/xxx/.htpasswd user1
```
当您按Enter键时，系统将提示您输入user1的密码两次。
3、 以相同的方式创建其他用户密码对。在这种情况下，可以不使用 `-c` 标志：
```
$ sudo htpasswd /etc/xxx/.htpasswd user2
```
4、 查看创建好的 密码文件
```
$ cat /etc/xxx/.htpasswd
```
```
user1:$apr1$/woC1jnP$KAh0SsVn5qeSMjTtn0E9Q0
user2:$apr1$QdR8fNLT$vbCEEzDj7LyqCMyNpSoBh/
user3:$apr1$Mr5A0e.U$0j39Hp5FfxRkneklXaMrr/
```

## 配置 HTTP Basic Authentication 认证

1. 在要保护的位置内，指定 `auth_basic` 指令并为密码保护区域命名。 请求凭证时，该区域的名称将显示在用户名/密码对话窗口中：
```
location /status {                                       
    auth_basic “Administrator’s Area”;
    ....
}
```
2. 指定包含用户/密码对的.htpasswd文件的路径的 `auth_basic_user_file` 指令：
```
location /status {                                       
    auth_basic           “Administrator’s Area”;
    auth_basic_user_file /etc/apache2/.htpasswd; 
}
```
或者，可以通过基本身份验证来限制访问整个网站，但仍会公开某些网站区域。 在这种情况下，请指定 `auth_basic` 指令的`off`参数，用于取消上层配置的继承：
```
server {
    ...
    auth_basic           "Administrator’s Area";
    auth_basic_user_file conf/htpasswd;

    location /public/ {
        auth_basic off;
    }
}
```

## Basic Authentication 与 IP地址访问限制 相结合
HTTP基本认证可以有效地与IP地址的访问限制相结合。 

可以实施至少两种情况：
- 用户必须经过身份验证并具有有效的IP地址
- 用户必须经过身份验证，或者拥有有效的IP地址

1. 使用nignx access模块的allow和deny指令来允许或拒绝特定IP地址的访问：
```
location /status {
    ...
    deny 192.168.1.2;
    allow 192.168.1.1/24;
    allow 127.0.0.1;
    deny all;
}
```
只有192.168.1.1/24网络才能访问，不包括192.168.1.2地址。 请注意，allow和deny指令将按照它们定义的顺序应用。


2. 通过IP和HTTP认证的限制与满足指令相结合。

如果将指令设置为all，则如果客户端满足这两个条件，则授予访问权限。 如果将指令设置为any，则如果客户端满足至少一个条件，则访问被授予：
```
location /status {
    ...
    satisfy all;    

    deny  192.168.1.2;
    allow 192.168.1.1/24;
    allow 127.0.0.1;
    deny  all;

    auth_basic           "Administrator’s Area";
    auth_basic_user_file conf/htpasswd;
}
```

## 完整示例

下面的例子展示了如何通过简单的身份验证和IP地址的访问限制来保护您的状态区域：
```
http {
    server {
        listen 192.168.1.23:8080;
        root   /usr/share/nginx/html;

        location /status {
            status;
            satisfy all;

            deny  192.168.1.2;
            allow 192.168.1.1/24;
            allow 127.0.0.1;
            deny  all;

            auth_basic           “Administrator’s area;
            auth_basic_user_file /etc/apache2/.htpasswd; 
        }

        location = /status.html {
        }
    }
}
```
如果您输入与您的状态页面相对应的地址，首先，您将收到密码提示：

如果提供的名称和密码与密码文件中的名称和密码不匹配，则会出现“401需要授权”错误。


[RESTRICTING ACCESS WITH HTTP BASIC AUTHENTICATION](https://www.nginx.com/resources/admin-guide/restricting-access-auth-basic/#combine);

# 1. 【MySQL8.0安装过程】

## 1.1. 【安装过程】

> 从 MySQL5.7 开始，免安装版本没有 data 目录

1. step1. **初始化 data 目录**

    ```shell
    mysqld --initialize-insecure   #无密码的root账号
    
    mysqld --initialize
    # 有密码, 密码位于 data 文件夹中一个以 .err 结尾的文件里，其 “root@localhost:” 后面的字符即是密码
    
    mysqld --initialize --console
    # 有密码，在控制台直接打出
    ```

2. step2. **安装系统服务**：`mysqld --install [服务名]`  默认服务名为 “MySQL”

3. step3. **启动服务**：`net start mysql服务名`

4. step4. **测试**

    ```shell
    mysql -uroot          # 无密码时，可省略 -p 选项
    mysql -uroot -p       # 无密码时，在请输入密码栏中直接回车即可
    mysql -uroot -p密码    # 直接带上密码
    
    # 修改密码
    【方式1】mysqladmin -uroot -p旧密码 password 新密码
    【方式2】alter user root@localhost identified by "密码";
    【方式3】set password = '密码';
    
    select version();     #查看当前服务器的版本信息
    ```

## 1.2. 【配置文件】

> Windows 系统下为 my.ini

```shell
# 根目录中新建 my.ini 文件

[mysql]
port=3306
default-character-set=UTF8MB4
[mysqld]
basedir=C:\Develop\WAMP\mysql8.0
datadir=C:\Develop\WAMP\mysql8.0\data
port=3306
max_connections=200
character-set-server=UTF8MB4
default-storage-engine=INNODB
default_authentication_plugin=mysql_native_password
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
```

# 2. 【Apache 服务】

1. **编辑 httpd.conf**：将 `Define SRVROOT "/Apache24"`  双引号里面的路径改为 `C:\Develop\WAMP\Apache24`
2. **安装Apache服务**：`httpd -k install/uninstall/start`
3. **启动服务**：`net start Apache2.4`
4. **访问**：`127.0.0.1`
    * Apache安装后的默认主页的位置为: `/htdocs/`

# 3. 【php模块独立运行php代码】

* 方式1.**运行php代码**
    * 【格式】 `php -r "php脚本代码"`
    * 【范例】 `php -r "echo 'Hello World'";`

* 方式2.**运行php文件**
	* 【格式】 `php -f "php文件路径"`
	* 【范例】 `php -f "c:/users/yiyiq/desktop/Hello.php"`

# 4. 【配置Apache以运行php网页】

> **主配置文件**：`Apache24\conf\httpd.conf`   配置文件修改后，需重启 Apache

```shell

# 装载PHP模块
LoadModule php7_module "C:\Develop\WAMP\php7.2\php7apache2_4.dll"

# 指定php文件使用php模块执行
AddType application/x-httpd-php .php

# 指定php.ini的位置
PHPIniDir "C:\Develop\WAMP\PHP7.2"
```

1. **检测Apache配置文件语法**：`httpd -t`
2. **测试是否配置成功**：`<?php phpinfo();`

# 5. 【配置php的基本运行环境】

> **php配置文件**： 复制  `php.ini-development`  重命名为  `php.ini`

```shell
# 1.【配置时区】
php.ini
	↘ 【定位】;date.timezone =
	↘ 【改为】date.timezone = PRC
测试： echo date("Y-m-d H:i:s");

# 2.【配置数据库连接机制】

# 告诉PHP扩展模块文件的路径
【定位】; extension_dir = "ext"
【修改】extension_dir = "C:\Develop\WAMP\php7.2\ext"

# 启用 MySQL 模块
删除 “;extension=mysqli” 前面的分号

# 测试
$con=mysqli_connect("localhost","root","123456");
var_dump($con);
```

> 1.  **连接数据库时报错：The server requested authentication method unknown to the client**
>
>     * MySQL8 默认使用了新的密码验证插件：caching_sha2_password
>     * 当前 PHP 版本中所带的 mysqlnd 无法支持这种验证
>     * `ALTER USER root@localhost IDENTIFIED WITH mysql_native_password BY 'new_password';`

# 6. 【虚拟主机配置】

## 6.1. 【端口更改】

>  定位到该行：`Listen 80`

## 6.2. 【配置文件夹访问权限】

1. **将当前主机中的某个文件夹，对外以某个域名的方式展现出来**

    * **站点名字**：`ServerName www.yyq.com` 
    * **站点的文件夹位置**：`DocumentRoot "C:\Users\yiyiq\Documents\MyCode\PHP"`

2. **访问**： `http://www.yyq.com/` 

    * **报错**：`Forbidden: You don't have permission to access / on this server`
    * **原因**：一个文件夹的访问，是有权限的。初始的站点所对应的文件夹，安装的时候已经设置好权限了

3. **配置文件夹访问权限**

    ```shell
    # apache2.4的配置方法
    
    <Directory "C:\Users\yiyiq\Documents\MyCode\PHP">
           Options Indexes FollowSymLinks     #当无可显示网页时，显示文件列表
           Require all granted                #允许所有请求访问资源
    </Directory>
    
    附:
    Require all granted               #允许所有请求访问资源
    Require all denied                #拒绝所有请求访问资源
    Require host google.com           #只允许来自特定域名主机的访问请求
    Require ip 192.120 192.168.100 192.168.1.1        #只允许来自特定IP或IP段的访问请求
    Require not ip 192.168.1.1        #拒绝来自特定IP或IP段的访问请求
    ```

## 6.3. 【设定 默认网页】

```shell
<IfModule dir_module>
       #这里是对全局(所有站点，所有文件夹)都起作用
       DirectoryIndex index.html index.php
</IfModule>

对于没有明确网页的访问请求，会按顺序从前往后找这些文件
如果最终都没找到，那此时Options中的Indexes就发挥作用了: 显示该文件夹中的所有文件和文件夹
可将 DirectoryIndex 设置项放在一个单独的站点或单独的文件夹中，则只对该单独的站点或单独的文件夹起作用

<Directory "C:\Users\yiyiq\Documents\MyCode\PHP">
       ...
       #只对该文件夹(及其下属文件夹)有效
       DirectoryIndex index.html index.php
</Directory>
```

## 6.4. 【主机别名设置】

* **使用多种形式访问一个站点**：`http://www.abc.com`  、`http://abc.com` ...
    * 相当于 “2个站点（主机名）” 但访问的是一个内容
* **此时就需要使用主机别名来实现**：`ServerAlias 别名1 别名2 别名N`

## 6.5. 【文件夹访问控制的文件控制方式】

* 通常，我们在配置文件中，使用 Directory 配置项来控制文件夹的访问权限

* 其实也可以使用一个独立的文件来控制某文件夹的访问权限

* 该文件名必须是：`.htaccess` ，只有后缀和点号（无文件名部分）

* 该文件必须放在要被控制访问权限的文件夹中（不同的文件夹可以放不同的该文件）

* 其 “上级文件夹” （通常是 Directory 设定中的文件夹）必须使用如下代码允许 `.htaccess` 发挥作用

    ```shell
    <Directory "...">
           ...
           #允许.htaccess文件发挥作用
           AllowOverride  All
    </Directory>
    
    # .htaccess 文件中出现的代码，几乎可以跟 Directory 设定中出现的代码一样
    # 如果 .htaccess 文件有效，则其设置会覆盖其上级设置
    # 此 .htaccess 文件修改后可以立即发挥作用，无需重启apache
    ```

## 6.6. 【目录别名设置 Alias】
* 目录别名也叫虚拟目录
* 一个站点是一个文件夹，该文件夹可有下级文件夹
* 实际存在的下级目录，可按正常的层级关系进行访问

    ```shell
    http://www.php.com/             # 根文件夹 (即站点目录)
    http://www.php.com/day1/        # 根文件夹中的day1目录
    http://www.php.com/day1/abc/    # 根文件夹中的day1目录中的abc目录

    # 在一个站点中，如果不存在某个文件夹，则可通过配置项，来做到 “对外” 看起来却存在一样
    # 比如 http://www.php.com/soft/     # 假设站点中不存在soft目录
    ```

* 虚拟目录配置

    ```shell
    <IfModule alias_module>
           Alias /soft "c:\users\yiyiq\desktop\"
    </IfModule>
    
    # 访问: http://www.yyq.com/soft => 报错，禁止访问
    
    # 设置文件夹访问权限
    <Directory "c:\users\yiyiq\desktop">
           Options Indexes FollowSymLinks
           Require all granted
    </Directory>
    
    # 访问: http://www.yyq.com/soft => 正常访问
    # 通过该技术，可将一个站点之外的 “网页/数据/内容” 也呈现在当前站点中
    ```
    

## 6.7. 【多站点配置】

1. **引入多站点配置文件**
    * **定位**：`# Include conf/extra/httpd-vhosts.conf`
    * **启用**：删除 `#` 号

2. **编辑**： `conf/extra/httpd-vhosts.conf` 
	* 一旦进行多站点配置，则原来 httpd.conf 中的默认站点配置就失效了
	
	```shell
	# 站点1
	<VirtualHost *:80>
	       ServerName www.yyq.com
	       ServerAlias yyq.com
	       DocumentRoot "C:\Users\yiyiq\Documents\MyCode\PHP"
	       <Directory "C:\Users\yiyiq\Documents\MyCode\PHP">
	               Options Indexes FollowSymLinks
	               Require all granted
	               AllowOverride All
	               DirectoryIndex index.html index.php
	       </Directory>
	</VirtualHost>
	
	# 站点N
	<VirtualHost *:80>
	       ...
	</VirtualHost>
	```

配置
=====
### 漂亮滴URL
Laravel 使用 public/.htaccess 文件来允许URL们经过 index.php 重写。
如果你的web服务器是Apache的话，记得要打开mod_rewrite模块(在httpd.conf中取消LoadModule rewrite_module modules/mod_rewrite.so的注释)

如果你的Apache不支持.htaccess文件的话，可以试试下面这种方法：
```
		Options +FollowSymLinks
		RewriteEngine On
		RewriteCond %{REQUEST_FILENAME} !-d
		RewriteCond %{REQUEST_FILENAME} !-f
		RewriteRule ^ index.php [L]
```
补充一下在windows下的做法：
```
NameVirtualHost 127.0.0.1
<VirtualHost 127.0.0.1>
    DocumentRoot "C:/newsrc/test/blog/public"
    ServerName blog
	<Directory "C:/newsrc/test/blog/public">
		AllowOverride all
		Allow from all
		Options +FollowSymLinks
		RewriteEngine On
		RewriteCond %{REQUEST_FILENAME} !-d
		RewriteCond %{REQUEST_FILENAME} !-f
		RewriteRule ^ index.php [L]
	</Directory>
</VirtualHost>
```
同时在hosts文件中加上
```
127.0.0.1	blog
```

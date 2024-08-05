# php://filter协议	

对于类似源码，可利用php://filter协议绕过读取文件内容

```php
<?php
include("$file");
当看到ini_set("allow_url_include","on");设置为on，
那我们可以想到可以进行文件包含用伪协议来读取flag.php这个文件
```

写入payload

```php
<?php
include('php://filter/read=convert.base64-encode/resource=flag.php');
```



## 1.定义

​	php://filter 是一种元封装器， 设计用于数据流打开时的[筛选过滤](https://www.php.net/manual/zh/filters.php)应用。 这对于一体式（all-in-one）的文件函数非常有用，类似 [readfile()](https://www.php.net/manual/zh/function.readfile.php)、 [file()](https://www.php.net/manual/zh/function.file.php) 和 [file_get_contents()](https://www.php.net/manual/zh/function.file-get-contents.php)， 在数据流内容读取之前没有机会应用其他过滤器。

​	常用payload格式：

```
php://filter/convert.base64-encode/resource=flag.php
php://filter/<此处为过滤器>/resource=<此处为数据源	>
```

直接「读取」数据源的内容，resource 参数必须位于 php://filter  的末尾，并指定需要过滤筛选的数据流。

## 2.php://filter参数简单总结

### 2.1 参数

| php://filter 参数         | 描述                                                         |
| ------------------------- | ------------------------------------------------------------ |
| resource=<要过滤的数据流> | 必须项。它指定了你要筛选过滤的数据流。                       |
| read=<读链的过滤器>       | 可选项。可以设定一个或多个过滤器名称，以管道符（*\ *）分隔   |
| write=<写链的过滤器>      | 可选项。可以设定一个或多个过滤器名称，以管道符（\ ）分隔     |
| <; 两个链的过滤器>        | 任何没有以 read= 或 write= 作前缀的筛选器列表会视情况应用于读或写链。 |

### 2.2 过滤器

PHP 过滤器用于对来自非安全来源的数据（比如用户输入）进行验证和过滤。

分成四种过滤器

- #### [2.2.1字符串过滤器](https://www.php.net/manual/zh/filters.string.php)

  string.rot13

  string.toupper/string.tolower

- #### [2.2.2转换过滤器](https://www.php.net/manual/zh/filters.convert.php)

  

- #### [2.2.3压缩过滤器](https://www.php.net/manual/zh/filters.compression.php)

  

- #### [2.2.4加密过滤器](https://www.php.net/manual/zh/filters.encryption.php)
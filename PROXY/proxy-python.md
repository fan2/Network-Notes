## python 代理

### urllib 代理

以下摘自 [package-control-st3.py](https://gist.github.com/albur/6319642)：

```Python
urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler({'http': 'http://USER:PASS@HOST:PORT', 'https': 'https://USER:PASS@HOST:PORT'})) );
```

urllib.request.install_opener 调用 build_opener 时创建 ProxyHandler 可设置 http/https 代理参数。

### pip 代理

[Using pip behind a proxy](https://stackoverflow.com/questions/14149422/using-pip-behind-a-proxy)  
[How to easy_install and pip through a proxy](https://www.jacobtomlinson.co.uk/2014/11/25/easy-install-and-pip-through-a-proxy/)  
[Install Python modules with Pip behind a proxy](https://www.internalpointers.com/post/install-python-modules-pip-behind-proxy)  

```Shell
# pip -h；raspbian/CentOS 同此。
faner@MBP-FAN:~|⇒  pip3 -h

Usage:   
  pip <command> [options]

Commands:

General Options:

  --proxy <proxy>             Specify a proxy in the form [user:passwd@]proxy.server:port.

```

执行 `pip(3) install` 时可通过指定 `--proxy` 选项设置代理。

```Shell
# it will works for Ubuntu?
sudo pip --proxy http://web-proxy.mydomain.com install somepackage
```

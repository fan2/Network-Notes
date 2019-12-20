## apt(Debian) 代理

[AptConf](https://wiki.debian.org/AptConf)  
[Configure proxy for APT?](https://askubuntu.com/questions/257290/configure-proxy-for-apt)  
[How to Configure apt-get behind proxy server](https://ubuntuforums.org/showthread.php?t=2011511)  

执行 `man apt.conf` 可查看详细的 apt 配置描述。

```Shell
# man apt.conf

APT.CONF(5)                                  APT                                  APT.CONF(5)

NAME
       apt.conf - Configuration file for APT

DESCRIPTION
       /etc/apt/apt.conf is the main configuration file shared by all the tools in the APT
       suite of tools, though it is by no means the only place options can be set. The suite
       also shares a common command line parser to provide a uniform environment.

       When an APT tool starts up it will read the configuration files in the following
       order:

        1. the file specified by the APT_CONFIG environment variable (if any)


THE ACQUIRE GROUP

       http
           http::Proxy sets the default proxy to use for HTTP URIs. It is in the standard
           form of http://[[user][:pass]@]host[:port]/. Per host proxies can also be
           specified by using the form http::Proxy::<host> with the special keyword DIRECT
           meaning to use no proxies. If no one of the above settings is specified,
           http_proxy environment variable will be used.

       https
           The Cache-control, Timeout, AllowRedirect, Dl-Limit and proxy options work for
           HTTPS URIs in the same way as for the http method, and default to the same values
           if they are not explicitly set. The Pipeline-Depth option is not yet supported.

```

/etc/apt/apt.conf 中可配置代理：

```Shell

Acquire::http::proxy "http://lgn:pwd@192.168.1.254:8080/";
Acquire::https::proxy "http://lgn:pwd@192.168.1.254:8080/";

# Acquire::http::Proxy "http://yourproxyaddress:proxyport";
# Acquire::http::Proxy "http://username:password@yourproxyaddress:proxyport";
```

## yum(REHL) 代理

[10. Using yum with a Proxy Server](https://www.centos.org/docs/5/html/yum/sn-yum-proxy-server.html)  
[2.2 Yum Configuration](https://docs.oracle.com/cd/E37670_01/E37355/html/ol_yum_config.html) / [2.2.1 Configuring Use of a Proxy Server](https://docs.oracle.com/cd/E37670_01/E39381/html/ol_proxy_config.html)  
[How to enable Proxy Settings for Yum Command](https://www.linuxtechi.com/proxy-settings-yum-command-on-rhel-centos-servers/) on [RHEL / CentOS / Fedora Servers](https://www.cyberciti.biz/faq/centos-redhat-fedora-linux-using-yum-with-a-proxy-server/)  

specify the proxy setting in `/etc/yum.conf` as shown in the following example.

```Shell
proxy=http://proxysvr.yourdom.com:3128
proxy_username=yumacc
proxy_password=clydenw 
```

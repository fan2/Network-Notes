
## Windows 设置代理

Windows 下的 **Internet 选项** 可设置全局代理？

[Windows 下如何全局走 socks？](https://www.v2ex.com/t/184543)  
[shadowsocks-windows](https://github.com/shadowsocks/shadowsocks-windows)  

- [Win7 64位系统全局代理所有程序都有效?](https://github.com/shadowsocks/shadowsocks-windows/issues/530)  
- [windows终端命令行下如何使用代理？](https://github.com/shadowsocks/shadowsocks-windows/issues/1489)  

> SS 全局代理只针对使用 IE 代理的程序才全局，不是像 VPN 那样的全局，要实现VPN那样的功能，要用Proxifier。  

### Internet

### cmd

```Shell
set http_proxy=http://host:port
set https_proxy=http://host:port
```

Window 没有这个环境变量，要到 IE 设置 或 控制面板 中的 **Internet 选项** 里设置代理？

Windows cmd 代理：[设置](http://blog.csdn.net/lovelyelfpop/article/details/69586366) 与 [取消](http://jinbitou.net/2017/09/21/2534.html)  
[CMD 和 Git 中的代理设置](http://www.cnblogs.com/terrylin/p/3296428.html)  
[如何对windows的命令行设置代理IP？](https://www.zhihu.com/question/23059121)  
[windows环境下设置命令行CMD、Git、NPM和Bowser代理设置](http://www.it610.com/article/5167917.htm)  

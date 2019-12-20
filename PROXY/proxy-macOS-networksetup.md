
## networksetup

系统网络管理命令 networksetup：

```Shell
# man networksetup
NETWORKSETUP(8)           BSD System Manager's Manual          NETWORKSETUP(8)

NAME
     networksetup -- configuration tool for network settings in System Preferences.
```

执行 `networksetup -printcommands` 可查看 networksetup 子命令。

执行 `networksetup -help` 可查看子命令的帮助信息（Display these help listings）：

```Shell
# networksetup -help

# 按顺序列举设备信息（Hardware Port、Device）
Usage: networksetup -listnetworkserviceorder
    Display services with corresponding port and device in order they are tried for connecting
    to a network. An asterisk (*) denotes that a service is disabled.

# 设备 Hardware Port 列表，作为其他命令的 <networkservice> 参数
Usage: networksetup -listallnetworkservices
	Display list of services. An asterisk (*) denotes that a network service is disabled.

# 列举设备信息（Hardware Port、Device、Ethernet Address），例如无线网卡信息：`Hardware Port: Wi-Fi Device: en0`
Usage: networksetup -listallhardwareports
	Display list of hardware ports with corresponding device name and ethernet address.

# 获取具体某个设备的网络连接信息
Usage: networksetup -getinfo <networkservice>
	Display IPv4 address, IPv6 address, subnet mask,
	router address, ethernet address for <networkservice>.

# 获取具体某个设备的 DNS 服务器信息
Usage: networksetup -getdnsservers <networkservice>
	Display DNS info for <networkservice>.

# 为某个设备设置 DNS 服务器
Usage: networksetup -setdnsservers <networkservice> <dns1> [dns2] [...] 
	Set the <networkservice> DNS servers to <dns1> [dns2] [...]. Any number of dns servers can be
	specified. Specify "Empty" for <dns1> to clear all DNS entries.

Usage: networksetup -getnetworkserviceenabled <networkservice>
    Display whether a service is on or off (enabled or disabled).

Usage: networksetup -setnetworkserviceenabled <networkservice> <on off>
    Set <networkservice> to either <on> or <off> (enabled or disabled).

Usage: networksetup -getMTU <hardwareport or device name>
    Get the MTU value for hardwareport or device specified.

Usage: networksetup -setMTU <hardwareport or device name> <value>
    Set MTU for hardwareport or device specified.

Usage: networksetup -listvalidMTUrange <hardwareport or device name>
    List the valid MTU range for hardwareport or device specified.

```

### networkservices

查看本机安装的设备硬件端口和名称：

```Shell
# 列举设备，只查看设备的 Hardware Port 信息
faner@MBP-FAN:~|⇒  networksetup -listallnetworkservices
An asterisk (*) denotes that a network service is disabled.
USB-Serial Controller
Wi-Fi
Thunderbolt Bridge
Thunderbolt Ethernet
Bluetooth PAN

# 列举设备，查看设备的 Hardware Port 和 Device 信息
faner@MBP-FAN:~|⇒  networksetup -listnetworkserviceorder
An asterisk (*) denotes that a network service is disabled.
(1) USB-Serial Controller
(Hardware Port: USB-Serial Controller, Device: usbserial)

(2) Wi-Fi
(Hardware Port: Wi-Fi, Device: en0)

(3) Thunderbolt Bridge
(Hardware Port: Thunderbolt Bridge, Device: bridge0)

(4) Thunderbolt Ethernet
(Hardware Port: Thunderbolt Ethernet, Device: en5)

(5) Bluetooth PAN
(Hardware Port: Bluetooth PAN, Device: en3)
```

### proxy

执行 `networksetup -help | grep proxy` 可查看代理相关的操作接口。

```Shell
# Auto Proxy Discovery
## 获取`自动发现代理`的开关状态
Usage: networksetup -getproxyautodiscovery <networkservice>
    Display whether Proxy Auto Discover is on or off for <network service>.

## 设置`自动发现代理`的开关
Usage: networksetup -setproxyautodiscovery <networkservice> <on off>
    Set Proxy Auto Discovery to either <on> or <off>.

# Automatic Proxy Configuration
## 设置`自动代理配置`的URL
Usage: networksetup -setautoproxyurl <networkservice> <url>
    Set proxy auto-config to url for <networkservice> and enable it.

## 获取`自动代理配置`的URL
Usage: networksetup -getautoproxyurl <networkservice>
    Display proxy auto-config (url, enabled) info for <networkservice>.

## 设置`自动代理配置`的开关
Usage: networksetup -setautoproxystate <networkservice> <on off>
    Set proxy auto-config to either <on> or <off>.

# Web Proxy(HTTP)
## 获取`网页代理(HTTP)`配置信息
Usage: networksetup -getwebproxy <networkservice>
    Display Web proxy (server, port, enabled value) info for <networkservice>.

## 设置`网页代理(HTTP)`信息
Usage: networksetup -setwebproxy <networkservice> <domain> <port number> <authenticated> <username> <password>
    Set Web proxy for <networkservice> with <domain> and <port number>. Turns proxy on. Optionally, specify <on> or <off> for <authenticated> to enable and disable authenticated proxy support. Specify <username> and <password> if you turn authenticated proxy support on.

## 设置`网页代理(HTTP)`的开关
Usage: networksetup -setwebproxystate <networkservice> <on off>
    Set Web proxy to  either <on> or <off>.

# Secure Web Proxy(HTTPS)
## 获取`安全网页代理(HTTPS)`配置信息
Usage: networksetup -getsecurewebproxy <networkservice>
    Display Secure Web proxy (server, port, enabled value) info for <networkservice>.

## 设置`安全网页代理(HTTPS)`信息
Usage: networksetup -setsecurewebproxy <networkservice> <domain> <port number> <authenticated> <username> <password>
    Set Secure Web proxy for <networkservice> with <domain> and <port number>. Turns proxy on. Optionally, specify <on> or <off> for <authenticated> to enable and disable authenticated proxy support. Specify <username> and <password> if you turn authenticated proxy support on.

## 设置`安全网页代理(HTTPS)`开关
Usage: networksetup -setsecurewebproxystate <networkservice> <on off>
    Set SecureWeb proxy to  either <on> or <off>.

# SOCKS Proxy
## 获取`SOCKS 代理`配置信息
Usage: networksetup -getsocksfirewallproxy <networkservice>
    Display SOCKS Firewall proxy (server, port, enabled value) info for <networkservice>.

## 设置`SOCKS 代理`信息
Usage: networksetup -setsocksfirewallproxy <networkservice> <domain> <port number> <authenticated> <username> <password>
    Set SOCKS Firewall proxy for <networkservice> with <domain> and <port number>. Turns proxy on. Optionally, specify <on> or <off> for <authenticated> to enable and disable authenticated proxy support. Specify <username> and <password> if you turn authenticated proxy support on.

## 设置`SOCKS 代理`开关
Usage: networksetup -setsocksfirewallproxystate <networkservice> <on off>
    Set SOCKS Firewall proxy to  either <on> or <off>.

```

执行 `networksetup -getautoproxyurl Wi-Fi` 查看无线网卡（Wi-Fi）的 `自动代理配置` 的 URL 信息：

```Shell
faner@MBP-FAN:~|⇒  networksetup -getautoproxyurl Wi-Fi
URL: http://<host>[:port]/proxy.pac
Enabled: Yes
```

执行 `networksetup -getwebproxy Wi-Fi` 查看无线网卡（Wi-Fi）的 `网页代理(HTTP)` 的配置信息：

```Shell
faner@MBP-FAN:~|⇒  networksetup -getwebproxy Wi-Fi
Enabled: Yes
Server: <host>
Port: <port>
Authenticated Proxy Enabled: 0
```

执行 `networksetup -getsocksfirewallproxy Wi-Fi` 查看无线网卡（Wi-Fi）的 `SOCKS 代理` 配置信息：

```Shell
# 获取 SOCKS 代理
faner@MBP-FAN:~|⇒  networksetup -getsocksfirewallproxy Wi-Fi
Enabled: Yes
Server: 127.0.0.1
Port: 1080
Authenticated Proxy Enabled: 0
```

#### 设置 HTTP/HTTPS 代理

为系统设置 whistle 代理，以便调试 Safari：

```Shell
# 禁用 PAC 自动代理
faner@MBP-FAN:~|⇒  networksetup -setautoproxystate Wi-Fi off

# 启用 HTTP 代理
faner@MBP-FAN:~|⇒  networksetup -setwebproxy Wi-Fi 127.0.0.1 8899
faner@MBP-FAN:~|⇒  networksetup -setwebproxystate Wi-Fi on

# 启用 HTTPS 代理
faner@MBP-FAN:~|⇒  networksetup -setsecurewebproxy Wi-Fi 127.0.0.1 8899
faner@MBP-FAN:~|⇒  networksetup -setsecurewebproxystate Wi-Fi on

# 查看代理配置
faner@MBP-FAN:~|⇒  scutil --proxy
<dictionary> {
  ExceptionsList : <array> {
    0 : *.local、169.254/16
  }
  FTPPassive : 1
  HTTPEnable : 1
  HTTPPort : 8899
  HTTPProxy : 127.0.0.1
  HTTPSEnable : 1
  HTTPSPort : 8899
  HTTPSProxy : 127.0.0.1
  ProxyAutoConfigEnable : 0
}
```

> 如果是有线网卡，需将 `Wi-Fi` 替换为 `Ethernet`。

**分3组命令执行**：

```Shell
$ networksetup -setautoproxystate Wi-Fi off;
$ networksetup -setwebproxystate Wi-Fi on && networksetup -setwebproxy Wi-Fi 127.0.0.1 8899;
$ networksetup -setsecurewebproxystate Wi-Fi on && networksetup -setsecurewebproxy Wi-Fi 127.0.0.1 8899;
```

> 可用 `;` 继续将以上3行合并成一行（一句）执行。

#### 恢复 PAC 自动代理配置

设置自动代理脚本：`http://127.0.0.1:8090/proxy.pac`：

```Shell
# 禁用 HTTP 代理
faner@MBP-FAN:~|⇒  networksetup -setwebproxystate Wi-Fi off
# 禁用 HTTPS 代理
faner@MBP-FAN:~|⇒  networksetup -setsecurewebproxystate Wi-Fi off

# 启用 PAC 自动代理
faner@MBP-FAN:~|⇒  networksetup -setautoproxyurl Wi-Fi http://127.0.0.1:8090/proxy.pac
faner@MBP-FAN:~|⇒  networksetup -setautoproxystate Wi-Fi on

# 查看代理配置
faner@MBP-FAN:~|⇒  scutil --proxy
<dictionary> {
  ExceptionsList : <array> {
    0 : *.local、169.254/16
  }
  FTPPassive : 1
  HTTPEnable : 0
  HTTPSEnable : 0
  ProxyAutoConfigEnable : 1
  ProxyAutoConfigURLString : http://127.0.0.1:8090/proxy.pac
}
```

**分2组命令执行**：

```Shell
networksetup -setwebproxystate Wi-Fi off;networksetup -setsecurewebproxystate Wi-Fi off
networksetup -setautoproxystate Wi-Fi on;networksetup -setautoproxyurl Wi-Fi http://127.0.0.1:8090/proxy.pac
```

> 可用 `;` 继续将以上2行合并成一行（一句）执行。

一般只是使能 ProxyAutoConfigEnable 开关，不会经常修改 ProxyAutoConfigURLString，setautoproxyurl 可选。

#### 禁用所有代理

分3组命令执行：

```Shell
# 禁用 HTTP 代理
networksetup -setwebproxystate Ethernet off;
# 禁用 HTTPS 代理
networksetup -setsecurewebproxystate Ethernet off;
# 禁用 PAC 自动代理
networksetup -setautoproxystate Ethernet off;
```

可用 `;` 拼接合成一句命令执行：

```Shell
networksetup -setwebproxystate Ethernet off;networksetup -setautoproxystate Ethernet off;networksetup -setsecurewebproxystate Ethernet off;
```

## scutil

除了强大的 **networksetup** 命令可用于查看设置网络配置（包括代理）外，还可以使用 **scutil** 命令来查看代理等网络配置信息。

```Shell
# scutil --help
faner@MBP-FAN:~|⇒  scutil --help
usage: scutil
	interactive access to the dynamic store.

   or: scutil --proxy
	show "proxy" configuration.

   or: scutil --nwi
	show network information

# man scutil
faner@MBP-FAN:~|⇒  man scutil

SCUTIL(8)                 BSD System Manager's Manual                SCUTIL(8)

NAME
     scutil -- Manage system configuration parameters

OPTIONS

     --proxy
         Reports the current proxy configuration.
```

以下为 `自动代理配置`（Automatic Proxy Configuration）信息

```Shell
# <host> 为代理的 domain 或 IP 地址，端口可选。
faner@MBP-FAN:~|⇒  scutil --proxy
<dictionary> {
  ProxyAutoConfigEnable : 1
  ProxyAutoConfigURLString : http://<host>[:port]/proxy.pac
}
```

以下为 `网页代理(HTTP)`（Web Proxy(HTTP)）配置信息：

```Shell
# <host> 为代理的 domain 或 IP 地址
faner@MBP-FAN:~|⇒  scutil --proxy
<dictionary> {
  HTTPEnable : 1
  HTTPPort : <port>
  HTTPProxy : <host>
}
```

以下为 `SOCKS 代理`（SOCKS Proxy）配置信息：

```Shell
faner@MBP-FAN:~|⇒  scutil --proxy
<dictionary> {
  HTTPEnable : 0
  HTTPSEnable : 0
  ProxyAutoConfigEnable : 0
  SOCKSEnable : 1
  SOCKSPort : 1080
  SOCKSProxy : 127.0.0.1
}
```

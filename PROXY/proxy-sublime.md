## Sublime Text 设置代理

控制面板（<kbd>⌘</kbd><kbd>⇧</kbd><kbd>P</kbd>）输入 Preferences: Package Control Settings - Default 打开 Package Control 默认配置文件：

`~/Library/Application Support/Sublime Text 3/Packages/Package Control/Package Control.sublime-settings`

其中有关于 **channels**、**repositories**、**代理** 相关的配置参数说明：

```json
	// A list of URLs that each contain a JSON file with a list of repositories.
	// The repositories from these channels are placed in order after the
	// repositories from the "repositories" setting
	"channels": [
		"https://packagecontrol.io/channel_v3.json"
	],

	// A list of URLs that contain a packages JSON file. These repositories
	// are placed in order before repositories from the "channels"
	// setting
	"repositories": [],

	// An HTTP proxy server to use for requests. Not normally used on Windows
	// since the system proxy configuration is utilized via WinINet. However,
	// if WinINet is not working properly, this will be used by the Urllib
	// downloader, which acts as a fallback.
	"http_proxy": "",
	// An HTTPS proxy server to use for requests - this will inherit from
	// http_proxy if it is set to "" or null and http_proxy has a value. You
	// can set this to false to prevent inheriting from http_proxy. Not
	// normally used on Windows since the system proxy configuration is
	// utilized via WinINet. However, if WinINet is not working properly, this
	// will be used by the Urllib downloader, which acts as a fallback.
	"https_proxy": "",

	// Username and password for both http_proxy and https_proxy. May be used
	// with WinINet to set credentials for system-level proxy config.
	"proxy_username": "",
	"proxy_password": "",

```

同 bash 终端通用代理变量：`http_proxy`，`https_proxy`。  
当没有设置 https_proxy 时，将采用 http_proxy 的配置（如果有的话）。

控制面板（<kbd>⌘</kbd><kbd>⇧</kbd><kbd>P</kbd>）输入 Preferences: Package Control Settings - User 打开 Package Control 用户配置文件：

`~/Library/Application\ Support/Sublime\ Text 3/Packages/User/Package\ Control.sublime-settings` ：

其中可以添加 **channels**、**repositories**、**代理** 等配置参数：

```json
	"channels":
	[
		"https://packagecontrol.io/channel_v3.json",
		"https://wilon.github.io/static/channel_v3.json"
	],
	
	"http_proxy": "http://<host>:<port>",
	"https_proxy": "https://<host>:<port>",
```

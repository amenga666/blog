---
title: "终端代理设置"
date: 2020-05-21T20:00:00+08:00
draft: false
authors: ["BahuangShanren"]
tags: [命令行,Git,Linux,Windows]
categories: [方案]
images: [https://cdn.jsdelivr.net/gh/amenga666/picture@latest/Terminal.webp]
featuredImage: "https://cdn.jsdelivr.net/gh/amenga666/picture@latest/Terminal.webp"
featuredImagePreview: "https://cdn.jsdelivr.net/gh/amenga666/picture@latest/Terminal.webp"
summary: Git、Linux与Windows的终端代理设置
---

## Windows终端代理设置

### cmd

#### 临时代理

{{< admonition type=info title="注意" open=true >}}
只对当前终端有效，新建终端需要重新设置。
{{< /admonition >}}

**格式**：

```shell
set http_proxy=http://proxy_userid:proxy_password@proxy_ip:proxy_port
```

输入设置代理的命令：

**HTTP代理**：

```shell
set http_proxy=http://127.0.0.1:7890
set https_proxy=http://127.0.0.1:7890
```

或者

**SOCKS5代理**：

```shell
set http_proxy=socks5://127.0.0.1:7890
set https_proxy=socks5://127.0.0.1:7890
```

使用`echo %http_proxy%`命令查看是否设置成功。

#### 永久代理

1. 新建一个`cmd_init.cmd`，将上面相应的代理命令写入。
2. 打开注册表，在`HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\`下新建名为`AutoRun`的**字符串值**，数据的值是一个绝对路径，路径指向刚才新建的`cmd_init.cmd`，可以将这个文件放在C盘根目录，即路径为`C:\cmd_init.cmd`。
3. 重新打开cmd，它会自动运行这两条命令。

#### 取消代理

取消当前终端的代理设置：

```shell
set http_proxy=
set https_proxy=
```

### PowerShell

#### 临时代理

{{< admonition type=info title="注意" open=true >}}
只对当前终端有效，新建终端需要重新设置。
{{< /admonition >}}

**格式**：

```shell
$env:http_proxy="http://proxy_userid:proxy_password@proxy_ip:proxy_port"
```

输入设置代理的命令：

**HTTP代理**：

```shell
$env:http_proxy="http://127.0.0.1:7890"
$env:https_proxy="http://127.0.0.1:7890"
```

或者

**SOCKS5代理**：

```shell
$env:http_proxy="socks5://127.0.0.1:7890"
$env:https_proxy="socks5://127.0.0.1:7890"
```

#### 永久代理

1. 在PowerShell中运行以下命令：

    ```shell
    if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
    notepad $PROFILE
    ```

2. 默认会使用记事本打开一个文件，在文件中写入上面相应的代理命令，保存关闭即可。
3. 上面的配置文件位于`此电脑/文档/WindowsPowerShell/`，名为`Microsoft.PowerShell_profile.ps1`，这个文件的内容会在每次打开PowerShell时自动运行。

#### 取消代理

取消当前终端的代理设置：

```shell
$env:http_proxy=""
$env:https_proxy=""
```

## Linux终端代理设置

### 临时代理

{{< admonition type=info title="注意" open=true >}}
只对当前终端有效，新建终端需要重新设置。
{{< /admonition >}}

输入设置代理的命令：

**格式**：

```bash
export http_proxy=http://proxy_userid:proxy_password@proxy_ip:proxy_port
```

**HTTP代理**：

```bash
export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890
```

**SOCKS5代理**:

```bash
export http_proxy=socks5://127.0.0.1:7890
export https_proxy=socks5://127.0.0.1:7890
```

设置终端中的**wget**、**curl**等软件都走**SOCKS5**代理：

```bash
export ALL_PROXY=socks5://127.0.0.1:7890
```

### 永久代理

#### 方法一

1. 将上面的临时代理命令写入环境配置文件中，比如`~/.bashrc`或`~/.zshrc`。
2. 运行`source ~/.bashrc`或`source ~/.zshrc`以应用新的环境变量。
3. 这样当前终端和新建的终端就会使用代理。

#### 方法二

1. 通过设置**alias**来简化操作。将以下命令写入`/etc/bashrc`或者`~/.bashrc`，前者生效范围是所有用户，后者是当前用户。

    ```bash
    alias setproxy="export ALL_PROXY=socks5://127.0.0.1:7890"
    alias unsetproxy="unset ALL_PROXY"
    ```

2. 运行`source /etc/bashrc`或`source ~/.bashrc`以应用新的环境变量。
3. 每次要使用代理就输入`setproxy`，不用了就输入`unsetproxy`。

### 取消代理

取消当前终端的代理设置：

```bash
unset http_proxy
unset https_proxy
unset ALL_RPOXY
```

## Git设置代理

### 永久代理

{{< admonition type=info title="注意" open=true >}}
使用`--global`参数即全局永久生效，不使用则对当前仓库永久生效，相当于`--local`，关于配置级别，参考[此文](http://localhost:1313/2020-7/#%E9%85%8D%E7%BD%AE%E7%BA%A7%E5%88%AB)。
{{< /admonition >}}

**格式**：

```shell
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

**HTTP代理**：

```shell
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

**SOCKS5代理**：

```shell
git config --global http.proxy socks5://127.0.0.1:7890
git config --global https.proxy socks5://127.0.0.1:7890
```

### 取消代理

```shell
git config --global --unset http.proxy
git config --global --unset https.proxy
```

使用`git config --global --list`命令查看是否设置成功。

{{< admonition type=quote title="参考文档" open=true >}}
https://www.yixuju.cn/other/talking-about-proxy/
{{< /admonition >}}
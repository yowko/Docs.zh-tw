---
title: "Linux 上 .NET Core 的必要條件"
description: "支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: johalex
ms.author: johalex
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: dd1557d3a43a13c8103c82dfa467aa889fcf3bbb
ms.openlocfilehash: 2ee303424721b7e1ecb8473c5f957ca929a8742f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a>Linux 上 .NET Core 的必要條件

本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。 支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：

* [命令列](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>支援的 Linux 版本

下列 Linux 發行版本/版本支援 .NET core 2.x：

 * Red Hat Enterprise Linux 7 x64
 * CentOS 7 x64
 * Oracle Linux 7 x64
 * Fedora 25、26 x64
 * Debian 9、8.7+ x64 
 * Ubuntu 17.04、16.04、14.04 x64
 * Linux Mint 18、17 x64
 * openSUSE 42.2+ x64
 * SUSE Enterprise Linux (SLES) 12 SP2+ x64

下列 Linux 發行版本/版本支援 .NET core 1.x：

* Red Hat Enterprise Linux / CentOS / Oracle Linux 7 x64
* Fedora 24 x64
* Debian 8.2+ x64
* Ubuntu / Linux Mint 14.04、16.04、16.10*、17 x64
* openSUSE 42.1 (1.1) x64
> [!NOTE]
> 最新的 .NET Core 1.1 修補程式版本支援 Ubuntu / Linux 16.10

如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。

如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。
## <a name="linux-distribution-dependencies"></a>Linux 發行版本相依性
### <a name="ubuntu"></a>Ubuntu
Ubuntu 發行版本需要安裝下列程式庫：

* libunwind8
* libunwind8-dev
* gettext
* libicu-dev
* liblttng-ust-dev
* libcurl4-openssl-dev
* libssl-dev
* uuid-dev
* unzip

### <a name="centos"></a>CentOS
CentOS 發行版本需要安裝下列程式庫：
* deltarpm
* epel-release
* unzip
* libunwind
* gettext
* libcurl-devel
* openssl-devel
* zlib
* libicu-devel

## <a name="installing-net-core-prerequisites-with-the-native-installers"></a>使用原生安裝程式安裝 .NET Core 必要條件

受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。 原生安裝程式需要伺服器的管理員 (sudo) 存取權。 使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。 原生安裝程式也會安裝 .NET Core SDK 全系統。

Linux 上有兩個安裝程式套件選擇： 
* 使用摘要架構的套件管理員，例如 Ubuntu 的 apt get 或 CentOS 的 yum。 
* 使用套件本身，DEB 或 RPM。 

### <a name="scripting-installs-with-the-net-core-installer-script"></a>指令碼安裝與 .NET Core 安裝程式指令碼 

`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。 您可以從 [CLI GitHub 存放庫 (英文)](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain) 下載指令碼。 

安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。 此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。

> [!IMPORTANT]
> 執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。

## <a name="install-net-core-dependencies-for-red-hat-enterprise-linux-rhel-7-server"></a>安裝 Red Hat Enterprise Linux (RHEL) 7 伺服器的 .NET Core 相依性

> [!Warning]
> 開始之前，請先移除系統中所有舊版的 .NET Core。

### <a name="verify-and-enable-the-net-channel-for-rhel-7-server"></a>驗證並啟用 RHEL 7 伺服器的 .NET 通道
在 RHEL 伺服器上安裝 .NET Core 相依性：

1. 啟用 Red Hat .NET 通道，位於 RHEL 7 伺服器訂閱底下。 
    * Red Hat Enterprise 7 伺服器請使用：
         ```bash
        subscription-manager repos --enable=rhel-7-server-dotnet-rpms
        ```
    * Red Hat Enterprise 7 工作站請使用：
         ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
        ```
    * Red Hat Enterprise 7 HPC 計算節點請使用：
         ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. 安裝 scl 工具。
    ```bash
    yum install scl-utils
    ```
3. 安裝 .NET Core 1.1 (以及所有相依性)：
    ```bash
    yum install rh-dotnetcore11
    scl enable rh-dotnetcore11 bash
    ```
4. 執行 `dotnet --help` 命令，以證明安裝成功。

     ```bash
     dotnet --help
     ```
> [!NOTE]
> 如需 Red Hat .NET 通道存取登錄說明，請參閱 Red Hat 的 [.NET Core 1.1 入門指南的第 1 章](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)。


## <a name="install-net-core-for-ubuntu-1404-1604-1610--linux-mint-17-18-64-bit"></a>安裝 .NET Core for Ubuntu 14.04、16.04、16.10 以及 Linux Mint 17、18 (64 位元)

> [!Warning]
> 開始之前，請先移除系統中所有舊版的 .NET Core。

### <a name="add-the-dotnet-apt-get-feed"></a>新增 dotnet apt-get 摘要

1. 設定所需的裝載套件摘要版本。

   **Ubuntu 14.04 / Linux Mint 17**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    **Ubuntu 16.04 / Linux Mint 18**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    **Ubuntu 16.10**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
2. 安裝 .NET Core。
# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

安裝裝載套件摘要之後，在 Ubuntu 或 Linux Mint 上安裝 .NET Core 2.0：
```bash
sudo apt-get install dotnet-sdk-2.0.0
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

安裝裝載套件摘要之後，在 Ubuntu 或 Linux Mint 上安裝 .NET Core 1.x：
```bash
sudo apt-get install dotnet-dev-1.0.4
```
---
3. 執行 `dotnet --help` 命令，以證明安裝成功。

 ```bash
     dotnet --help
 ```
## <a name="install-net-core-for-debian-8-or-9-64-bit"></a>安裝 .NET Core for Debian 8 或 9 (64 位元)。

> [!Warning]
> 開始之前，請先移除系統中所有舊版的 .NET Core。

在 Debian 8 或 9 (64 位元) 安裝 .NET Core：
1. 取得必要條件。 
    ```bash
    sudo apt-get install curl libunwind8 gettext
    ```
2. 下載 .NET Core SDK 二進位檔 (tarball)。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)   

```bash
     curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)   

```bash
     curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
```
---
3. 擷取 .NET Core SDK 二進位檔。
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. 將 dotnet 新增至 PATH。
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. 執行 `dotnet --help` 命令，以證明安裝成功。

     ```bash
     dotnet --help
     ```

## <a name="install-net-core-for-fedora-24-25-or-26-64-bit"></a>安裝 .NET Core for Fedora 24、25 或 26 (64 位元)

> [!Warning]
> 開始之前，請先移除系統中所有舊版的 .NET Core。

安裝 .NET Core for Fedora 26、25 (.NET Core 2.x) 或 24 (.NET Core 1.x)： 
1. 取得必要條件。 
    ```bash
    sudo dnf install libunwind libicu
    ```
2. 下載 .NET Core SDK 二進位檔 (tarball)。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Fedora 26 或 25**

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Fedora 24**

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
```

---
3. 擷取 .NET Core SDK 二進位檔。
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. 將 dotnet 新增至 PATH。
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. 執行 `dotnet --help` 命令，以證明安裝成功。

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>安裝 .NET Core for CentOS 7.1 (64 位元) 以及 Oracle Linux 7.1 (64 位元)

> [!Warning]
> 開始之前，請先移除系統中所有舊版的 .NET Core。

安裝 .NET Core for CentOS 7.1 (64 位元) 以及 Oracle Linux 7.1 (64 位元)：

1. 取得必要條件。
    ```bash
    sudo dnf install libunwind libicu
    ```
2. 下載 .NET Core SDK 二進位檔 (tarball)。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
```

---
3. 擷取 .NET Core SDK 二進位檔。
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. 將 dotnet 新增至 PATH。
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. 執行 `dotnet --help` 命令，以證明安裝成功。

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit-net-core-2x-and-opensuse-64-bit"></a>安裝 .NET Core for SUSE Linux Enterprise Server (64 位元) (.NET Core 2.x) 及 openSUSE (64 位元)

> [!Warning]
> 開始之前，請先移除系統中所有舊版的 .NET Core。

安裝 .NET Core for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 位元) 及 NET Core 2.x 的 openSUSE 42.2，或 .NET Core 1.x 的 openSUSE 42.1(64 位元)：

1. 取得必要條件。
    ```bash
    sudo zypper install libunwind libicu
    ```
2. 下載 .NET Core SDK 二進位檔 (tarball)。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**SLES 12 SP2、openSUSE 42.2**

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**openSUSE 42.1**

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
```

---
3. 擷取 .NET Core SDK 二進位檔。
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. 將 dotnet 新增至 PATH。
    ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. 執行 `dotnet --help` 命令，以證明安裝成功。

     ```bash
     dotnet --help
     ```

> [!IMPORTANT]
> 如果支援的 Linux 發行版本/版本遇到 .NET Core 2.x 安裝問題，請參閱已安裝的發行版本/版本的 [2.0 已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。
> [!IMPORTANT]
> 如果支援的 Linux 發行版本/版本遇到 .NET Core 1.x 安裝問題，請參閱已安裝的發行版本/版本的 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。

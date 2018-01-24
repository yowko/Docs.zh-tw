---
title: "Linux 上 .NET Core 的必要條件"
description: "支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 12/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: d3c5dde443f848831f7c0585633339c35213357b
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux 上 .NET Core 的必要條件

本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。 支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：

* [使用命令列搭配您偏好的編輯器](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>支援的 Linux 版本

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.0 將 Linux 視為單一作業系統。 針對每個支援的 Linux 發行版本與每種晶片架構，會有單一的 Linux 組建。

下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 2.x：

 * Red Hat Enterprise Linux 7
 * CentOS 7
 * Oracle Linux 7
 * Fedora 25, Fedora 26
 * Debian 8.7 或更新的版本 
 * Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04
 * Linux Mint 18, Linux Mint 17
 * openSUSE 42.2 或更新的版本
 * SUSE Enterprise Linux (SLES) 12 SP2 或更新的版本

如需 .NET Core 2.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 24
* Debian 8.2 或更新的版本
* Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*
 * 最新的 .NET Core 1.1 修補程式版本支援 Ubuntu 16.10
* Linux Mint 17
* openSUSE 42.1 或更新的版本 (.NET Core 1.1)

如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。

---

## <a name="linux-distribution-dependencies"></a>Linux 發行版本相依性

下列要作為範例。 確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。

### <a name="ubuntu"></a>Ubuntu

Ubuntu 發行版本需要安裝下列程式庫：

* libunwind8
* liblttng-ust0
* libcurl3
* libssl1.0.0
* libuuid1
* libkrb5-3
* zlib1g
* libicu52 (適用於 14.X)
* libicu55 (適用於 16.X)
* libicu57 (適用於 17.X)

### <a name="centos"></a>CentOS

CentOS 發行版本需要安裝下列程式庫：

* libunwind
* lttng-ust
* libcurl
* openssl-libs
* libuuid
* krb5-libs
* libicu
* zlib

如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>使用原生安裝程式來安裝 .NET Core 相依性

受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。 原生安裝程式需要伺服器的管理員 (sudo) 存取權。 使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。 原生安裝程式也會安裝 .NET Core SDK 全系統。

Linux 上有兩個安裝程式套件選擇：

* 使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。
* 使用套件本身，DEB 或 RPM。

### <a name="scripting-installs-with-the-net-core-installer-script"></a>使用 .NET Core 安裝程式指令碼以指令碼進行安裝

`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。 指令碼下載位置：https://dot.net/v1/dotnet-install.sh

安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。 此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。

> [!IMPORTANT]
> 執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a>安裝 Red Hat Enterprise Linux (RHEL) 7 的 .NET Core

若要在 RHEL 7 上安裝 .NET Core：

1. 啟用 Red Hat .NET 通道，位於 RHEL 7 訂閱底下。
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
    
3. 安裝 .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

安裝 .NET Core 2.0 SDK 及執行階段：

   ```bash
   yum install rh-dotnet20
   ```

為環境啟用 .NET Core 2.0 SDK/執行階段：

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

安裝 .NET Core 1.1 SDK 及執行階段：

   ```bash
   yum install rh-dotnetcore11
   ```

為環境啟用 .NET Core 1.1 SDK 及執行階段：

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

**.NET Core 1.0**

安裝 .NET Core 1.0 SDK 及執行階段：

   ```bash
   yum install rh-dotnetcore10
   ```

為環境啟用 .NET Core 1.0 SDK 及執行階段：

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. 執行 `dotnet --version` 命令，以證明安裝成功。

     ```bash
     dotnet --version
     ```

如需 Red Hat .NET 通道存取登錄說明，請參閱 Red Hat 的 [.NET Core 1.1 入門指南的第 1 章](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)。

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a>安裝適用於 Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 與 Linux Mint 17, Linux Mint 18 的 .NET Core (64 位元)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. 註冊受信任的 Microsoft 產品金鑰。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. 設定所需的裝載套件摘要版本。

   **Ubuntu 17.10**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   **Ubuntu 17.04**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 16.04 / Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 14.04 / Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. 安裝 .NET Core。

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 設定所需的裝載套件摘要版本。

   **Ubuntu 16.10**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  **Ubuntu 16.04 / Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   **Ubuntu 14.04 / Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. 在 Ubuntu 或 Linux Mint 上安裝 .NET Core 1.x：

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a>安裝適用於 Debian 8 或 Debian 9 的 .NET Core (64 位元)

若要在 Debian 8 或 Debian 9 上安裝 .NET Core (64 位元)：

1. 請移除系統中所有 .NET Core **先前的預覽版**。

> [!NOTE]
> 需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. 安裝系統元件。

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. 註冊受信任的 Microsoft 產品金鑰。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. 註冊 Microsoft 產品摘要。

   **Debian 9 (Stretch)**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   **Debian 8 (Jessie)**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. 安裝 .NET Core SDK。

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. 將 dotnet 新增至 PATH。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 取得必要條件。

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. 下載 .NET Core SDK 二進位檔 (tarball)。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. 擷取 .NET Core SDK 二進位檔。

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. 將 dotnet 新增至 PATH。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a>安裝適用於 Fedora 24, Fedora 25 或 Fedora 26 的 .NET Core (64 位元)

在 Fedora 26 或 Fedora 25 上安裝 .NET Core 2.x，或在 Fedora 24 上安裝 .NET Core 1.x：

1. 請移除系統中所有 .NET Core **先前的預覽版**。

> [!NOTE]
> 需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Fedora 26 或 Fedora 25**

2. 註冊 Microsoft 簽章金鑰。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. 新增 dotnet 產品摘要。

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. 安裝 .NET Core SDK。

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. 將 dotnet 新增至 PATH。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Fedora 24**

2. 取得必要條件。

   ```bash
   sudo dnf install libunwind libicu
   ```

3. 下載 .NET Core SDK 二進位檔 (tarball)。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. 擷取 .NET Core SDK 二進位檔。

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. 將 dotnet 新增至 PATH。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>安裝 .NET Core for CentOS 7.1 (64 位元) 以及 Oracle Linux 7.1 (64 位元)

安裝 .NET Core for CentOS 7.1 (64 位元) 與 Oracle Linux 7.1 (64 位元)：

1. 請移除系統中所有 .NET Core **先前的預覽版**。

> [!NOTE]
> 需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. 註冊 Microsoft 簽章金鑰。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. 新增 Microsoft 產品摘要。

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. 安裝 .NET Core SDK。

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. 將 dotnet 新增至 PATH

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 取得必要條件。

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. 下載 .NET Core SDK 二進位檔 (tarball)。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. 擷取 .NET Core SDK 二進位檔。

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. 將 dotnet 新增至 PATH。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a>安裝適用於 SUSE Linux Enterprise Server 的 .NET Core (64 位元)

安裝適用於 SUSE Linux Enterprise Server (SLES) 12 SP2 (64 位元) 的 .NET Core 2.x：

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 新增 dotnet 產品摘要。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. 安裝 .NET Core SDK。

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. 將 dotnet 新增至 PATH。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a>安裝適用於 openSUSE 的 .NET Core (64 位元)

安裝適用於 openSUSE 的 .NET Core 2.x 或適用於 openSUSE (64 位元) 的 .NET Core 1.x：

1. 請移除系統中所有 .NET Core **先前的預覽版**。

> [!NOTE]
> 需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. 註冊 Microsoft 簽章金鑰。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. 新增 dotnet 產品摘要。

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. 安裝 .NET Core SDK。

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. 將 dotnet 新增至 PATH。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 取得必要條件。

   ```bash
   sudo zypper install libunwind libicu
   ```

3. 下載 .NET Core SDK 二進位檔 (tarball)。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. 擷取 .NET Core SDK 二進位檔。
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. 將 dotnet 新增至 PATH。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. 執行 `dotnet --version` 命令，以證明安裝成功。

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> 如果支援的 Linux 發行版本/版本遇到 .NET Core 2.x 安裝問題，請參閱已安裝的發行版本/版本的 [2.0 已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)主題。 
>
> 如果支援的 Linux 發行版本/版本遇到 .NET Core 1.x 安裝問題，請參閱已安裝的發行版本/版本的 [1.0.0 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)和 [1.0.1 已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)主題。

---
title: Linux 上 .NET Core 的必要條件
description: 支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。
author: jralexander
ms.author: johalex
ms.date: 05/08/2018
ms.openlocfilehash: 4890f682ee2d0b55dc5059d8f1d3091def07a8a5
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483498"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux 上 .NET Core 的必要條件

本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。 支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：

* [使用命令列搭配您偏好的編輯器](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> 實際執行伺服器/生產環境不需要 .NET Core SDK 套件。 僅需要.NET Core 執行階段套件，即可將應用程式部署到生產環境。 .NET Core 執行階段將應用程式作為獨立部署的一部分進行部署，不過，針對架構相依的部署應用程式必須單獨加以部署。 如需架構相依部署類型和獨立部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](./deploying/index.md)。 另請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)以了解特定指導方針。

## <a name="supported-linux-versions"></a>支援的 Linux 版本

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.x 將 Linux 視為單一作業系統。 針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。

下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 2.x：

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 27、26
* Debian 9、8.7 或更新版本
* Ubuntu 18.04、17.10、16.04、14.04
* Linux Mint 18、17
* openSUSE 42.3 或更新版本
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 或更新版本

如需 .NET Core 2.x 支援的作業系統完整清單、發行版本、版本、不支援的作業系統版本，以及生命週期原則連結，請參閱 [.NET Core 2.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 26
* Debian 8.2 或更新的版本
* Ubuntu 16.04、14.04
* Linux Mint 18、17
* openSUSE 42.3 或更新版本 (.NET Core 1.1)

如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。

---

## <a name="linux-distribution-dependencies"></a>Linux 發行版本相依性

下列要作為範例。 確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。

### <a name="ubuntu"></a>Ubuntu

Ubuntu 發行版本需要安裝下列程式庫：

* liblttng-ust0
* libcurl3
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (適用於 14.x)
* libicu55 (適用於 16.x)
* libicu57 (適用於 17.x)
* libicu60 (適用於 18.x)

針對 .NET Core 2.1 之前的版本，還需要下列的相依性：

* libunwind8
* libuuid1

### <a name="centos"></a>CentOS

CentOS 發行版本需要安裝下列程式庫：

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

針對 .NET Core 2.1 之前的版本，還需要下列的相依性：

* libunwind
* libuuid

如需有關相依性的詳細資訊，請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) \(英文\)。

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>使用原生安裝程式來安裝 .NET Core 相依性

受支援的 Linux 發行版本/版本可使用 .NET Core 原生安裝程式。 原生安裝程式需要伺服器的管理員 (sudo) 存取權。 使用原生安裝程式的優點在於它會安裝所有的 .NET Core 原生相依性。 原生安裝程式也會安裝 .NET Core SDK 全系統。

Linux 上有兩個安裝程式套件選擇：

* 使用摘要型套件管理員，例如 Ubuntu 的 apt get 或 CentOS/RHEL 的 yum。
* 使用套件本身，DEB 或 RPM。

### <a name="scripting-installs-with-the-net-core-installer-script"></a>使用 .NET Core 安裝程式指令碼以指令碼進行安裝

[dotnet-install 指令碼](./tools/dotnet-install-script.md)用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。 您可以從 [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh) 下載指令碼。

安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。 此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>安裝適用於支援之 Red Hat Enterprise Linux (RHEL) 版本的 .NET Core

若要在支援的 RHEL 版本上安裝.NET Core：

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

為了確保您能夠擁有最新安裝資訊，請遵循適用於支援之的 RHEL 版本non-admin [.NET Core 2.x SDK 和執行階段安裝程式指示](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2.  如需在 Red Hat Enterprise Linux 上安裝 .NET Core 1.1 的最新資訊，請參閱 [.NET Core 1.1 入門指南](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET Core 1.0**

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2.  如需在 Red Hat Enterprise Linux 上安裝 .NET Core 1.0 的最新資訊，請參閱 [.NET Core 1.0 入門指南](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

如需 Red Hat .NET 通道存取登錄說明，請參閱 Red Hat 的 [.NET Core 1.1 入門指南的第 1 章](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)。

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>為支援的 Ubuntu 和 Linux Mint 發行版本/版本 (64 位元) 安裝 .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 Ubuntu 和 Linux Mint 發行版本/版本 (64 位元) 上安裝 .NET Core 2.x：

**.NET Core 2.0**

|執行階段/SDK          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04/Linux Mint 18|Ubuntu 14.04/Linux Mint 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET Core Runtime 2.0.7  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|.NET Core Runtime 2.0.6  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|.NET Core Runtime 2.0.5  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|.NET Core SDK 2.1.105    |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|.NET Core SDK 2.1.103    |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|.NET Core SDK 2.0.3      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|.NET Core SDK 2.0.0      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET Core 2.1**

>[!IMPORTANT]
> 若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。

|執行階段/SDK                  |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04/Linux Mint 18|Ubuntu 14.04/Linux Mint 17|
|---------------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET Core Runtime 2.1.0-rc1      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0-rc1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-rc1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-rc1)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-rc1)            |
|.NET Core Runtime 2.1.0-preview2 |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0-preview2)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview2)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview2)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview2)            |
|.NET Core Runtime 2.1.0-preview1 |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0-preview1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview1)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview1)            |
|.NET Core SDK 2.1.300-rc1  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300-rc1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-rc1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-rc1)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-rc1)            |
|.NET Core SDK 2.1.300-preview2   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300-preview2)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview2)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview2)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview2)            |
|.NET Core SDK 2.1.300-preview1   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300-preview1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview1)|[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview1)            |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview1)            |


# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 Ubuntu 和 Linux Mint 發行版本/版本 (64 位元) 上安裝 .NET Core 1.x：

| 執行階段/SDK         |Ubuntu 16.04/Linux Mint 18|Ubuntu 14.04/Linux Mint 17|
|-------------------------|----------------------------|----------------------------|
|.NET Core Runtime 1.1.7  |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.1.6  |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.10 |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core Runtime 1.0.9  |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.8      |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.1.7      |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.0.4      |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET Core SDK 1.0.1      |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>為支援的 Debian 版本 (64 位元) 安裝 .NET Core

在支援的 Debian 版本 (64 位元) 上安裝 .NET Core：

> [!NOTE]
> 需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 Debian 版本 (64 位元) 上安裝 .NET Core 2.x：

**.NET Core 2.0**

|執行階段/SDK          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|.NET Core Runtime 2.0.7  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|.NET Core Runtime 2.0.6  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|.NET Core Runtime 2.0.5  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|.NET Core SDK 2.1.105    |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET Core SDK 2.1.103    |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|.NET Core SDK 2.0.3      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|.NET Core SDK 2.0.0      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET Core 2.1**

>[!IMPORTANT]
> 若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。

|執行階段/SDK                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|.NET Core Runtime 2.1.0-rc1      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-rc1)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-rc1)   |
|.NET Core Runtime 2.1.0-preview2 |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview2)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview2)   |
|.NET Core Runtime 2.1.0-preview1 |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview1)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview1)   |
|.NET Core SDK 2.1.300-rc1        |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-rc1)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-rc1)        |
|.NET Core SDK 2.1.300-preview2   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview2)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview2)   |
|.NET Core SDK 2.1.300-preview1   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview1)   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview1)   |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 若要在 Debian 9 或 Debian 8 上安裝 .NET Core 1.x：

* .NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* .NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.10 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* .NET Core Runtime 1.0.9 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* .NET Core SDK 1.1.8 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* .NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* .NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* .NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>為支援的 Fedora 版本 (64 位元) 安裝 .NET Core

若要在支援的 Fedora 版本上安裝 .NET Core：

> [!NOTE]
> 需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 Fedora 版本 (64 位元) 上安裝 .NET Core 2.x：

**.NET Core 2.0**

|執行階段/SDK          |Fedora 26 或更新版本 |Fedora 25 或更舊版本 |
|-------------------------|-------------------|----------------------|
|.NET Core Runtime 2.0.7  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|.NET Core Runtime 2.0.6  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|.NET Core Runtime 2.0.5  |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|.NET Core SDK 2.1.105    |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|.NET Core SDK 2.1.103    |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|.NET Core SDK 2.0.3      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET Core 2.1**

>[!IMPORTANT]
> 若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。

|執行階段/SDK                  |Fedora 27          |Fedora 26             |
|---------------------------------|-------------------|----------------------|
|.NET Core Runtime 2.1.0-rc1      |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0-rc1)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-rc1)           |
|.NET Core Runtime 2.1.0-preview2 |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0-preview2)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview2)           |
|.NET Core Runtime 2.1.0-preview1 |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0-preview1)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview1)           |
|.NET Core SDK 2.1.300-rc1        |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300-rc1)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-rc1)           |
|.NET Core SDK 2.1.300-preview2   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300-preview2)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview2))           |
|.NET Core SDK 2.1.300-preview1   |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0-preview1)       |[安裝連結](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview1)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 Fedora 版本 (64 位元) 上安裝 .NET Core 1.x：

**Fedora 24**

* .NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* .NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* .NET Core SDK 1.1.8 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* .NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* .NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* .NET Core Runtime 1.0.9 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* .NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* .NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>為支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 安裝 .NET Core

若要為支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 安裝 .NET Core：

> [!NOTE]
> 需要使用者控制的目錄，以用於來自 tar.gz 的 Linux 系統安裝。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 上安裝 .NET Core 2.x：

**.NET Core 2.0**

* .NET Core Runtime 2.0.7 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET Core Runtime 2.0.6 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET Core Runtime 2.0.5 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* .NET Core SDK 2.1.105 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105)
* .NET Core SDK 2.1.103 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* .NET Core SDK 2.0.3 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
* .NET Core SDK 2.0.0 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0)
 
**.NET Core 2.1**

>[!IMPORTANT]
> 若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview/)。

* .NET Core Runtime 2.1.0-rc1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-rc1)
* .NET Core Runtime 2.1.0-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview2)
* .NET Core Runtime 2.1.0-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)
* .NET Core SDK 2.1.300-rc1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-rc1)
* .NET Core SDK 2.1.300-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview2)
* .NET Core SDK 2.1.300-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 CentOS 和 Oracle Linux 發行版本/版本 (64 位元) 上安裝 .NET Core 1.x：

* .NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* .NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.10 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* .NET Core Runtime 1.0.9 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* .NET Core SDK 1.1.8 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* .NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* .NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* .NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>為支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 安裝.NET Core

為支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 安裝.NET Core 2.x：

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 上安裝.NET Core 2.x：

**.NET Core 2.0**

**SUSE Linux Enterprise Server**

* .NET Core Runtime 2.0.7 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7)
* .NET Core Runtime 2.0.6 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6)
* .NET Core Runtime 2.0.5 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5)
* .NET Core SDK 2.1.105 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105)
* .NET Core SDK 2.1.103 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103)
* .NET Core SDK 2.0.3 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3)
* .NET Core SDK 2.0.0 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0)

**openSUSE**

* .NET Core Runtime 2.0.7 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7)
* .NET Core Runtime 2.0.6 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* .NET Core Runtime 2.0.5 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* .NET Core SDK 2.1.105 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105)
* .NET Core SDK 2.1.103 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* .NET Core SDK 2.0.3 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
* .NET Core SDK 2.0.0 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0)
 
**.NET Core 2.1**

>[!IMPORTANT]
> 若要將 .NET Core 2.1 與 Visual Studio 搭配使用，您需要[安裝 Visual Studio 2017 15.7 Preview 1 或更新版本](https://www.visualstudio.com/vs/preview)。

**SUSE Linux Enterprise Server**

* .NET Core Runtime 2.1.0-rc1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0-rc1)
* .NET Core Runtime 2.1.0-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0-preview2)
* .NET Core Runtime 2.1.0-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0-preview1)
* .NET Core SDK 2.1.300-rc1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300-rc1)
* .NET Core SDK 2.1.300-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300-preview2)
* .NET Core SDK 2.1.300-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300-preview1)

**openSUSE**

* .NET Core Runtime 2.1.0-rc1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-rc1)
* .NET Core Runtime 2.1.0-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview2)
* .NET Core Runtime 2.1.0-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)
* .NET Core SDK 2.1.300-rc1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-rc1)
* .NET Core SDK 2.1.300-preview2 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview2)
* .NET Core SDK 2.1.300-preview1 [安裝連結](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. 請移除系統中所有 .NET Core **先前的預覽版**。

2. 在支援的 SUSE Linux Enterprise Server 和 OpenSUSE 發行版本/版本 (64 位元) 上安裝.NET Core 1.x

**SUSE Linux Enterprise Server 13.2**

* .NET Core Runtime 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET Core Runtime 1.1.6 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* .NET Core SDK 1.1.7 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)

**openSUSE 24**

* .NET Core SDK 1.0.4 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)
* .NET Core SDK 1.0.1 [安裝連結](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)

---

> [!IMPORTANT]
> 如果您在支援的 Linux 發行版本/版本上安裝 .NET Core 的相關問題，請參閱已安裝之發行版本/版本的下列主題：
> * [.NET Core 2.1 的已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [.NET Core 2.0 的已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [.NET Core 1.1 的已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [.NET Core 1.0 的已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0)

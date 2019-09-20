---
title: Linux 上 .NET Core 的必要條件
description: 支援的 Linux 版本和 .NET Core 的相依性，以在 Linux 電腦上開發、部署和執行 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 31c53b2cc0fe576e56685f4a5561258136fd2541
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116590"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux 上 .NET Core 的必要條件

本文會說明在 Linux 開發 .NET Core 應用程式所需的相依性。 支援的 Linux 發行版本/版本和跟隨的相依性，適用於在 Linux 開發 .NET Core 應用程式的兩種方式：

* [使用命令列搭配您偏好的編輯器](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> 實際執行伺服器/生產環境不需要 .NET Core SDK 套件。 僅需要.NET Core 執行階段套件，即可將應用程式部署到生產環境。 .NET Core 執行階段將應用程式作為獨立部署的一部分進行部署，不過，針對架構相依的部署應用程式必須單獨加以部署。 如需架構相依部署類型和獨立部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](./deploying/index.md)。 另請參閱[獨立式 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)以了解特定指導方針。

## <a name="supported-linux-versions"></a>支援的 Linux 版本

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.x 將 Linux 視為單一作業系統。 針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。 

如需下載連結和詳細資訊，請參閱 [.NET Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)或 [.NET Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)。

下列 Linux 發行版本/版本支援 .NET core 2.x：

* Red Hat Enterprise Linux 7、6 - 64 位元 (`x86_64` 或 `amd64`)
* CentOS 7 - 64 位元 (`x86_64` 或 `amd64`) 
* Oracle Linux 7 - 64 位元 (`x86_64` 或 `amd64`) 
* Fedora 28、27 - 64 位元 (`x86_64` 或 `amd64`) 
* Debian 9 (64 位元，`arm32`)、8.7 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)
* Ubuntu 18.04 (64 位元 `arm32`)、16.04、14.04 - 64 位元 (`x86_64` 或 `amd64`)
* Linux Mint 18、17 - 64 位元 (`x86_64` 或 `amd64`)
* openSUSE 42.3 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)
* Alpine Linux 3.7 或更新版本 - 64 位元 (`x86_64` 或 `amd64`)

如需 .NET Core 2.1 和 .NET Core 2.2 支援的作業系統完整清單、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結，請參閱 [.NET Core 2.1 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)和 [.NET Core 2.2 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

如需下載連結和詳細資訊，請參閱 [.NET Core 1.1 下載](https://dotnet.microsoft.com/download/dotnet-core/1.1)或 [.NET Core 1.0 下載](https://dotnet.microsoft.com/download/dotnet-core/1.0)。

下列 Linux 64 位元 (`x86_64` or `amd64`) 發行版本/版本支援NET Core 1.x：

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1)、27
* Debian 8.2 或更新的版本
* Ubuntu 18.04 (.NET Core 1.1)、16.04、14.04
* Linux Mint 17
* openSUSE 42.3 或更新版本 (.NET Core 1.1)

如需 .NET Core 1.x 支援的作業系統完整清單、不支援的作業系統版本，以及週期原則連結，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET Core 3.0 Preview 1](#tab/netcore30)

.NET Core 3.0 Preview 1 將 Linux 視為單一作業系統。 針對支援的 Linux 發行版本，會有單一的 Linux 組建 (按晶片架構)。 

如需下載連結和詳細資訊，請參閱 [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) (.NET Core 3.0 下載)。

下列 Linux 發行版本/版本支援 .NET Core 3.0 Preview 1。 

作業系統                            | 版本               | 架構  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64、ARM32\*、ARM64\*
Ubuntu                        | 16.04+、18.04+        | x64、ARM32\*、ARM64\*
Linux Mint                    | 18                    | X64
openSUSE                      | 42.3+                 | X64
SUSE Enterprise Linux (SLES)  | 12 SP2+               | X64
Alpine Linux                  | 3.8+                  | x64、ARM64

\* 從 Debian 9 和 Ubuntu 16.04 開始，支援 ARM32 和 ARM64。 ARM 晶片不支援這些發行版本的舊版。

如需 .NET Core 3.0 支援的作業系統、發行版本與版本、不支援的 OS 版本，以及生命週期原則連結完整清單，請參閱 [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) (.NET Core 3.0 支援的 OS 版本)。

如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。

---

## <a name="linux-distribution-dependencies"></a>Linux 發行版本相依性

下列要作為範例。 確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。

### <a name="ubuntu"></a>Ubuntu

Ubuntu 發行版本需要安裝下列程式庫：

* liblttng-ust0
* libcurl3 (適用於 14.x 及 16.x)
* libcurl4 (適用於 18.x)
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

### <a name="centos-and-fedora"></a>CentOS 與 Fedora

CentOS 發行版本需要安裝下列程式庫：

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

Fedora 使用者：如果您的 openssl 版本 >= 1.1，則必須安裝 compat-openssl10。

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

[dotnet-install 指令碼](./tools/dotnet-install-script.md)用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。 您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。

指令碼預設為安裝最新的 "LTS" 版本，也就是目前的 .NET Core 1.1。 若要安裝 .NET Core 2.1，請使用下列參數執行指令碼：

```bash
./dotnet-install.sh -c Current
```

安裝程式 bash 指令碼是用於自動化案例和非系統管理員安裝。 此指令碼也能讀取 PowerShell 參數，所以它們可以搭配 Linux/OS X 系統上的指令碼一起使用。

## <a name="troubleshoot"></a>疑難排解

如果您在支援的 Linux 發行版本/版本上安裝 .NET Core 的相關問題，請參閱已安裝之發行版本/版本的下列主題：

* [.NET Core 3.0 的已知問題](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [.NET Core 2.2 的已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [.NET Core 2.1 的已知問題](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [.NET Core 1.1 的已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [.NET Core 1.0 的已知問題](https://github.com/dotnet/core/blob/master/release-notes/1.0)

---
title: .NET 核心 SDK 和運行時依賴項 - .NET 核心
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET 核心 SDK 的作業系統和 CPU 體系結構先決條件。
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157802"
---
# <a name="net-core-dependencies-and-requirements"></a>.NET 核心依賴關係和要求

本文詳細介紹了 .NET Core 支援哪些作業系統和 CPU 體系結構。

## <a name="supported-operating-systems"></a>支援的作業系統

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET 核心 3.1](#tab/netcore31)

.NET Core 3.1 支援以下 Windows 版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1+， 8.1                    | x64、x86        |
| 視窗 10 用戶端             | 版本 1607*                  | x64、x86        |
| Windows Server                | 2012 R2+                       | x64、x86        |
| Nano Server                   | 版本 1803*                  | x64， ARM32      |

有關 .NET Core 3.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 支援以下 Windows 版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1+， 8.1                    | x64、x86        |
| 視窗 10 用戶端             | 版本 1607*                  | x64、x86        |
| Windows Server                | 2012 R2+                       | x64、x86        |
| Nano Server                   | 版本 1803*                  | x64， ARM32      |

有關 .NET Core 3.0 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2 支援以下 Windows 版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1+， 8.1                    | x64、x86        |
| 視窗 10 用戶端             | 版本 1607*                  | x64、x86        |
| Windows Server                | 2008 R2 SP1+                   | x64、x86        |
| Nano Server                   | 版本 1803*                   | x64， ARM32      |

有關 .NET Core 2.2 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 支援以下 Windows 版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1+， 8.1                    | x64、x86        |
| 視窗 10 用戶端             | 版本 1607*                  | x64、x86        |
| Windows Server                | 2008 R2 SP1+                   | x64、x86        |
| Nano Server                   | 版本 1803*                  | x64，            |

有關 .NET Core 2.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>視窗 7 / Vista / 8.1 / 伺服器 2008 R2

如果要在以下 Windows 版本上安裝 .NET SDK 或運行時，則需要其他依賴項：

- Windows 7 SP1
- 視窗 Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

安裝下列項目：

- [微軟視覺C++ 2015 可轉散布更新 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

如果您遇到以下錯誤之一，還需要上述要求：

> 無法啟動該程式，因為您的電腦中缺少*api-ms-win-cr-runtime-l1-1-0.dll。* 請嘗試重新安裝程式以解決此問題。
>
> \- 或 -
>
> 找到庫*hostfxr.dll，* 但從*C：path_to_app\\\<載入\\>主機fxr.dll*失敗。

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET 核心 3.1](#tab/netcore31)

.NET Core 3.1 將 Linux 視為單個作業系統。 支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。

.NET Core 3.1 支援以下 Linux 發行版本/版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                             | 版本               | 架構    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29°                   | x64 |
| Debian                         | 9+                    | x64、ARM32、ARM64 |
| Ubuntu                         | 16.04+                | x64、ARM32、ARM64 |
| Linux Mint                     | 18€                   | x64 |
| openSUSE                       | 15€                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.10°                 | x64、ARM64 |

有關 .NET Core 3.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。

有關如何在 ARM64（內核 4.14+）上安裝 .NET 酷睿 3.1 的詳細資訊，請參閱[在 Linux ARM64 上安裝 .NET 核心 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。

> [!IMPORTANT]
> ARM64 支援需要 Linux 內核 4.14 或更高版本。 某些 linux 發行版本滿足此要求，而其他發行版本則不滿足此要求。 例如，Ubuntu 18.04 受支援，但 Ubuntu 16.04 不支援。

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 將 Linux 視為單個作業系統。 支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。

.NET Core 3.0 支援以下 Linux 發行版本/版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                             | 版本               | 架構    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29°                   | x64 |
| Debian                         | 9+                    | x64、ARM32、ARM64 |
| Ubuntu                         | 16.04+                | x64、ARM32、ARM64 |
| Linux Mint                     | 18€                   | x64 |
| openSUSE                       | 15€                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.8+                  | x64、ARM64 |

有關 .NET Core 3.0 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。

如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2 將 Linux 視為單個作業系統。 支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。

.NET Core 2.2 支援以下 Linux 發行版本/版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                             |  版本                |  架構   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6、7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64， ARM32 |
| Ubuntu                         |  16.04, 18.04, 18.10    | x64， ARM32 |
| Linux Mint                     |  17, 18                 | x64 |
| openSUSE                       |  15€                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

有關 .NET Core 2.2 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 將 Linux 視為單個作業系統。 支援 Linux 發行版本只有一個 Linux 版本（每個晶片體系結構）。

.NET Core 2.1 支援以下 Linux 發行版本/版本：

> [!NOTE]
> 符號`+`表示最小版本。

| OS                             |  版本                |  架構   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  29°                    | x64 |
| Debian                         |  9                      | x64， ARM32 |
| Ubuntu                         |  16.04, 18.04, 19.04, 19.10    | x64， ARM32 |
| Linux Mint                     |  17+                    | x64 |
| openSUSE                       |  15€                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

有關 .NET Core 2.1 支援的作業系統、分發和生命週期策略的詳細資訊，請參閱[.NET Core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。

---

## <a name="linux-distribution-dependencies"></a>Linux 發行版本相依性

根據您的 linux 發行版本，您可能需要安裝其他依賴項。

> [!IMPORTANT]
> 確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。

### <a name="ubuntu"></a>Ubuntu

Ubuntu 分發需要安裝以下庫：

- liblttng-ust0
- libcurl3 (適用於 14.x 及 16.x)
- libcurl4 (適用於 18.x)
- libssl1.0.0
- libkrb5-3
- zlib1g
- libicu52 (適用於 14.x)
- libicu55 (適用於 16.x)
- libicu57 (適用於 17.x)
- libicu60 (適用於 18.x)

對於使用*System.Drawing.Common*程式集的 .NET Core 應用，您還需要以下依賴項：

- libgdiplus（版本 6.0.1 或更高版本）

> [!WARNING]
> 大多數版本的Ubuntu包括早期版本的libgdiplus。 您可以通過將 Mono 存儲庫添加到系統來安裝最新版本的 libgdiplus。 如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。

### <a name="centos-and-fedora"></a>CentOS 與 Fedora

CentOS 發行版本需要安裝下列程式庫：

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib

Fedora 使用者：如果您的 OpenSSL 版本>= 1.1，則需要安裝相容**openssl10**。

對於 .NET Core 2.0，還需要以下依賴項：

- libunwind
- libuuid

有關依賴項的詳細資訊，請參閱[自包含的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。

對於使用*System.Drawing.Common*程式集的 .NET Core 應用，您還需要以下依賴項：

- libgdiplus（版本 6.0.1 或更高版本）

> [!WARNING]
> CentOS 和 Fedora 的大多數版本都包括早期版本的 libgdiplus。 您可以通過將 Mono 存儲庫添加到系統來安裝最新版本的 libgdiplus。 如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/>。

::: zone-end

::: zone pivot="os-macos"

.NET 核心支援以下 macOS 版本：

> [!NOTE]
> 符號`+`表示最小版本。

| .NET 核心版本 | macOS                 | 架構 |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | 高塞拉 （10.13+）  | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | 高塞拉 （10.13+）  | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | 塞拉 （10.12+）       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | 塞拉 （10.12+）       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

從 macOS Catalina（版本 10.15）開始，所有 2019 年 6 月 1 日之後構建的所有軟體都必須使用開發人員 ID 進行公證。 此要求適用于 .NET 核心運行時、.NET 核心 SDK 和使用 .NET Core 創建的軟體。

自 2020 年 2 月 18 日起，對 .NET Core（運行時和 SDK）版本 3.1、3.0 和 2.1 的安裝程式進行了公證。 未對以前發佈的版本進行公證。 如果運行非公證應用，您將看到類似于下圖的錯誤：

![macOS 卡塔利娜公證警報](media/dependencies/macos-notarized-pkg-warning.png)

有關強制公證如何影響 .NET Core（和 .NET 核心應用）的詳細資訊，請參閱使用[macOS Catalina 公證](macos-notarization-issues.md)。

## <a name="libgdiplus"></a>利格迪加

.NET 核心應用程式，使用*系統.繪圖.公共*程式集需要安裝 libgdiplus。

獲得 libgdiplus 的一種簡單方法是使用[macOS 的自製啤酒（"釀造"）](https://brew.sh/)包管理器。 安裝*沖煮*後，通過在終端（命令）提示符上執行以下命令來安裝 libgdiplus：

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>後續步驟

- 要開發和運行應用，請安裝[.NET 核心 SDK（](sdk.md)包括運行時）。
- 要運行其他人創建的應用，請安裝[.NET Core 運行時](runtime.md)。

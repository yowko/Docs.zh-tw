---
title: .NET Core SDK 和執行時間相依性-.NET Core
description: 詳細說明在 Windows、Linux 和 macOS 上安裝 .NET Core SDK 和執行時間的作業系統和 CPU 架構必要條件。
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a535048fc8756b55068098ad61fdc37fc8c1f04e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837000"
---
# <a name="net-core-dependencies-and-requirements"></a>.NET Core 相依性和需求

本文詳細說明 .NET Core 支援哪些作業系統和 CPU 架構。

## <a name="supported-operating-systems"></a>Supported operating systems

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31tabnetcore31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 支援下列 Windows 版本：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                            | {2&gt;版本&lt;2}                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8.1                    | x64、x86        |
| Windows 10 用戶端             | 版本 1607 +                  | x64、x86        |
| Windows Server                | 2012 R2 +                       | x64、x86        |
| Nano 伺服器                   | 版本 1803 +                  | x64、ARM32      |

如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 支援下列 Windows 版本：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                            | {2&gt;版本&lt;2}                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8.1                    | x64、x86        |
| Windows 10 用戶端             | 版本 1607 +                  | x64、x86        |
| Windows Server                | 2012 R2 +                       | x64、x86        |
| Nano 伺服器                   | 版本 1803 +                  | x64、ARM32      |

如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2 支援下列 Windows 版本：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                            | {2&gt;版本&lt;2}                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8.1                    | x64、x86        |
| Windows 10 用戶端             | 版本 1607 +                  | x64、x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64、x86        |
| Nano 伺服器                   | 版本 1803 +                   | x64、ARM32      |

如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 支援下列 Windows 版本：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                            | {2&gt;版本&lt;2}                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8.1                    | x64、x86        |
| Windows 10 用戶端             | 版本 1607 +                  | x64、x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64、x86        |
| Nano 伺服器                   | 版本 1803 +                  | x64            |

如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7/Vista/8.1/Server 2008 R2

如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

安裝下列項目：

- [Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件 Update 3。
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

如果您遇到下列其中一個錯誤，也需要上述需求：

> 程式無法啟動，因為您的電腦遺失了*4.9.0-api* --win---------l1-1。 請嘗試重新安裝程式以修正此問題。
>
> \-或-
>
> 找到*程式庫用 hostfxr* ，但從*C：\\\<path_to_app >\\用 hostfxr*載入它失敗。

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31tabnetcore31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 將 Linux 視為單一作業系統。 針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。

下列 Linux 發行版本/版本支援 .NET Core 3.1：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                             | {2&gt;版本&lt;2}               | 架構    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6、7、8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9+                    | x64、ARM32、ARM64 |
| Ubuntu                         | 16.04+                | x64、ARM32、ARM64 |
| Linux Mint                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.10 +                 | x64、ARM64 |

如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。

如需有關如何在 ARM64 上安裝 .NET Core 3.1 （核心 4.14 +）的詳細資訊，請參閱[在 Linux 上安裝 .Net core 3.0 ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。

> [!IMPORTANT]
> ARM64 支援需要 Linux 核心4.14 或更高版本。 有些 linux 散發套件符合此需求，而有些則不需要。 例如，支援 Ubuntu 18.04，但 Ubuntu 16.04 則否。

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 將 Linux 視為單一作業系統。 針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。

下列 Linux 發行版本/版本支援 .NET Core 3.0：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                             | {2&gt;版本&lt;2}               | 架構    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6、7、8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9+                    | x64、ARM32、ARM64 |
| Ubuntu                         | 16.04+                | x64、ARM32、ARM64 |
| Linux Mint                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.8+                  | x64、ARM64 |

如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。

如需如何在 ARM64 上安裝 .NET Core 3.0 的詳細資訊，請參閱 [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (在 Linux ARM64 上安裝 .NET Core 3.0)。

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2 將 Linux 視為單一作業系統。 針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。

下列 Linux 發行版本/版本支援 .NET Core 2.2：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                             |  {2&gt;版本&lt;2}                |  架構   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6、7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29、30                 | x64 |
| Debian                         |  9                      | x64、ARM32 |
| Ubuntu                         |  16.04、18.04、18.10、19.04    | x64、ARM32 |
| Linux Mint                     |  17、18                 | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 將 Linux 視為單一作業系統。 針對支援的 Linux 發行版本，有單一 Linux 組建（每個晶片架構）。

下列 Linux 發行版本/版本支援 .NET Core 2.1：

> [!NOTE]
> `+` 符號代表最小版本。

| OS                             |  {2&gt;版本&lt;2}                |  架構   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6、7、8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  29 +                    | x64 |
| Debian                         |  9                      | x64、ARM32 |
| Ubuntu                         |  16.04、18.04、19.04、19.10    | x64、ARM32 |
| Linux Mint                     |  17 +                    | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。

---

## <a name="linux-distribution-dependencies"></a>Linux 發行版本相依性

根據您的 linux 散發套件，您可能需要安裝其他相依性。

> [!IMPORTANT]
> 確切的版本和名稱在您選擇的 Linux 發行版本上可能略有出入。

### <a name="ubuntu"></a>Ubuntu

Ubuntu 發行版本需要安裝下列程式庫：

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

針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：

- libgdiplus （6.0.1 版或更新版本）

> [!WARNING]
> 最新版的 Ubuntu 包含舊版的 libgdiplus。 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。 如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。

### <a name="centos-and-fedora"></a>CentOS 與 Fedora

CentOS 發行版本需要安裝下列程式庫：

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib

Fedora 使用者：如果您的 OpenSSL 版本 > = 1.1，您必須安裝相容性 **-compat-openssl10**。

針對 .NET Core 2.0，也需要下列相依性：

- libunwind
- libuuid

如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。

針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：

- libgdiplus （6.0.1 版或更新版本）

> [!WARNING]
> 大部分的 CentOS 和 Fedora 版本都包含舊版的 libgdiplus。 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 libgdiplus。 如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。

::: zone-end

::: zone pivot="os-macos"

下列 macOS 版本支援 .NET Core：

> [!NOTE]
> `+` 符號代表最小版本。

| .NET Core 版本 | macOS                 | 架構 |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | 高塞拉里昂（10.13 +）  | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | 高塞拉里昂（10.13 +）  | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | 塞拉里昂（10.12 +）       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | 塞拉里昂（10.12 +）       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a>libgdiplus

使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。

取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。 安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>後續步驟

- 若要開發及執行應用程式，請安裝[.NET Core SDK](sdk.md) （包括執行時間）。
- 若要執行其他人已建立的應用程式，請安裝[.Net Core 運行](runtime.md)時間。

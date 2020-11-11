---
title: 在 Linux 發行版本上安裝 .NET
description: 瞭解 Linux 發行版本支援在 Linux 上安裝 .NET 的功能。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 898def653811007438184b187fc71ab013a44210
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506723"
---
# <a name="install-net-on-linux"></a>在 Linux 上安裝 .NET

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [安裝在 Linux 上](linux.md)

.NET 適用于不同的 Linux 發行版本。 大部分的 Linux 平臺和散發套件都有每年的主要版本，而且大部分都提供用來安裝 .NET 的套件管理員。 本文說明目前支援的專案，以及使用哪一個套件管理員。

本文的其餘部分將細分為 .NET 所支援的每個主要 Linux 發行版本。 所有 .NET 版本都維持支援，直到 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Linux 散發套件的生命週期結束為止。

為了達到最佳相容性，請選擇長期發行 (LTS) 版本。

## <a name="unsupported-releases"></a>不支援的版本

不再支援下列 .NET 版本 ❌ 。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

下列各節未詳述這些不支援的版本，而且您的里程可能會因嘗試安裝而異。

## <a name="alpine"></a>Alpine

沒有適用于 Alpine 的安裝程式。 您必須使用 [安裝腳本](linux-alpine.md#scripted-install) ，或遵循 [手動安裝](linux-alpine.md#manual-install) 指示。

下表列出目前支援的 .NET 版本，以及其支援的 Alpine 版本。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Alpine 的版本 [達到生命週期結束](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)，否則仍支援這些版本。

- ✔️表示仍支援 Alpine 或 .NET 版本。
- ❌指出該 Alpine 版本不支援 Alpine 或 .net 版本。
- 當版本的 Alpine 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| Alpine                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3.12](linux-alpine.md)  | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [3.11](linux-alpine.md)  | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [3.10](linux-alpine.md)  | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌ [3.9](linux-alpine.md)   | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌ [3.8](linux-alpine.md)   | ✔️2。1        | ✔️3。1        | ❌ 5.0 |

如需詳細資訊，請參閱 [在 Alpine 上安裝 .net](linux-alpine.md)。

## <a name="centos"></a>CentOS

CentOS 7 使用 Yum 作為套件管理員，而 CentOS 8 使用 DNF。

下表是 CentOS 7 和 CentOS 8 上目前支援的 .NET 版本清單。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 CentOS 版本，否則仍支援這些版本。

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |

如需詳細資訊，請參閱 [在 CentOS 上安裝 .net](linux-centos.md)。

## <a name="debian"></a>Debian

Debian 使用 APT (Advanced Package Tool) 作為套件管理員。

下表列出目前支援的 .NET 版本，以及其支援的 Debian 版本。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Debian 的版本 [達到生命週期結束](https://wiki.debian.org/DebianReleases)，否則仍支援這些版本。

- ✔️表示仍支援 Debian 或 .NET 版本。
- ❌指出該 Debian 版本不支援 Debian 或 .net 版本。
- 當版本的 Debian 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️2。1        | ❌ 3.1        | ❌ 5.0 |

如需詳細資訊，請參閱 [在 Debian 上安裝 .net](linux-debian.md)。

## <a name="fedora"></a>Fedora

Fedora 使用 DNF 作為其套件管理員。

下表列出目前支援的 .NET 版本，以及其支援的 Fedora 版本。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Fedora 的版本 [達到生命週期結束](https://fedoraproject.org/wiki/End_of_life)，否則仍支援這些版本。

- ✔️表示仍支援 Fedora 或 .NET 版本。
- ❌指出該 Fedora 版本不支援 Fedora 或 .net 版本。
- 當版本的 Fedora 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [33](linux-fedora.md#fedora-33-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ❌[31](linux-fedora.md#fedora-31-) | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌[29](linux-fedora.md#fedora-29-) | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌[28](linux-fedora.md#fedora-28-) | ✔️2。1        | ❌ 3.1        | ❌ 5.0 |
| ❌[27](linux-fedora.md#fedora-27-) | ✔️2。1        | ❌ 3.1        | ❌ 5.0 |

如需詳細資訊，請參閱 [在 Fedora 上安裝 .net](linux-fedora.md)。

## <a name="opensuse"></a>openSUSE

openSUSE 會使用 zypper 作為套件管理員。

下表是 openSUSE 15 上目前支援的 .NET 版本清單。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 openSUSE 版本，否則仍支援這些版本。

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️2。1        | ✔️3。1        | ✔️5。0 |

如需詳細資訊，請參閱 [在 openSUSE 上安裝 .net](linux-opensuse.md)。

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) 使用 yum (RHEL 7) 和 DNF (RHEL 8) 作為套件管理員。

下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET 版本清單。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或已不再支援 RHEL 版本，否則仍支援這些版本。

- ✔️表示仍支援 RHEL 或 .NET 的版本。
- ❌表示該 rhel 版本不支援 rhel 或 .net 的版本。
- 當版本的 RHEL 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |

如需詳細資訊，請參閱 [在 RHEL 上安裝 .net](linux-rhel.md)。

## <a name="sles"></a>SLES

SLES 使用 zypper 作為套件管理員。

下表是 SLES 12 SP2 和 SLES 15 目前支援的 .NET 版本清單。 在 [.net 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 SLES 版本之前，會持續支援這些版本。

- ✔️表示仍支援 SLES 或 .NET 版本。
- ❌表示該 sles 版本不支援 sles 或 .net 的版本。
- 當 SLES 和某個版本的 .NET 都✔️時，支援該作業系統和 .NET 組合。

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |

如需詳細資訊，請參閱 [在 SLES 上安裝 .net](linux-sles.md)。

## <a name="ubuntu"></a>Ubuntu

Ubuntu 使用 APT (Advanced Package Tool) 作為套件管理員。

下表表示 Ubuntu 和 .NET 的支援狀態。

- ✔️表示仍支援 Ubuntu 或 .NET 版本。
- ❌表示該 ubuntu 版本不支援 ubuntu 或 .net 版本。
- 當 Ubuntu 版本和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20.10](linux-ubuntu.md#2010-)       | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [20.04 (LTS) ](linux-ubuntu.md#2004-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ❌[19.10](linux-ubuntu.md#1910-)       | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ❌[19.04](linux-ubuntu.md#1904-)       | ✔️2。1        | ✔️3。1        | ❌ 5.0 |
| ❌[18.10](linux-ubuntu.md#1810-)       | ✔️2。1        | ❌ 3.1        | ❌ 5.0 |
| ✔️ [18.04 (LTS) ](linux-ubuntu.md#1804-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ❌ [17.10](linux-ubuntu.md#1710-)       | ✔️2。1        | ❌ 3.1        | ❌ 5.0 |
| ❌ [17.04](linux-ubuntu.md#1704-)       | ✔️2。1        | ❌ 3.1        | ❌ 5.0 |
| ❌[16.10](linux-ubuntu.md#1610-)       | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ✔️ [16.04 (LTS) ](linux-ubuntu.md#1604-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |

如需詳細資訊，請參閱 [在 Ubuntu 上安裝 .net](linux-ubuntu.md)。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .net](how-to-detect-installed-versions.md?pivots=os-linux)。
- [教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。
- [教學課程：將 .net 應用程式](../docker/build-container.md)。

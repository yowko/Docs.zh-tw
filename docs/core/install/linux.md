---
title: 安裝 .NET Core 和 Linux 發行版本
description: 瞭解哪些 Linux 散發套件支援在 Linux 上安裝 .NET Core。
author: thraka
ms.author: adegeo
ms.date: 06/01/2020
ms.openlocfilehash: e668ad733481c2d9b73994b6344b38768f5851fe
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903372"
---
# <a name="install-net-core-on-linux"></a>在 Linux 上安裝 .NET Core

.NET Core 適用于不同的 Linux 發行版本。 大部分的 Linux 平臺和發佈都有每年的主要版本，而且大部分都提供用來安裝 .NET Core 的套件管理員。 本文說明目前支援的專案，以及所使用的套件管理員。

本文的其餘部分會細分 .NET Core 支援的每個主要 Linux 散發套件。 所有 .NET Core 版本都持續支援，直到[.Net core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或 Linux 散發達到生命週期結束為止。

為求最佳相容性，請選擇長期發行（LTS）版本。

## <a name="unsupported-releases"></a>不支援的版本

已不再支援下列 .NET Core 版本 ❌ 。 這些下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

這些不支援的版本在下列各節中並未詳述，而您的里程可能會因您嘗試安裝而異。

## <a name="alpine"></a>Alpine

沒有安裝程式可供 Alpine。 您必須使用[安裝腳本](linux-alpine.md#scripted-install)或遵循[手動安裝](linux-alpine.md#manual-install)指示。

下表列出目前支援的 .NET Core 版本，以及支援的 Alpine 版本。 在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或[Alpine 版本達到生命週期結束](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)之前，這些版本仍受到支援。

- ✔️表示仍然支援 Alpine 或 .NET Core 的版本。
- A ❌ 表示該 Alpine 版本不支援 Alpine 或 .Net Core 的版本。
- 當 Alpine 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| Alpine                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3.12](linux-alpine.md)  | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [3.11](linux-alpine.md)  | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [3.10](linux-alpine.md)  | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [3.9](linux-alpine.md)   | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌ [3.8](linux-alpine.md)   | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |

如需詳細資訊，請參閱[在 Alpine 上安裝 .Net Core](linux-alpine.md)。

## <a name="centos"></a>CentOS

CentOS 7 使用 Yum 作為套件管理員，而 CentOS 8 使用 DNF。

下表是 CentOS 7 和 CentOS 8 上目前支援的 .NET Core 版本清單。 在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或不再支援 CentOS 版本之前，這些版本都會持續受到支援。

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

如需詳細資訊，請參閱[在 CentOS 上安裝 .Net Core](linux-centos.md)。

## <a name="debian"></a>Debian

Debian 使用 APT （Advanced Package Tool）做為套件管理員。

下表列出目前支援的 .NET Core 版本，以及支援的 Debian 版本。 在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或[Debian 版本達到生命週期結束](https://wiki.debian.org/DebianReleases)之前，這些版本仍受到支援。

- ✔️表示仍然支援 Debian 或 .NET Core 的版本。
- A ❌ 表示該 Debian 版本不支援 Debian 或 .Net Core 的版本。
- 當 Debian 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |

如需詳細資訊，請參閱[在 Debian 上安裝 .Net Core](linux-debian.md)。

## <a name="fedora"></a>Fedora

Fedora 會使用 DNF 作為其套件管理員。

下表列出目前支援的 .NET Core 版本，以及支援的 Fedora 版本。 在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或[Fedora 版本達到生命週期結束](https://fedoraproject.org/wiki/End_of_life)之前，這些版本仍受到支援。

- ✔️表示仍然支援 Fedora 或 .NET Core 的版本。
- A ❌ 表示該 Fedora 版本不支援 Fedora 或 .Net Core 的版本。
- 當 Fedora 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️2。1        | ✔️3。1        | ❌5.0 預覽 |
| ❌[29](linux-fedora.md#fedora-29-) | ✔️2。1        | ✔️3。1        | ❌5.0 預覽 |
| ❌[28](linux-fedora.md#fedora-28-) | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ❌[27](linux-fedora.md#fedora-27-) | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |

如需詳細資訊，請參閱[在 Fedora 上安裝 .Net Core](linux-fedora.md)。

## <a name="opensuse"></a>openSUSE

openSUSE 使用 zypper 做為封裝管理員。

下表是 openSUSE 15 上目前支援的 .NET Core 版本清單。 在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或不再支援 openSUSE 版本之前，這些版本都會持續受到支援。

- ✔️表示仍然支援 openSUSE 或 .NET Core 的版本。
- A ❌ 表示該 openSUSE 版本不支援 openSUSE 或 .Net Core 的版本。
- 當 openSUSE 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

如需詳細資訊，請參閱[在 openSUSE 上安裝 .Net Core](linux-opensuse.md)。

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux （RHEL）會使用 yum （RHEL 7）和 DNF （RHEL 8）做為套件管理員。

下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET Core 版本清單。 在[.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或已不再支援 RHEL 版本之前，會持續支援這些版本。

- ✔️表示仍然支援 RHEL 或 .NET Core 的版本。
- A ❌ 表示該 rhel 版本不支援 rhel 或 .Net Core 的版本。
- 當 RHEL 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

如需詳細資訊，請參閱[在 RHEL 上安裝 .Net Core](linux-rhel.md)。

## <a name="sles"></a>SLES

SLES 會使用 zypper 作為套件管理員。

下表是 SLES 12 SP2 和 SLES 15 上目前支援的 .NET Core 版本清單。 在[.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或不再支援 SLES 版本之前，會持續支援這些版本。

- ✔️表示仍然支援 SLES 或 .NET Core 的版本。
- A ❌ 表示該 sles 版本不支援 sles 或 .Net Core 的版本。
- 當 SLES 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

如需詳細資訊，請參閱[在 SLES 上安裝 .Net Core](linux-sles.md)。

## <a name="ubuntu"></a>Ubuntu

Ubuntu 會使用 APT （Advanced Package Tool）作為套件管理員。

下表代表 Ubuntu 和 .NET Core 的支援狀態。

- ✔️表示仍然支援 Ubuntu 或 .NET Core 的版本。
- A ❌ 表示該 ubuntu 版本不支援 ubuntu 或 .Net Core 的版本。
- 當 Ubuntu 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20.04 （LTS）](linux-ubuntu.md#2004-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [19.10](linux-ubuntu.md#1910-)       | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌[19.04](linux-ubuntu.md#1904-)       | ✔️2。1        | ✔️3。1        | ❌5.0 預覽 |
| ❌[18.10](linux-ubuntu.md#1810-)       | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ✔️ [18.04 （LTS）](linux-ubuntu.md#1804-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌ [17.10](linux-ubuntu.md#1710-)       | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ❌ [17.04](linux-ubuntu.md#1704-)       | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ❌[16.10](linux-ubuntu.md#1610-)       | ❌2.1        | ❌3.1        | ❌5.0 預覽 |
| ✔️ [16.04 （LTS）](linux-ubuntu.md#1604-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

如需詳細資訊，請參閱[在 Ubuntu 上安裝 .Net Core](linux-ubuntu.md)。

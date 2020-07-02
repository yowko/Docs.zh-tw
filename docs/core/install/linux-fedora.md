---
title: 在 Fedora 上安裝 .NET Core-.NET Core
description: 示範在 Fedora 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c90c08eefa074fa139642a268f879af79d7280da
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619477"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a>在 Fedora 上安裝 .NET Core SDK 或 .NET Core 執行時間

Fedora 上支援 .NET Core。 本文說明如何在 Fedora 上安裝 .NET Core。 當 Fedora 版本不支援時，該版本就不再支援 .NET Core。 不過，這些指示可以協助您取得在這些版本上執行的 .NET Core，即使它不受支援也一樣。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>支援的發行版本

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

已不再支援下列 .NET Core 版本。 這些下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a>Fedora 32 ✔️

.NET Core 3.1 適用于 Fedora 32 的預設封裝存放庫。

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a>Fedora 31 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a>Fedora 30❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a>Fedora 29❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a>Fedora 28❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a>Fedora 27❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a>針對套件管理員進行疑難排解

本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。

### <a name="failed-to-fetch"></a>無法提取

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>抓取

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>相依性

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式](../tutorials/with-visual-studio-code.md)

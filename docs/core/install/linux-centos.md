---
title: 在 CentOS 上安裝 .NET Core-.NET Core
description: 示範在 CentOS 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7937502067e1717fd7f5c973c64ad33ae2a443a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538614"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-centos"></a>在 CentOS 上安裝 .NET Core SDK 或 .NET Core 執行時間

CentOS 支援 .NET Core。 本文說明如何在 CentOS 上安裝 .NET Core。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>支援的發行版本

下表是 CentOS 7 和 CentOS 8 上目前支援的 .NET Core 版本清單。 在 [.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 CentOS 版本之前，會持續支援這些版本。

- ✔️表示仍支援 CentOS 或 .NET Core 的版本。
- ❌指出該 CentOS 版本不支援 CentOS 或 .Net Core 的版本。
- 當版本的 CentOS 和 .NET Core 版本都✔️時，支援該作業系統和 .NET 組合。

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (僅限手動安裝)  |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#centos-8-) | ✔️2。1        | ✔️3。1        | ✔️5.0 預覽 |
| ✔️ [7](#centos-7-) | ✔️2。1        | ✔️3。1        | ✔️5.0 預覽 |

不再支援下列 .NET Core 版本。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a>CentOS 8 ✔️

CentOS 8 的預設封裝存放庫中有提供 .NET Core 3.1。

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="centos-7-"></a>CentOS 7 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-31](includes/linux-install-31-yum.md)]

## <a name="troubleshoot-the-package-manager"></a>針對套件管理員進行疑難排解

本節提供使用套件管理員安裝 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。

### <a name="unable-to-find-package"></a>找不到套件

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>無法提取

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>單元

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>相依性

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式](../tutorials/with-visual-studio-code.md)

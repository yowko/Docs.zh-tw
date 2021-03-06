---
title: 在 CentOS 上安裝 .NET-.NET
description: 示範在 CentOS 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7e73f90a1f1f7e11e592b1b074f243c9f5b32ced
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970859"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a>在 CentOS 上安裝 .NET SDK 或 .NET 執行時間

CentOS 支援 .NET。 本文說明如何在 CentOS 上安裝 .NET。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>支援的發行版本

下表是 CentOS 7 和 CentOS 8 上目前支援的 .NET 版本清單。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 CentOS 版本，否則仍支援這些版本。

- ✔️表示仍支援 CentOS 或 .NET 版本。
- ❌指出該 CentOS 版本不支援 CentOS 或 .net 版本。
- 當版本的 CentOS 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#centos-8-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [7](#centos-7-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |

不再支援下列 .NET 版本。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="remove-preview-versions"></a>移除預覽版本

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="centos-8-"></a>CentOS 8 ✔️

CentOS 8 的預設封裝存放庫中有提供 .NET 5.0。

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a>CentOS 7 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>針對套件管理員進行疑難排解

本節提供使用套件管理員安裝 .NET 時可能會遇到的常見錯誤的相關資訊。

### <a name="unable-to-find-package"></a>找不到套件

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>無法提取

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>相依性

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="next-steps"></a>後續步驟

- [如何啟用 .NET CLI 的 TAB 鍵自動完成](../tools/enable-tab-autocomplete.md)
- [教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code](../tutorials/with-visual-studio-code.md)

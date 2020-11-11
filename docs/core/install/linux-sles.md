---
title: 在 SLES 上安裝 .NET-.NET
description: 示範在 SLES 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 558574116aac2a3c755481069641e81a435a2a43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506866"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a>在 SLES 上安裝 .NET SDK 或 .NET 執行時間

SLES 支援 .NET。 本文說明如何在 SLES 上安裝 .NET。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a>支援的發行版本

下表是 SLES 12 SP2 和 SLES 15 目前支援的 .NET 版本清單。 在 [.net 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 SLES 版本之前，會持續支援這些版本。

- ✔️表示仍支援 SLES 或 .NET 版本。
- ❌表示該 sles 版本不支援 sles 或 .net 的版本。
- 當 SLES 和某個版本的 .NET 都✔️時，支援該作業系統和 .NET 組合。

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5。0 |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](#sles-15-)     | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [12 SP2](#sles-12-) | ✔️2。1        | ✔️3。1        | ✔️5。0 |

不再支援下列 .NET Core 版本。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a>SLES 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

目前，SLES 15 Microsoft 存放庫安裝套件會將 *Microsoft 生產* 的存放庫檔案安裝到錯誤的目錄，防止 zypper 找到 .net 套件。 若要修正此問題，請在正確的目錄中建立符號。

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a>SLES 12 ✔️

.NET 需要 SP2 作為 SLES 12 系列的最小值。

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>針對套件管理員進行疑難排解

本節提供使用套件管理員安裝 .NET 時可能會遇到的常見錯誤的相關資訊。

### <a name="failed-to-fetch"></a>無法提取

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>相依性

當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。 但是，如果您手動安裝 .NET 或發行獨立應用程式，則必須確定已安裝這些程式庫：

- krb5
- libicu
- libopenssl1_1

如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您必須安裝 **相容性 compat-openssl10** 。

如需相依性的詳細資訊，請參閱 [獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。

若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：

- [libgdiplus (6.0.1 版或更新版本) ](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。 如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code](../tutorials/with-visual-studio-code.md)

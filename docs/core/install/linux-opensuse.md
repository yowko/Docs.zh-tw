---
title: 在 openSUSE 上安裝 .NET Core-.NET Core
description: 示範在 openSUSE 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619464"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a>在 openSUSE 上安裝 .NET Core SDK 或 .NET Core 執行時間

OpenSUSE 上支援 .NET Core。 本文說明如何在 openSUSE 上安裝 .NET Core。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>支援的發行版本

下表是 openSUSE 15 上目前支援的 .NET Core 版本清單。 在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或不再支援 openSUSE 版本之前，這些版本都會持續受到支援。

- ✔️表示仍然支援 openSUSE 或 .NET Core 的版本。
- A ❌ 表示該 openSUSE 版本不支援 openSUSE 或 .Net Core 的版本。
- 當 openSUSE 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](#opensuse-15-)     | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

已不再支援下列 .NET Core 版本。 這些下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a>openSUSE 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>針對套件管理員進行疑難排解

本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。

### <a name="failed-to-fetch"></a>無法提取

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>抓取

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>相依性

當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。 但是，如果您手動安裝 .NET Core 或發行獨立的應用程式，您必須確定已安裝這些程式庫：

- krb5
- libicu
- libopenssl1_0_0

如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您將需要安裝**相容性 compat-openssl10**。

如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。

針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：

- [libgdiplus （6.0.1 版或更新版本）](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的*libgdiplus* 。 如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/> 。

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式](../tutorials/with-visual-studio-code.md)

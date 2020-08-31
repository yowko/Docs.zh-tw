---
title: 在 Debian 上安裝 .NET Core-.NET Core
description: 示範在 Debian 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: a9ccc461362b1be3e5bc2ee7d13d5d7d383192e4
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053153"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a>在 Debian 上安裝 .NET Core SDK 或 .NET Core 執行時間

本文說明如何在 Debian 上安裝 .NET Core。 當 Debian 版本不受支援時，就不再支援該版本的 .NET Core。 不過，這些指示可協助您讓 .NET Core 在這些版本上執行，即使它不受支援也是一樣。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>支援的發行版本

下表列出目前支援的 .NET Core 版本，以及其支援的 Debian 版本。 在 [.Net Core 的版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Debian 的版本 [達到生命週期結束](https://wiki.debian.org/DebianReleases)之前，會持續支援這些版本。

- ✔️表示仍支援 Debian 或 .NET Core 的版本。
- ❌指出該 Debian 版本不支援 Debian 或 .Net Core 的版本。
- 當版本的 Debian 和 .NET Core 版本都✔️時，支援該作業系統和 .NET 組合。

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (僅限手動安裝)  |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](#debian-10-)     | ✔️2。1        | ✔️3。1        | ✔️5.0 預覽 |
| ✔️ [9](#debian-9-)       | ✔️2。1        | ✔️3。1        | ✔️5.0 預覽 |
| ❌[8](#debian-8-)       | ✔️2。1        | ❌ 3.1        | ❌ 5.0 預覽 |

不再支援下列 .NET Core 版本。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a>Debian 10 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a>Debian 9 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a>Debian 8 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a>APT 更新 SDK 或執行時間

當 .NET Core 有新的修補程式版本可供使用時，您可以使用下列命令透過 APT 升級：

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a>APT 疑難排解

本節提供使用 APT 來安裝 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。

### <a name="unable-to-locate"></a>找不到

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a>無法提取

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a>單元

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>相依性

當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。 但是，如果您手動安裝 .NET Core 或發行獨立應用程式，則必須確定已安裝這些程式庫：

- libc6
- libgcc1
- libgssapi-krb5.keytab-2
- 適用于 8.x) 的 libicu52 (
- libicu57 (for 2.x) 
- libicu63 (for 2.x) 
- 適用于 11. x) 的 libicu67 (
- 適用于 8.x) 的 libssl1.0.0 1.0.0 (
- libssl1.0.0 1.1 (for 2.x-11. x) 
- libstdc + + 6
- zlib1g

若為使用 system.string 元件的 .NET Core *應用程式，* 您也需要下列相依性：

- libgdiplus (6.0.1 版或更新版本) 

  > [!WARNING]
  > 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。 如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式](../tutorials/with-visual-studio-code.md)

---
title: 在 Ubuntu 上安裝 .NET Core-.NET Core
description: 示範在 Ubuntu 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c590bd89b718a5cd31dae9f83049eac910cb4049
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863887"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a>在 Ubuntu 上安裝 .NET Core SDK 或 .NET Core 執行時間

Ubuntu 支援 .NET Core。 本文說明如何在 Ubuntu 上安裝 .NET Core。 當 Ubuntu 版本不支援時，該版本就不再支援 .NET Core。 不過，這些指示可以協助您取得在這些版本上執行的 .NET Core，即使它不受支援也一樣。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>支援的發行版本

下表列出目前支援的 .NET Core 版本，以及支援的 Ubuntu 版本。 這些版本持續支援，直到[.Net Core 版本達到支援的終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或 Ubuntu 的版本[達到生命週期的結束](https://wiki.ubuntu.com/Releases)為止。

- ✔️表示仍然支援 Ubuntu 或 .NET Core 的版本。
- A ❌ 表示該 ubuntu 版本不支援 ubuntu 或 .Net Core 的版本。
- 當 Ubuntu 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20.04 （LTS）](#2004-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌[19.10](#1910-)       | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌[19.04](#1904-)       | ✔️2。1        | ✔️3。1        | ❌5.0 預覽 |
| ❌[18.10](#1810-)       | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ✔️ [18.04 （LTS）](#1804-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌[17.10](#1710-)       | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ❌ [17.04](#1704-)       | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ❌[16.10](#1610-)       | ❌2.1        | ❌3.1        | ❌5.0 預覽 |
| ✔️ [16.04 （LTS）](#1604-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

已不再支援下列 .NET Core 版本。 這些下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a>20.04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a>19.10❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a>19.04❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a>18.10❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a>18.04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a>17.10❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a>17.04❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a>16.10❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a>16.04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a>APT 更新 SDK 或執行時間

當 .NET Core 有新的修補程式版本可供使用時，您只要使用下列命令，即可透過 APT 進行升級：

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a>APT 疑難排解

本節提供您在使用 APT 安裝 .NET Core 時可能會遇到的常見錯誤資訊。

### <a name="unable-to-locate"></a>找不到

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
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

## <a name="snap"></a>抓取

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>相依性

當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。 但是，如果您手動安裝 .NET Core 或發行獨立的應用程式，您必須確定已安裝這些程式庫：

- libc6
- libgcc1
- libgssapi-krb5-krb5-2
- libicu52 (適用於 14.x)
- libicu55 (適用於 16.x)
- libicu60 (適用於 18.x)
- libicu66 （適用于 20. x）
- libssl1.0.0 1.0.0 （適用于 14. x、16. x）
- libssl1.0.0 1.1 （適用于 18. x、20. x）
- libstdc + + 6
- zlib1g

針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：

- libgdiplus （6.0.1 版或更新版本）

  > [!WARNING]
  > 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的*libgdiplus* 。 如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/> 。

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>接下來的步驟

- [教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式](../tutorials/with-visual-studio-code.md)

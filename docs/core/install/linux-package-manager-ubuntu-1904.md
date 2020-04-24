---
title: 在 Ubuntu 19.04 套件管理員上安裝 .NET 內核 - .NET Core
description: 使用包管理器在 Ubuntu 19.04 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 3f338832185ed626289141f48cec88c1bf2e3a33
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645596"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Ubuntu 19.04 套件管理員 - 安裝 .NET 核心

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

本文介紹如何使用包管理器在 Ubuntu 19.04 上安裝 .NET Core。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>新增 Microsoft 儲存函式庫金鑰和來源

在安裝 .NET 之前,您需要:

- 將 Microsoft 包簽署金鑰添加到受信任金鑰清單中。
- 將儲存庫添加到包管理員。
- 安裝所需的依賴項。

每部電腦只需要執行這項作業一次。

打開終端並運行以下命令。

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>安裝 .NET 核心 SDK

更新可供安裝的產品,然後安裝 .NET 核心 SDK。 在終端中,運行以下命令。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> 如果收到類似於**找不到包 dotnet-sdk-3.1**的錯誤訊息,請參閱[對套件管理員部分進行故障排除](#troubleshoot-the-package-manager)。

## <a name="install-the-aspnet-core-runtime"></a>安裝ASP.NET核心執行時

更新可用於安裝的產品,然後安裝ASP.NET核心運行時。 在終端中,運行以下命令。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> 如果收到類似於**無法找到包 aspnetcore-運行時-3.1**的錯誤消息,請參閱[「包管理器疑難解答](#troubleshoot-the-package-manager)」部分。

## <a name="install-the-net-core-runtime"></a>安裝 .NET 核心執行時

更新可用於安裝的產品,然後安裝 .NET Core 運行時。 在終端中,運行以下命令。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> 如果收到類似於**找不到包 dotnet-執行時-3.1**的錯誤訊息,請參閱[套件管理器部分的故障排除](#troubleshoot-the-package-manager)。

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>排除套件管理員故障

本節提供有關在使用包管理器安裝 .NET Core 時可能得到的常見錯誤的資訊。

### <a name="unable-to-locate"></a>無法定位

如果收到類似於**無法找到包 [.NET Core 包]** 的錯誤消息,請運行以下命令。

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

如果這不起作用,則可以使用以下命令運行手動安裝。

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>無法擷取

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

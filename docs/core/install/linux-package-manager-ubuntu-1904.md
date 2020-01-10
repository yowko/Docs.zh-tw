---
title: 在 Ubuntu 19.04 套件管理員上安裝 .NET Core-.NET Core
description: 使用套件管理員在 Ubuntu 19.04 上安裝 .NET Core SDK 和執行階段。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a229369b9252d08fe5fc83add98c694214ce5ba5
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740603"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Ubuntu 19.04 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

本文說明如何使用套件管理員在 Ubuntu 19.04 上安裝 .NET Core。 如果您僅要安裝執行階段，我們建議您安裝 [ASP.NET Core runtime](#install-the-aspnet-core-runtime)，因為它同時包含 .net Core 和 ASP.NET Core 執行階段。

## <a name="register-microsoft-key-and-feed"></a>註冊 Microsoft 金鑰和總結

安裝 .NET 之前，您必須：

- 註冊 Microsoft 金鑰。
- 註冊產品存放庫。
- 安裝必要的相依性。

每部電腦只需要執行這項作業一次。

開啟終端機並執行下列命令。

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

更新可供安裝的產品，然後安裝 .NET Core SDK。 在您的終端機中，執行下列命令。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> 如果您收到類似 [**找不到封裝 dotnet-sdk-3.1**] 的錯誤訊息，請參閱[疑難排解套件管理員](#troubleshoot-the-package-manager)一節。

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行階段

更新可供安裝的產品，然後安裝 ASP.NET Core 執行階段。 在您的終端機中，執行下列命令。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> 如果您收到類似「找不到套件 aspnetcore-runtime-3.1」的錯誤訊息，請參閱[針對套件管理員進行疑難排解](#troubleshoot-the-package-manager)一節。

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行階段

更新可供安裝的產品，然後安裝 .NET Core 執行階段。 在您的終端機中，執行下列命令。

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> 如果您收到類似「找不到套件 dotnet-runtime-3.1」的錯誤訊息，請參閱[針對套件管理員進行疑難排解](#troubleshoot-the-package-manager)一節。

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>針對套件管理員進行疑難排解

如果您收到類似「**找不到封裝 {.Net Core 封裝}** 」的錯誤訊息，請執行下列命令。

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

如果無法解決問題，您可以使用下列命令來執行手動安裝。

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

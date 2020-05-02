---
title: 在 Linux 上安裝 .NET Core CentOS 8 套件管理員-.NET Core
description: 使用套件管理員，在 CentOS 8 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: b4cf5975e18aa8dfa8649c0d038caf38d648ad86
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728516"
---
# <a name="centos-8-package-manager---install-net-core"></a>CentOS 8 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

本文說明如何使用套件管理員在 CentOS 8 上安裝 .NET Core。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行時間

在您的終端機中，執行下列命令。

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

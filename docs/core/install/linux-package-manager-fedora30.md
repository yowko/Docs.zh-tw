---
title: 在 Fedora 上安裝 .NET Core-套件管理員-.NET Core
description: 使用套件管理員在 Fedora 30 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 7996cd74a250370c2212ca1977cb8c44ad0bd078
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836973"
---
# <a name="fedora-30-package-manager---install-net-core"></a>Fedora 30 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

本文說明如何使用套件管理員在 Fedora 30 上安裝 .NET Core。 如果您要安裝執行時間，我們建議您安裝[ASP.NET Core 運行](#install-the-aspnet-core-runtime)時間，因為它同時包含 .net Core 和 ASP.NET Core 執行時間。

## <a name="register-microsoft-key-and-feed"></a>註冊 Microsoft 金鑰和摘要

安裝 .NET 之前，您必須：

- 註冊 Microsoft 金鑰
- 註冊產品存放庫
- 安裝必要的相依性

每部電腦只需要執行這項作業一次。

開啟終端機並執行下列命令。

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

更新可供安裝的產品，然後安裝 .NET Core SDK。 在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行時間

更新可供安裝的產品，然後安裝 ASP.NET 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

更新可供安裝的產品，然後安裝 .NET Core 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

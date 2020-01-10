---
title: 在 CentOS 7 上安裝 .NET Core-套件管理員-.NET Core
description: 使用封裝管理員，在 CentOS 7 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a7b4a76d780714850fe0792f51f1fa1282f6525d
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740738"
---
# <a name="centos-7-package-manager---install-net-core"></a>CentOS 7 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

本文說明如何使用套件管理員，在 CentOS 7 上安裝 .NET Core。 如果您要安裝執行時間，我們建議您安裝[ASP.NET Core 運行](#install-the-aspnet-core-runtime)時間，因為它同時包含 .net Core 和 ASP.NET Core 執行時間。

## <a name="register-microsoft-key-and-feed"></a>註冊 Microsoft 金鑰和總結

安裝 .NET 之前，您必須：

- 註冊 Microsoft 金鑰。
- 註冊產品存放庫。
- 安裝必要的相依性。

每部電腦只需要執行這項作業一次。

開啟終端機並執行下列命令。

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

更新可供安裝的產品，然後安裝 .NET Core SDK。 在您的終端機中，執行下列命令。

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行時間

更新可供安裝的產品，然後安裝 ASP.NET 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

更新可供安裝的產品，然後安裝 .NET Core 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

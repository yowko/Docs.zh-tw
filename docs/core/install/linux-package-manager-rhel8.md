---
title: 在 Linux RHEL 8 套件管理員上安裝 .NET Core-.NET Core
description: 使用套件管理員，在 RHEL 8 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: 8829e842e920e6abd4184b5140f80bb016acace2
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728233"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

本文說明如何使用套件管理員，在 Red Hat Enterprise Linux （RHEL）8上安裝 .NET Core。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>註冊您的 Red Hat 訂用帳戶

若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。 如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

向訂閱管理員註冊之後，您就可以開始安裝和啟用 .NET Core SDK。 在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行時間

向訂閱管理員註冊之後，您就可以開始安裝和啟用 ASP.NET Core 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

向訂用帳戶管理員註冊之後，您就可以開始安裝和啟用 .NET Core 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="see-also"></a>另請參閱

- [在 Red Hat Enterprise Linux 8 上使用 .NET Core 3。1](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)

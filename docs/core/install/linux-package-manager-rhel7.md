---
title: 在 Linux RHEL 7 套件管理員上安裝 .NET Core-.NET Core
description: 使用套件管理員，在 RHEL 7 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: f17a410ccea1ef4dec32de1d80ef6aac889aa6f3
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836952"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

本文說明如何使用套件管理員，在 RHEL 7 上安裝 .NET Core。 RHEL 7 尚無法使用 .NET Core 3.1。

## <a name="register-your-red-hat-subscription"></a>註冊您的 Red Hat 訂用帳戶

若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。 如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

向訂閱管理員註冊之後，您就可以開始安裝和啟用 .NET Core SDK。 在您的終端機中，執行下列命令以啟用 RHEL 7 dotnet 通道並安裝。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行時間

向訂閱管理員註冊之後，您就可以開始安裝和啟用 ASP.NET Core 執行時間。 在您的終端機中，執行下列命令。

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

向訂用帳戶管理員註冊之後，您就可以開始安裝和啟用 .NET Core 執行時間。 在您的終端機中，執行下列命令。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a>請參閱

- [在 Red Hat Enterprise Linux 7 上使用 .NET Core 3.0](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)

---
title: 在 Linux RHEL 8 套裝軟體管理器上安裝 .NET 核心 - .NET 核心
description: 使用包管理器在 RHEL 8 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849807"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 套裝軟體管理器 - 安裝 .NET 核心

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

本文介紹如何使用包管理器在 RHEL 8 上安裝 .NET Core。

## <a name="register-your-red-hat-subscription"></a>註冊您的紅帽訂閱

要在 RHEL 上安裝來自紅帽的 .NET 核心，首先需要使用紅帽訂閱管理器進行註冊。 如果系統上尚未完成此操作，或者不確定，請參閱[.NET Core 的紅帽產品文檔](https://access.redhat.com/documentation/net_core/)。

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

向訂閱管理器註冊後，即可安裝並啟用 .NET 核心 SDK。 在終端中，運行以下命令。

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>安裝ASP.NET核心運行時

向訂閱管理器註冊後，即可安裝並啟用ASP.NET核心運行時。 在終端中，運行以下命令。

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET 核心運行時

註冊訂閱管理器後，即可安裝並啟用 .NET 核心運行時。 在終端中，運行以下命令。

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>另請參閱

- [在紅帽企業 Linux 8 上使用 .NET 核心 3.1](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)

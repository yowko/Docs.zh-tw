---
title: 在 Fedora 32 上安裝 .NET Core-套件管理員-.NET Core
description: 使用套件管理員在 Fedora 32 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624963"
---
# <a name="fedora-32-package-manager---install-net-core"></a>Fedora 32 套件管理員-安裝 .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

本文說明如何使用套件管理員在 Fedora 32 上安裝 .NET Core。

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

從 Fedora 32 開始，.NET Core 3.1 可在 Fedora 的預設封裝存放庫中取得。

## <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

安裝 .NET Core SDK。 在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>安裝 ASP.NET Core 執行時間

安裝 ASP.NET 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

安裝 .NET Core 執行時間。 在您的終端機中，執行下列命令。

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

若要安裝其他版本的 .NET Core，請手動安裝[.NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install)或[.net core 運行](runtime.md?pivots=os-linux#download-and-manually-install)時間。

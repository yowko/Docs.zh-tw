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
# <a name="fedora-32-package-manager---install-net-core"></a><span data-ttu-id="73834-103">Fedora 32 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="73834-103">Fedora 32 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="73834-104">本文說明如何使用套件管理員在 Fedora 32 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="73834-104">This article describes how to use a package manager to install .NET Core on Fedora 32.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

<span data-ttu-id="73834-105">從 Fedora 32 開始，.NET Core 3.1 可在 Fedora 的預設封裝存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="73834-105">Starting with Fedora 32, .NET Core 3.1 is available in the default package repositories in Fedora.</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="73834-106">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="73834-106">Install the .NET Core SDK</span></span>

<span data-ttu-id="73834-107">安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="73834-107">Install the .NET Core SDK.</span></span> <span data-ttu-id="73834-108">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="73834-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="73834-109">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="73834-109">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="73834-110">安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="73834-110">Install the ASP.NET runtime.</span></span> <span data-ttu-id="73834-111">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="73834-111">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="73834-112">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="73834-112">Install the .NET Core runtime</span></span>

<span data-ttu-id="73834-113">安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="73834-113">Install the .NET Core runtime.</span></span> <span data-ttu-id="73834-114">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="73834-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="73834-115">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="73834-115">How to install other versions</span></span>

<span data-ttu-id="73834-116">若要安裝其他版本的 .NET Core，請手動安裝[.NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install)或[.net core 運行](runtime.md?pivots=os-linux#download-and-manually-install)時間。</span><span class="sxs-lookup"><span data-stu-id="73834-116">To install other versions of .NET Core, manually install [the .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) or [the .NET Core Runtime](runtime.md?pivots=os-linux#download-and-manually-install).</span></span>

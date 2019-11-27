---
title: 在 Debian 9 上安裝 .NET Core-套件管理員-.NET Core
description: 使用套件管理員，在 Debian 9 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: e0aed17a7283a1d032aa8d6da723bc5b115d91a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451035"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="95042-103">Debian 9 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="95042-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="95042-104">本文說明如何使用套件管理員，在 Debian 9 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="95042-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span> <span data-ttu-id="95042-105">如果您要安裝執行時間，我們建議您安裝[ASP.NET Core 運行](#install-the-aspnet-core-runtime)時間，因為它同時包含 .net Core 和 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="95042-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="95042-106">註冊 Microsoft 金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="95042-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="95042-107">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="95042-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="95042-108">註冊 Microsoft 金鑰</span><span class="sxs-lookup"><span data-stu-id="95042-108">Register the Microsoft key</span></span>
- <span data-ttu-id="95042-109">註冊產品存放庫</span><span class="sxs-lookup"><span data-stu-id="95042-109">register the product repository</span></span>
- <span data-ttu-id="95042-110">安裝必要的相依性</span><span class="sxs-lookup"><span data-stu-id="95042-110">Install required dependencies</span></span>

<span data-ttu-id="95042-111">這只需要針對每部機器執行一次。</span><span class="sxs-lookup"><span data-stu-id="95042-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="95042-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="95042-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="95042-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="95042-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="95042-114">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="95042-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="95042-115">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="95042-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="95042-116">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="95042-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="95042-117">更新可供安裝的產品，然後安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="95042-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="95042-118">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="95042-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="95042-119">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="95042-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="95042-120">更新可供安裝的產品，然後安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="95042-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="95042-121">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="95042-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="95042-122">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="95042-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

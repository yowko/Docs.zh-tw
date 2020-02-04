---
title: 在 Ubuntu 18.04 套件管理員上安裝 .NET Core-.NET Core
description: 使用套件管理員在 Ubuntu 18.04 上安裝 .NET Core SDK 和執行階段。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: e36116d357b8fcd5ced328a574e12c558dd9e2f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920696"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="199fc-103">Ubuntu 18.04 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="199fc-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="199fc-104">本文說明如何使用套件管理員在 Ubuntu 18.04 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="199fc-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span> <span data-ttu-id="199fc-105">如果您要安裝執行階段，我們建議您安裝 [ASP.NET Core runtime](#install-the-aspnet-core-runtime)，因為它同時包含 .net Core 和 ASP.NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="199fc-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="199fc-106">註冊 Microsoft 金鑰和總結</span><span class="sxs-lookup"><span data-stu-id="199fc-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="199fc-107">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="199fc-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="199fc-108">註冊 Microsoft 金鑰。</span><span class="sxs-lookup"><span data-stu-id="199fc-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="199fc-109">註冊產品存放庫。</span><span class="sxs-lookup"><span data-stu-id="199fc-109">Register the product repository.</span></span>
- <span data-ttu-id="199fc-110">安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="199fc-110">Install required dependencies.</span></span>

<span data-ttu-id="199fc-111">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="199fc-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="199fc-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="199fc-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="199fc-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="199fc-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="199fc-114">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="199fc-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="199fc-115">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="199fc-115">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="199fc-116">如果您收到類似 [**找不到封裝 dotnet-sdk-3.1**] 的錯誤訊息，請參閱[疑難排解套件管理員](#troubleshoot-the-package-manager)一節。</span><span class="sxs-lookup"><span data-stu-id="199fc-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="199fc-117">安裝 ASP.NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="199fc-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="199fc-118">更新可供安裝的產品，然後安裝 ASP.NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="199fc-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="199fc-119">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="199fc-119">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="199fc-120">如果您收到類似「找不到套件 aspnetcore-runtime-3.1」的錯誤訊息，請參閱**針對套件管理員進行疑難排解**一節。</span><span class="sxs-lookup"><span data-stu-id="199fc-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="199fc-121">安裝 .NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="199fc-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="199fc-122">更新可供安裝的產品，然後安裝 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="199fc-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="199fc-123">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="199fc-123">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="199fc-124">如果您收到類似「找不到套件 dotnet-runtime-3.1」的錯誤訊息，請參閱**針對套件管理員進行疑難排解**一節。</span><span class="sxs-lookup"><span data-stu-id="199fc-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="199fc-125">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="199fc-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="199fc-126">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="199fc-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="199fc-127">本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="199fc-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="199fc-128">找不到</span><span class="sxs-lookup"><span data-stu-id="199fc-128">Unable to locate</span></span>

<span data-ttu-id="199fc-129">如果您收到類似「**找不到封裝 {.Net Core 封裝}** 」的錯誤訊息，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="199fc-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="199fc-130">如果無法解決問題，您可以使用下列命令來執行手動安裝。</span><span class="sxs-lookup"><span data-stu-id="199fc-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="199fc-131">無法提取</span><span class="sxs-lookup"><span data-stu-id="199fc-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

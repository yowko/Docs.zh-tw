---
title: 在 Ubuntu 18.04 套件管理員上安裝 .NET 內核 - .NET Core
description: 使用包管理器在 Ubuntu 18.04 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: ea01c324335c5e0eb120b72fd6384df640f0997e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645616"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="e1ba1-103">Ubuntu 18.04 套件管理員 - 安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="e1ba1-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e1ba1-104">本文介紹如何使用包管理器在 Ubuntu 18.04 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="e1ba1-105">新增 Microsoft 儲存函式庫金鑰和來源</span><span class="sxs-lookup"><span data-stu-id="e1ba1-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="e1ba1-106">在安裝 .NET 之前,您需要:</span><span class="sxs-lookup"><span data-stu-id="e1ba1-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e1ba1-107">將 Microsoft 包簽署金鑰添加到受信任金鑰清單中。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="e1ba1-108">將儲存庫添加到包管理員。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="e1ba1-109">安裝所需的依賴項。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-109">Install required dependencies.</span></span>

<span data-ttu-id="e1ba1-110">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e1ba1-111">打開終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e1ba1-112">安裝 .NET 核心 SDK</span><span class="sxs-lookup"><span data-stu-id="e1ba1-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="e1ba1-113">更新可供安裝的產品,然後安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e1ba1-114">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-114">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="e1ba1-115">如果收到類似於**找不到包 dotnet-sdk-3.1**的錯誤訊息,請參閱[對套件管理員部分進行故障排除](#troubleshoot-the-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e1ba1-116">安裝ASP.NET核心執行時</span><span class="sxs-lookup"><span data-stu-id="e1ba1-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e1ba1-117">更新可用於安裝的產品,然後安裝ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="e1ba1-118">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-118">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="e1ba1-119">如果收到類似於**無法找到包 aspnetcore-運行時-3.1**的錯誤消息,請參閱[「包管理器疑難解答](#troubleshoot-the-package-manager)」部分。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e1ba1-120">安裝 .NET 核心執行時</span><span class="sxs-lookup"><span data-stu-id="e1ba1-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="e1ba1-121">更新可用於安裝的產品,然後安裝 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e1ba1-122">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-122">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="e1ba1-123">如果收到類似於**找不到包 dotnet-執行時-3.1**的錯誤訊息,請參閱[套件管理器部分的故障排除](#troubleshoot-the-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e1ba1-124">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="e1ba1-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="e1ba1-125">排除套件管理員故障</span><span class="sxs-lookup"><span data-stu-id="e1ba1-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="e1ba1-126">本節提供有關在使用包管理器安裝 .NET Core 時可能得到的常見錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="e1ba1-127">無法定位</span><span class="sxs-lookup"><span data-stu-id="e1ba1-127">Unable to locate</span></span>

<span data-ttu-id="e1ba1-128">如果收到類似於**無法找到包 [.NET Core 包]** 的錯誤消息,請運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="e1ba1-129">如果這不起作用,則可以使用以下命令運行手動安裝。</span><span class="sxs-lookup"><span data-stu-id="e1ba1-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="e1ba1-130">無法擷取</span><span class="sxs-lookup"><span data-stu-id="e1ba1-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

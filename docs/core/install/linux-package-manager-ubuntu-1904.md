---
title: 在 Ubuntu 19.04 套裝軟體管理器上安裝 .NET 內核 - .NET Core
description: 使用包管理器在 Ubuntu 19.04 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: c7b30d2760a0a83a0fdd7ff5fa35b2f3d490494f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920671"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="02e1f-103">Ubuntu 19.04 套裝軟體管理器 - 安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="02e1f-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="02e1f-104">本文介紹如何使用包管理器在 Ubuntu 19.04 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="02e1f-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span> <span data-ttu-id="02e1f-105">如果要安裝運行時，我們建議您安裝[ASP.NET核心運行時](#install-the-aspnet-core-runtime)，因為它包括 .NET Core 和 ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="02e1f-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="02e1f-106">註冊 Microsoft 金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="02e1f-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="02e1f-107">在安裝 .NET 之前，您需要：</span><span class="sxs-lookup"><span data-stu-id="02e1f-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="02e1f-108">註冊微軟金鑰。</span><span class="sxs-lookup"><span data-stu-id="02e1f-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="02e1f-109">註冊產品存儲庫。</span><span class="sxs-lookup"><span data-stu-id="02e1f-109">Register the product repository.</span></span>
- <span data-ttu-id="02e1f-110">安裝所需的依賴項。</span><span class="sxs-lookup"><span data-stu-id="02e1f-110">Install required dependencies.</span></span>

<span data-ttu-id="02e1f-111">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="02e1f-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="02e1f-112">打開終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="02e1f-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="02e1f-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="02e1f-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="02e1f-114">更新可供安裝的產品，然後安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="02e1f-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="02e1f-115">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="02e1f-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="02e1f-116">如果收到類似于**找不到包 dotnet-sdk-3.1**的錯誤訊息，請參閱[對包管理器部分進行故障排除](#troubleshoot-the-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="02e1f-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="02e1f-117">安裝ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="02e1f-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="02e1f-118">更新可用於安裝的產品，然後安裝ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="02e1f-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="02e1f-119">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="02e1f-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="02e1f-120">如果收到類似于**無法找到包 aspnetcore-運行時-3.1**的錯誤訊息，請參閱["包管理器疑難排解](#troubleshoot-the-package-manager)"部分。</span><span class="sxs-lookup"><span data-stu-id="02e1f-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="02e1f-121">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="02e1f-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="02e1f-122">更新可用於安裝的產品，然後安裝 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="02e1f-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="02e1f-123">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="02e1f-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="02e1f-124">如果收到類似于**找不到包 dotnet-運行時-3.1**的錯誤訊息，請參閱[包管理器部分的故障排除](#troubleshoot-the-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="02e1f-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="02e1f-125">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="02e1f-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="02e1f-126">排除包管理器故障</span><span class="sxs-lookup"><span data-stu-id="02e1f-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="02e1f-127">本節提供有關在使用包管理器安裝 .NET Core 時可能得到的常見錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="02e1f-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="02e1f-128">無法定位</span><span class="sxs-lookup"><span data-stu-id="02e1f-128">Unable to locate</span></span>

<span data-ttu-id="02e1f-129">如果收到類似于**無法找到包 [.NET Core 包]** 的錯誤訊息，請運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="02e1f-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="02e1f-130">如果這不起作用，則可以使用以下命令運行手動安裝。</span><span class="sxs-lookup"><span data-stu-id="02e1f-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="02e1f-131">無法提取</span><span class="sxs-lookup"><span data-stu-id="02e1f-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

---
title: 在 SLES 12 上安裝 .NET 內核 - 包管理器 - .NET 內核
description: 使用包管理器在 SLES 12 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 8358107c682274fc2b75bf72689eaa4b168a86c5
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134224"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="7b3e3-103">SLES 12 套裝軟體管理器 - 安裝 .NET 內核</span><span class="sxs-lookup"><span data-stu-id="7b3e3-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7b3e3-104">本文介紹如何使用包管理器在 SLES 12 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="7b3e3-105">註冊 Microsoft 金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="7b3e3-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="7b3e3-106">在安裝 .NET 之前，您需要：</span><span class="sxs-lookup"><span data-stu-id="7b3e3-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7b3e3-107">註冊微軟金鑰。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="7b3e3-108">註冊產品存儲庫。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-108">Register the product repository.</span></span>
- <span data-ttu-id="7b3e3-109">安裝所需的依賴項。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-109">Install required dependencies.</span></span>

<span data-ttu-id="7b3e3-110">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7b3e3-111">打開終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7b3e3-112">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7b3e3-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="7b3e3-113">更新可供安裝的產品，然後安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7b3e3-114">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7b3e3-115">安裝ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="7b3e3-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7b3e3-116">更新可供安裝的產品，然後安裝ASP.NET運行時。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="7b3e3-117">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7b3e3-118">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="7b3e3-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="7b3e3-119">更新可用於安裝的產品，然後安裝 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7b3e3-120">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7b3e3-121">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="7b3e3-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="7b3e3-122">排除包管理器故障</span><span class="sxs-lookup"><span data-stu-id="7b3e3-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="7b3e3-123">本節提供有關在使用包管理器安裝 .NET Core 時可能得到的常見錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="7b3e3-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="7b3e3-124">無法提取</span><span class="sxs-lookup"><span data-stu-id="7b3e3-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

---
title: 在 Fedora 31 - 封裝管理器上安裝 .NET 核心 - .NET 核心
description: 使用包管理器在 Fedora 31 上安裝 .NET 核心 SDK 和運行時。
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 28bda3676f99037e565080e1ff3f9d89a67d0d69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920775"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="fda14-103">Fedora 31 套裝軟體管理器 - 安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="fda14-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="fda14-104">本文介紹如何使用包管理器在 Fedora 31 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="fda14-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="fda14-105">如果要安裝運行時，我們建議您安裝[ASP.NET核心運行時](#install-the-aspnet-core-runtime)，因為它包括 .NET Core 和 ASP.NET核心運行時。</span><span class="sxs-lookup"><span data-stu-id="fda14-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="fda14-106">註冊 Microsoft 金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="fda14-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="fda14-107">在安裝 .NET 之前，您需要：</span><span class="sxs-lookup"><span data-stu-id="fda14-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="fda14-108">註冊微軟金鑰。</span><span class="sxs-lookup"><span data-stu-id="fda14-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="fda14-109">註冊產品存儲庫。</span><span class="sxs-lookup"><span data-stu-id="fda14-109">Register the product repository.</span></span>
- <span data-ttu-id="fda14-110">安裝所需的依賴項。</span><span class="sxs-lookup"><span data-stu-id="fda14-110">Install required dependencies.</span></span>

<span data-ttu-id="fda14-111">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="fda14-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="fda14-112">打開終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="fda14-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="fda14-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="fda14-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="fda14-114">更新可供安裝的產品，然後安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="fda14-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="fda14-115">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="fda14-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="fda14-116">安裝ASP.NET核心運行時</span><span class="sxs-lookup"><span data-stu-id="fda14-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="fda14-117">更新可供安裝的產品，然後安裝ASP.NET運行時。</span><span class="sxs-lookup"><span data-stu-id="fda14-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="fda14-118">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="fda14-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="fda14-119">安裝 .NET 核心運行時</span><span class="sxs-lookup"><span data-stu-id="fda14-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="fda14-120">更新可用於安裝的產品，然後安裝 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="fda14-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="fda14-121">在終端中，運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="fda14-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fda14-122">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="fda14-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="fda14-123">排除包管理器故障</span><span class="sxs-lookup"><span data-stu-id="fda14-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="fda14-124">本節提供有關在使用包管理器安裝 .NET Core 時可能得到的常見錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="fda14-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="fda14-125">無法提取</span><span class="sxs-lookup"><span data-stu-id="fda14-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

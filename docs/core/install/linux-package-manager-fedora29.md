---
title: 在 Fedora 29 - 封裝管理員上安裝 .NET 核心 - .NET 核心
description: 使用包管理員在 Fedora 29 上安裝 .NET 核心 SDK 和執行時。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1cbe38f4f104a8e178d8bcfd1fa1bd6d7645261
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645300"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="804b9-103">Fedora 29 套件管理員 -安裝 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="804b9-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="804b9-104">本文介紹如何使用包管理器在 Fedora 29 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="804b9-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="804b9-105">新增 Microsoft 儲存函式庫金鑰和來源</span><span class="sxs-lookup"><span data-stu-id="804b9-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="804b9-106">在安裝 .NET 之前,您需要:</span><span class="sxs-lookup"><span data-stu-id="804b9-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="804b9-107">將 Microsoft 包簽署金鑰添加到受信任金鑰清單中。</span><span class="sxs-lookup"><span data-stu-id="804b9-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="804b9-108">將儲存庫添加到包管理員。</span><span class="sxs-lookup"><span data-stu-id="804b9-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="804b9-109">安裝所需的依賴項。</span><span class="sxs-lookup"><span data-stu-id="804b9-109">Install required dependencies.</span></span>

<span data-ttu-id="804b9-110">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="804b9-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="804b9-111">打開終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="804b9-111">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="804b9-112">安裝 .NET 核心 SDK</span><span class="sxs-lookup"><span data-stu-id="804b9-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="804b9-113">更新可供安裝的產品,然後安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="804b9-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="804b9-114">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="804b9-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="804b9-115">安裝ASP.NET核心執行時</span><span class="sxs-lookup"><span data-stu-id="804b9-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="804b9-116">更新可供安裝的產品,然後安裝ASP.NET運行時。</span><span class="sxs-lookup"><span data-stu-id="804b9-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="804b9-117">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="804b9-117">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="804b9-118">安裝 .NET 核心執行時</span><span class="sxs-lookup"><span data-stu-id="804b9-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="804b9-119">更新可用於安裝的產品,然後安裝 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="804b9-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="804b9-120">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="804b9-120">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="804b9-121">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="804b9-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="804b9-122">排除套件管理員故障</span><span class="sxs-lookup"><span data-stu-id="804b9-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="804b9-123">本節提供有關在使用包管理器安裝 .NET Core 時可能得到的常見錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="804b9-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="804b9-124">無法擷取</span><span class="sxs-lookup"><span data-stu-id="804b9-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

---
title: 在 Debian 10 安裝 .NET 內核 - 套件管理員 - .NET 內核
description: 使用包管理員在 Debian 10 上安裝 .NET 核心 SDK 和執行時。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: a312496ed9a26783198cdd038db7ffa2bdc7381e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645283"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="c2a43-103">Debian 10 套件管理員 -安裝 .NET 內核</span><span class="sxs-lookup"><span data-stu-id="c2a43-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="c2a43-104">本文介紹如何使用包管理器在 Debian 10 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="c2a43-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="c2a43-105">新增 Microsoft 儲存函式庫金鑰和來源</span><span class="sxs-lookup"><span data-stu-id="c2a43-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="c2a43-106">在安裝 .NET 之前,您需要:</span><span class="sxs-lookup"><span data-stu-id="c2a43-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="c2a43-107">將 Microsoft 包簽署金鑰添加到受信任金鑰清單中。</span><span class="sxs-lookup"><span data-stu-id="c2a43-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="c2a43-108">將儲存庫添加到包管理員。</span><span class="sxs-lookup"><span data-stu-id="c2a43-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="c2a43-109">安裝所需的依賴項。</span><span class="sxs-lookup"><span data-stu-id="c2a43-109">Install required dependencies.</span></span>

<span data-ttu-id="c2a43-110">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="c2a43-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="c2a43-111">打開終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c2a43-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c2a43-112">安裝 .NET 核心 SDK</span><span class="sxs-lookup"><span data-stu-id="c2a43-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="c2a43-113">更新可供安裝的產品,然後安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="c2a43-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="c2a43-114">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c2a43-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c2a43-115">安裝ASP.NET核心執行時</span><span class="sxs-lookup"><span data-stu-id="c2a43-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="c2a43-116">更新可供安裝的產品,然後安裝ASP.NET運行時。</span><span class="sxs-lookup"><span data-stu-id="c2a43-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="c2a43-117">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c2a43-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c2a43-118">安裝 .NET 核心執行時</span><span class="sxs-lookup"><span data-stu-id="c2a43-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="c2a43-119">更新可用於安裝的產品,然後安裝 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="c2a43-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="c2a43-120">在終端中,運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c2a43-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c2a43-121">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="c2a43-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c2a43-122">排除套件管理員故障</span><span class="sxs-lookup"><span data-stu-id="c2a43-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="c2a43-123">本節提供有關在使用包管理器安裝 .NET Core 時可能得到的常見錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="c2a43-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="c2a43-124">無法擷取</span><span class="sxs-lookup"><span data-stu-id="c2a43-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

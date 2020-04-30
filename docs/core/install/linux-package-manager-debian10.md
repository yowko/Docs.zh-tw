---
title: 在 Debian 10 上安裝 .NET Core-套件管理員-.NET Core
description: 使用套件管理員，在 Debian 10 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 038f5579f99f700ce47dc67be2fd344f01cf800c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595609"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="fc92f-103">Debian 10 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc92f-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="fc92f-104">本文說明如何使用套件管理員，在 Debian 10 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="fc92f-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="fc92f-105">新增 Microsoft 存放庫金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="fc92f-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="fc92f-106">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="fc92f-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="fc92f-107">將 Microsoft 封裝簽署金鑰新增至受信任的金鑰清單。</span><span class="sxs-lookup"><span data-stu-id="fc92f-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="fc92f-108">將存放庫新增至套件管理員。</span><span class="sxs-lookup"><span data-stu-id="fc92f-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="fc92f-109">安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="fc92f-109">Install required dependencies.</span></span>

<span data-ttu-id="fc92f-110">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="fc92f-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="fc92f-111">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="fc92f-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="fc92f-112">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="fc92f-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="fc92f-113">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="fc92f-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="fc92f-114">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="fc92f-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="fc92f-115">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="fc92f-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="fc92f-116">更新可供安裝的產品，然後安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="fc92f-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="fc92f-117">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="fc92f-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="fc92f-118">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="fc92f-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="fc92f-119">更新可供安裝的產品，然後安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="fc92f-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="fc92f-120">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="fc92f-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fc92f-121">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="fc92f-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="fc92f-122">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="fc92f-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="fc92f-123">本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="fc92f-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="fc92f-124">無法提取</span><span class="sxs-lookup"><span data-stu-id="fc92f-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

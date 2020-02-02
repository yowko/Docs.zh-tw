---
title: 在 Debian 10 上安裝 .NET Core-套件管理員-.NET Core
description: 使用套件管理員，在 Debian 10 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 94bcb493536bdee71ba83053d9e671d529226ac3
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920839"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="28053-103">Debian 10 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="28053-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="28053-104">本文說明如何使用套件管理員，在 Debian 10 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="28053-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span> <span data-ttu-id="28053-105">如果您要安裝執行階段，我們建議您安裝 [ASP.NET Core runtime](#install-the-aspnet-core-runtime)，因為它同時包含 .net Core 和 ASP.NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="28053-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="28053-106">註冊 Microsoft 金鑰和總結</span><span class="sxs-lookup"><span data-stu-id="28053-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="28053-107">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="28053-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="28053-108">註冊 Microsoft 金鑰。</span><span class="sxs-lookup"><span data-stu-id="28053-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="28053-109">註冊產品存放庫。</span><span class="sxs-lookup"><span data-stu-id="28053-109">Register the product repository.</span></span>
- <span data-ttu-id="28053-110">安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="28053-110">Install required dependencies.</span></span>

<span data-ttu-id="28053-111">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="28053-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="28053-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="28053-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="28053-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="28053-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="28053-114">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="28053-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="28053-115">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="28053-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="28053-116">安裝 ASP.NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="28053-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="28053-117">更新可供安裝的產品，然後安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="28053-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="28053-118">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="28053-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="28053-119">安裝 .NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="28053-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="28053-120">更新可供安裝的產品，然後安裝 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="28053-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="28053-121">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="28053-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="28053-122">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="28053-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="28053-123">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="28053-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="28053-124">本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="28053-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="28053-125">無法提取</span><span class="sxs-lookup"><span data-stu-id="28053-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

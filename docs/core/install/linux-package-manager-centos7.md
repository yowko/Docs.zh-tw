---
title: 在 CentOS 7 上安裝 .NET Core-套件管理員-.NET Core
description: 使用封裝管理員，在 CentOS 7 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 62b07342197addaa5c7d962c08c4ff1d7121eff8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451077"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="76e0a-103">CentOS 7 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="76e0a-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="76e0a-104">本文說明如何使用套件管理員，在 CentOS 7 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="76e0a-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="76e0a-105">如果您要安裝執行時間，我們建議您安裝[ASP.NET Core 運行](#install-the-aspnet-core-runtime)時間，因為它同時包含 .net Core 和 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="76e0a-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="76e0a-106">註冊 Microsoft 金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="76e0a-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="76e0a-107">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="76e0a-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="76e0a-108">註冊 Microsoft 金鑰</span><span class="sxs-lookup"><span data-stu-id="76e0a-108">Register the Microsoft key</span></span>
- <span data-ttu-id="76e0a-109">註冊產品存放庫</span><span class="sxs-lookup"><span data-stu-id="76e0a-109">register the product repository</span></span>
- <span data-ttu-id="76e0a-110">安裝必要的相依性</span><span class="sxs-lookup"><span data-stu-id="76e0a-110">Install required dependencies</span></span>

<span data-ttu-id="76e0a-111">這只需要針對每部機器執行一次。</span><span class="sxs-lookup"><span data-stu-id="76e0a-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="76e0a-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="76e0a-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="76e0a-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="76e0a-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="76e0a-114">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="76e0a-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="76e0a-115">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="76e0a-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="76e0a-116">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="76e0a-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="76e0a-117">更新可供安裝的產品，然後安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="76e0a-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="76e0a-118">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="76e0a-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="76e0a-119">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="76e0a-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="76e0a-120">更新可供安裝的產品，然後安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="76e0a-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="76e0a-121">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="76e0a-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="76e0a-122">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="76e0a-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

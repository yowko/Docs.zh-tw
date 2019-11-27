---
title: 在 SLES 15-套件管理員上安裝 .NET Core-.NET Core
description: 使用封裝管理員，在 SLES 15 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 8e773dbc63ad8c969ae5c85c05ba9ed0c67311ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450965"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="ea522-103">SLES 15 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="ea522-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="ea522-104">本文說明如何使用套件管理員，在 SLES 15 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="ea522-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="ea522-105">如果您要安裝執行時間，我們建議您安裝[ASP.NET Core 運行](#install-the-aspnet-core-runtime)時間，因為它同時包含 .net Core 和 ASP.NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="ea522-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="ea522-106">註冊 Microsoft 金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="ea522-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="ea522-107">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="ea522-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="ea522-108">註冊 Microsoft 金鑰</span><span class="sxs-lookup"><span data-stu-id="ea522-108">Register the Microsoft key</span></span>
- <span data-ttu-id="ea522-109">註冊產品存放庫</span><span class="sxs-lookup"><span data-stu-id="ea522-109">register the product repository</span></span>
- <span data-ttu-id="ea522-110">安裝必要的相依性</span><span class="sxs-lookup"><span data-stu-id="ea522-110">Install required dependencies</span></span>

<span data-ttu-id="ea522-111">這只需要針對每部機器執行一次。</span><span class="sxs-lookup"><span data-stu-id="ea522-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="ea522-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="ea522-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="ea522-113">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="ea522-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="ea522-114">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="ea522-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="ea522-115">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="ea522-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="ea522-116">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="ea522-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="ea522-117">更新可供安裝的產品，然後安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="ea522-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="ea522-118">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="ea522-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="ea522-119">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="ea522-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="ea522-120">更新可供安裝的產品，然後安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="ea522-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="ea522-121">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="ea522-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ea522-122">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="ea522-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

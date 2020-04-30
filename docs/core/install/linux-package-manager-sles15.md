---
title: 在 SLES 15-套件管理員上安裝 .NET Core-.NET Core
description: 使用封裝管理員，在 SLES 15 上安裝 .NET Core SDK 和執行時間。
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: be5a21db8c3942bfe8827dfbce41bcf88aec342a
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595602"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="a2917-103">SLES 15 套件管理員-安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="a2917-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="a2917-104">本文說明如何使用套件管理員，在 SLES 15 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="a2917-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="a2917-105">新增 Microsoft 存放庫金鑰和摘要</span><span class="sxs-lookup"><span data-stu-id="a2917-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="a2917-106">安裝 .NET 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="a2917-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="a2917-107">將 Microsoft 封裝簽署金鑰新增至受信任的金鑰清單。</span><span class="sxs-lookup"><span data-stu-id="a2917-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="a2917-108">將存放庫新增至套件管理員。</span><span class="sxs-lookup"><span data-stu-id="a2917-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="a2917-109">安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="a2917-109">Install required dependencies.</span></span>

<span data-ttu-id="a2917-110">每部電腦只需要執行這項作業一次。</span><span class="sxs-lookup"><span data-stu-id="a2917-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="a2917-111">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a2917-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="a2917-112">目前，SLES 15 Microsoft 存放庫安裝套件會將*Microsoft*存放庫檔案安裝至錯誤的目錄，以防止 zypper 尋找 .net Core 套件。</span><span class="sxs-lookup"><span data-stu-id="a2917-112">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="a2917-113">若要修正此問題，請在正確的目錄中建立符號連結。</span><span class="sxs-lookup"><span data-stu-id="a2917-113">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="a2917-114">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a2917-114">Install the .NET Core SDK</span></span>

<span data-ttu-id="a2917-115">更新可供安裝的產品，然後安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="a2917-115">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="a2917-116">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a2917-116">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="a2917-117">安裝 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="a2917-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="a2917-118">更新可供安裝的產品，然後安裝 ASP.NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="a2917-118">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="a2917-119">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a2917-119">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="a2917-120">安裝 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="a2917-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="a2917-121">更新可供安裝的產品，然後安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="a2917-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="a2917-122">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a2917-122">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a2917-123">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="a2917-123">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a2917-124">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a2917-124">Troubleshoot the package manager</span></span>

<span data-ttu-id="a2917-125">本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="a2917-125">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="a2917-126">無法提取</span><span class="sxs-lookup"><span data-stu-id="a2917-126">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]

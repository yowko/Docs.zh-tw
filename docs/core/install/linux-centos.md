---
title: 在 CentOS 上安裝 .NET Core-.NET Core
description: 示範在 CentOS 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7937502067e1717fd7f5c973c64ad33ae2a443a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538614"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-centos"></a><span data-ttu-id="f42ac-103">在 CentOS 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="f42ac-103">Install .NET Core SDK or .NET Core Runtime on CentOS</span></span>

<span data-ttu-id="f42ac-104">CentOS 支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f42ac-104">.NET Core is supported on CentOS.</span></span> <span data-ttu-id="f42ac-105">本文說明如何在 CentOS 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f42ac-105">This article describes how to install .NET Core on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="f42ac-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="f42ac-106">Supported distributions</span></span>

<span data-ttu-id="f42ac-107">下表是 CentOS 7 和 CentOS 8 上目前支援的 .NET Core 版本清單。</span><span class="sxs-lookup"><span data-stu-id="f42ac-107">The following table is a list of currently supported .NET Core releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="f42ac-108">在 [.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 CentOS 版本之前，會持續支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="f42ac-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="f42ac-109">✔️表示仍支援 CentOS 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="f42ac-109">A ✔️ indicates that the version of CentOS or .NET Core is still supported.</span></span>
- <span data-ttu-id="f42ac-110">❌指出該 CentOS 版本不支援 CentOS 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="f42ac-110">A ❌ indicates that the version of CentOS or .NET Core isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="f42ac-111">當版本的 CentOS 和 .NET Core 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="f42ac-111">When both a version of CentOS and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="f42ac-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="f42ac-112">CentOS</span></span>                   | <span data-ttu-id="f42ac-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f42ac-113">.NET Core 2.1</span></span> | <span data-ttu-id="f42ac-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f42ac-114">.NET Core 3.1</span></span> | <span data-ttu-id="f42ac-115">.NET 5 Preview (僅限手動安裝) </span><span class="sxs-lookup"><span data-stu-id="f42ac-115">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="f42ac-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="f42ac-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="f42ac-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="f42ac-117">✔️ 2.1</span></span>        | <span data-ttu-id="f42ac-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="f42ac-118">✔️ 3.1</span></span>        | <span data-ttu-id="f42ac-119">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="f42ac-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="f42ac-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="f42ac-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="f42ac-121">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="f42ac-121">✔️ 2.1</span></span>        | <span data-ttu-id="f42ac-122">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="f42ac-122">✔️ 3.1</span></span>        | <span data-ttu-id="f42ac-123">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="f42ac-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="f42ac-124">不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="f42ac-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="f42ac-125">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="f42ac-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f42ac-126">3.0</span><span class="sxs-lookup"><span data-stu-id="f42ac-126">3.0</span></span>
- <span data-ttu-id="f42ac-127">2.2</span><span class="sxs-lookup"><span data-stu-id="f42ac-127">2.2</span></span>
- <span data-ttu-id="f42ac-128">2.0</span><span class="sxs-lookup"><span data-stu-id="f42ac-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f42ac-129">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="f42ac-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="f42ac-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="f42ac-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="f42ac-131">CentOS 8 的預設封裝存放庫中有提供 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="f42ac-131">.NET Core 3.1 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="f42ac-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="f42ac-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-31](includes/linux-install-31-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="f42ac-133">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="f42ac-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="f42ac-134">本節提供使用套件管理員安裝 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f42ac-134">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="f42ac-135">找不到套件</span><span class="sxs-lookup"><span data-stu-id="f42ac-135">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="f42ac-136">無法提取</span><span class="sxs-lookup"><span data-stu-id="f42ac-136">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="f42ac-137">單元</span><span class="sxs-lookup"><span data-stu-id="f42ac-137">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="f42ac-138">相依性</span><span class="sxs-lookup"><span data-stu-id="f42ac-138">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="f42ac-139">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="f42ac-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="f42ac-140">手動安裝</span><span class="sxs-lookup"><span data-stu-id="f42ac-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="f42ac-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f42ac-141">Next steps</span></span>

- [<span data-ttu-id="f42ac-142">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="f42ac-142">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

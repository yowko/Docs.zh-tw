---
title: 在 CentOS 上安裝 .NET-.NET
description: 示範在 CentOS 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b2ed62d024c6f0d78a4ec64693f1dafeabd8f47b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594628"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="457db-103">在 CentOS 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="457db-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="457db-104">CentOS 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="457db-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="457db-105">本文說明如何在 CentOS 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="457db-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="457db-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="457db-106">Supported distributions</span></span>

<span data-ttu-id="457db-107">下表是 CentOS 7 和 CentOS 8 上目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="457db-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="457db-108">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 CentOS 版本，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="457db-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="457db-109">✔️表示仍支援 CentOS 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="457db-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="457db-110">❌指出該 CentOS 版本不支援 CentOS 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="457db-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="457db-111">當版本的 CentOS 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="457db-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="457db-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="457db-112">CentOS</span></span>                   | <span data-ttu-id="457db-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="457db-113">.NET Core 2.1</span></span> | <span data-ttu-id="457db-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="457db-114">.NET Core 3.1</span></span> | <span data-ttu-id="457db-115">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="457db-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="457db-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="457db-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="457db-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="457db-117">✔️ 2.1</span></span>        | <span data-ttu-id="457db-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="457db-118">✔️ 3.1</span></span>        | <span data-ttu-id="457db-119">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="457db-119">✔️ 5.0</span></span> |
| <span data-ttu-id="457db-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="457db-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="457db-121">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="457db-121">✔️ 2.1</span></span>        | <span data-ttu-id="457db-122">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="457db-122">✔️ 3.1</span></span>        | <span data-ttu-id="457db-123">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="457db-123">✔️ 5.0</span></span> |

<span data-ttu-id="457db-124">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="457db-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="457db-125">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="457db-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="457db-126">3.0</span><span class="sxs-lookup"><span data-stu-id="457db-126">3.0</span></span>
- <span data-ttu-id="457db-127">2.2</span><span class="sxs-lookup"><span data-stu-id="457db-127">2.2</span></span>
- <span data-ttu-id="457db-128">2.0</span><span class="sxs-lookup"><span data-stu-id="457db-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="457db-129">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="457db-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="457db-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="457db-130">CentOS 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="457db-131">預設套件存放庫中尚無法使用 .NET 5.0，但 .NET Core 3.1 為。</span><span class="sxs-lookup"><span data-stu-id="457db-131">.NET 5.0 isn't yet available in the default package repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="457db-132">若要安裝 .NET Core 3.1，請使用 `dnf install` 命令搭配適當的封裝，例如 `aspnetcore-runtime-3.1` 或 `dotnet-sdk-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="457db-132">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="457db-133">下列指示適用于 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="457db-133">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/8/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="457db-134">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="457db-134">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="457db-135">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="457db-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="457db-136">本節提供使用套件管理員安裝 .NET 時可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="457db-136">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="457db-137">找不到套件</span><span class="sxs-lookup"><span data-stu-id="457db-137">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="457db-138">無法提取</span><span class="sxs-lookup"><span data-stu-id="457db-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="457db-139">單元</span><span class="sxs-lookup"><span data-stu-id="457db-139">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="457db-140">相依性</span><span class="sxs-lookup"><span data-stu-id="457db-140">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="457db-141">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="457db-141">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="457db-142">手動安裝</span><span class="sxs-lookup"><span data-stu-id="457db-142">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="457db-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="457db-143">Next steps</span></span>

- [<span data-ttu-id="457db-144">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="457db-144">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

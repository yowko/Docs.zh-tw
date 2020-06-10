---
title: 在 SLES-.NET Core 上安裝 .NET Core
description: 示範在 SLES 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: b2eab6a0305d492e37e1b33d02be43ca41d42b6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603031"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="2ac00-103">在 SLES 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="2ac00-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="2ac00-104">SLES 支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2ac00-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="2ac00-105">本文說明如何在 SLES 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2ac00-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="2ac00-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="2ac00-106">Supported distributions</span></span>

<span data-ttu-id="2ac00-107">下表是 SLES 12 SP2 和 SLES 15 上目前支援的 .NET Core 版本清單。</span><span class="sxs-lookup"><span data-stu-id="2ac00-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="2ac00-108">在[.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或不再支援 SLES 版本之前，會持續支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="2ac00-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="2ac00-109">✔️表示仍然支援 SLES 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="2ac00-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="2ac00-110">A ❌ 表示該 sles 版本不支援 sles 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="2ac00-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="2ac00-111">當 SLES 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="2ac00-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="2ac00-112">SLES</span><span class="sxs-lookup"><span data-stu-id="2ac00-112">SLES</span></span>                   | <span data-ttu-id="2ac00-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ac00-113">.NET Core 2.1</span></span> | <span data-ttu-id="2ac00-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2ac00-114">.NET Core 3.1</span></span> | <span data-ttu-id="2ac00-115">.NET 5 Preview （僅限手動安裝）</span><span class="sxs-lookup"><span data-stu-id="2ac00-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="2ac00-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="2ac00-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="2ac00-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="2ac00-117">✔️ 2.1</span></span>        | <span data-ttu-id="2ac00-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="2ac00-118">✔️ 3.1</span></span>        | <span data-ttu-id="2ac00-119">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="2ac00-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="2ac00-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="2ac00-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="2ac00-121">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="2ac00-121">✔️ 2.1</span></span>        | <span data-ttu-id="2ac00-122">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="2ac00-122">✔️ 3.1</span></span>        | <span data-ttu-id="2ac00-123">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="2ac00-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="2ac00-124">已不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="2ac00-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="2ac00-125">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="2ac00-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="2ac00-126">3.0</span><span class="sxs-lookup"><span data-stu-id="2ac00-126">3.0</span></span>
- <span data-ttu-id="2ac00-127">2.2</span><span class="sxs-lookup"><span data-stu-id="2ac00-127">2.2</span></span>
- <span data-ttu-id="2ac00-128">2.0</span><span class="sxs-lookup"><span data-stu-id="2ac00-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2ac00-129">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="2ac00-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="2ac00-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="2ac00-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="2ac00-131">目前，SLES 15 Microsoft 存放庫安裝套件會將*Microsoft*存放庫檔案安裝至錯誤的目錄，以防止 zypper 尋找 .net Core 套件。</span><span class="sxs-lookup"><span data-stu-id="2ac00-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="2ac00-132">若要修正此問題，請在正確的目錄中建立符號連結。</span><span class="sxs-lookup"><span data-stu-id="2ac00-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="2ac00-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="2ac00-133">SLES 12 ✔️</span></span>

<span data-ttu-id="2ac00-134">.NET Core 需要使用 SP2 作為 SLES 12 系列的最小值。</span><span class="sxs-lookup"><span data-stu-id="2ac00-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="2ac00-135">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="2ac00-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="2ac00-136">本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="2ac00-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="2ac00-137">無法提取</span><span class="sxs-lookup"><span data-stu-id="2ac00-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="2ac00-138">抓取</span><span class="sxs-lookup"><span data-stu-id="2ac00-138">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="2ac00-139">相依性</span><span class="sxs-lookup"><span data-stu-id="2ac00-139">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="2ac00-140">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="2ac00-140">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="2ac00-141">手動安裝</span><span class="sxs-lookup"><span data-stu-id="2ac00-141">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="2ac00-142">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2ac00-142">Next steps</span></span>

- [<span data-ttu-id="2ac00-143">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2ac00-143">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

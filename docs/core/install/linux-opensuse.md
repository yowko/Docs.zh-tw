---
title: 在 openSUSE 上安裝 .NET Core-.NET Core
description: 示範在 openSUSE 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 3a2ff1ca1519428f42c88048dde22aa11baaaa01
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324746"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="44888-103">在 openSUSE 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="44888-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="44888-104">OpenSUSE 上支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="44888-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="44888-105">本文說明如何在 openSUSE 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="44888-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="44888-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="44888-106">Supported distributions</span></span>

<span data-ttu-id="44888-107">下表是 openSUSE 15 上目前支援的 .NET Core 版本清單。</span><span class="sxs-lookup"><span data-stu-id="44888-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="44888-108">在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或不再支援 openSUSE 版本之前，這些版本都會持續受到支援。</span><span class="sxs-lookup"><span data-stu-id="44888-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="44888-109">✔️表示仍然支援 openSUSE 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="44888-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="44888-110">A ❌ 表示該 openSUSE 版本不支援 openSUSE 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="44888-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="44888-111">當 openSUSE 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="44888-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="44888-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="44888-112">openSUSE</span></span>                   | <span data-ttu-id="44888-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="44888-113">.NET Core 2.1</span></span> | <span data-ttu-id="44888-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="44888-114">.NET Core 3.1</span></span> | <span data-ttu-id="44888-115">.NET 5 Preview （僅限手動安裝）</span><span class="sxs-lookup"><span data-stu-id="44888-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="44888-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="44888-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="44888-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="44888-117">✔️ 2.1</span></span>        | <span data-ttu-id="44888-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="44888-118">✔️ 3.1</span></span>        | <span data-ttu-id="44888-119">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="44888-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="44888-120">已不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="44888-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="44888-121">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="44888-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="44888-122">3.0</span><span class="sxs-lookup"><span data-stu-id="44888-122">3.0</span></span>
- <span data-ttu-id="44888-123">2.2</span><span class="sxs-lookup"><span data-stu-id="44888-123">2.2</span></span>
- <span data-ttu-id="44888-124">2.0</span><span class="sxs-lookup"><span data-stu-id="44888-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="44888-125">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="44888-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="44888-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="44888-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="44888-127">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="44888-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="44888-128">本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="44888-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="44888-129">無法提取</span><span class="sxs-lookup"><span data-stu-id="44888-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="44888-130">抓取</span><span class="sxs-lookup"><span data-stu-id="44888-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="44888-131">相依性</span><span class="sxs-lookup"><span data-stu-id="44888-131">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="44888-132">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="44888-132">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="44888-133">手動安裝</span><span class="sxs-lookup"><span data-stu-id="44888-133">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="44888-134">後續步驟</span><span class="sxs-lookup"><span data-stu-id="44888-134">Next steps</span></span>

- [<span data-ttu-id="44888-135">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="44888-135">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

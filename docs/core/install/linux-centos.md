---
title: 在 CentOS 上安裝 .NET-.NET
description: 示範在 CentOS 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7e73f90a1f1f7e11e592b1b074f243c9f5b32ced
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970859"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="a68a8-103">在 CentOS 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="a68a8-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="a68a8-104">CentOS 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="a68a8-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="a68a8-105">本文說明如何在 CentOS 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="a68a8-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="a68a8-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="a68a8-106">Supported distributions</span></span>

<span data-ttu-id="a68a8-107">下表是 CentOS 7 和 CentOS 8 上目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="a68a8-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="a68a8-108">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 CentOS 版本，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="a68a8-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="a68a8-109">✔️表示仍支援 CentOS 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="a68a8-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="a68a8-110">❌指出該 CentOS 版本不支援 CentOS 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="a68a8-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="a68a8-111">當版本的 CentOS 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="a68a8-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="a68a8-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="a68a8-112">CentOS</span></span>                   | <span data-ttu-id="a68a8-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a68a8-113">.NET Core 2.1</span></span> | <span data-ttu-id="a68a8-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a68a8-114">.NET Core 3.1</span></span> | <span data-ttu-id="a68a8-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a68a8-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="a68a8-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="a68a8-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="a68a8-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="a68a8-117">✔️ 2.1</span></span>        | <span data-ttu-id="a68a8-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="a68a8-118">✔️ 3.1</span></span>        | <span data-ttu-id="a68a8-119">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="a68a8-119">✔️ 5.0</span></span> |
| <span data-ttu-id="a68a8-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="a68a8-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="a68a8-121">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="a68a8-121">✔️ 2.1</span></span>        | <span data-ttu-id="a68a8-122">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="a68a8-122">✔️ 3.1</span></span>        | <span data-ttu-id="a68a8-123">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="a68a8-123">✔️ 5.0</span></span> |

<span data-ttu-id="a68a8-124">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="a68a8-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="a68a8-125">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="a68a8-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="a68a8-126">3.0</span><span class="sxs-lookup"><span data-stu-id="a68a8-126">3.0</span></span>
- <span data-ttu-id="a68a8-127">2.2</span><span class="sxs-lookup"><span data-stu-id="a68a8-127">2.2</span></span>
- <span data-ttu-id="a68a8-128">2.0</span><span class="sxs-lookup"><span data-stu-id="a68a8-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="remove-preview-versions"></a><span data-ttu-id="a68a8-129">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="a68a8-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="centos-8-"></a><span data-ttu-id="a68a8-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="a68a8-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="a68a8-131">CentOS 8 的預設封裝存放庫中有提供 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="a68a8-131">.NET 5.0 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="a68a8-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="a68a8-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a68a8-133">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="a68a8-133">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a68a8-134">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a68a8-134">Troubleshoot the package manager</span></span>

<span data-ttu-id="a68a8-135">本節提供使用套件管理員安裝 .NET 時可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a68a8-135">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="a68a8-136">找不到套件</span><span class="sxs-lookup"><span data-stu-id="a68a8-136">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="a68a8-137">無法提取</span><span class="sxs-lookup"><span data-stu-id="a68a8-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="a68a8-138">相依性</span><span class="sxs-lookup"><span data-stu-id="a68a8-138">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="next-steps"></a><span data-ttu-id="a68a8-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a68a8-139">Next steps</span></span>

- [<span data-ttu-id="a68a8-140">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="a68a8-140">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="a68a8-141">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a68a8-141">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)

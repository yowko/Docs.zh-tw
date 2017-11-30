---
title: "在 Windows 10 上安裝 .NET Framework"
description: "了解如何在 Windows 10 或 Windows Server 2016 上安裝.NET Framework。"
author: rlander
ms.author: mairaw
keywords: ".NET Framework, 安裝"
ms.date: 11/17/2017
ms.topic: article
ms.custom: updateeachrelease
ms.prod: .net-framework
ms.openlocfilehash: d7f8dd4c6ee9f7eeda389a955f806a5765876ea7
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a><span data-ttu-id="0f63e-104">在 Windows 10 和 Windows Server 2016 上安裝.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f63e-104">Install the .NET Framework on Windows 10 and Windows Server 2016</span></span>

<span data-ttu-id="0f63e-105">.NET Framework 才能在 Windows 上執行許多應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f63e-105">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="0f63e-106">這篇文章中的指示應該協助您安裝您所需要的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0f63e-106">The instructions in this article should help you install the .NET Framework versions that you need.</span></span> <span data-ttu-id="0f63e-107">[.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47)是最新可用版本。</span><span class="sxs-lookup"><span data-stu-id="0f63e-107">The [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) is the latest available version.</span></span>

<span data-ttu-id="0f63e-108">您可能已到達此頁面上嘗試執行應用程式後類似下列其中一個在電腦上看到的對話方塊：</span><span class="sxs-lookup"><span data-stu-id="0f63e-108">You may have arrived on this page after trying to run an application and seeing a dialog on your machine similar to the following one:</span></span>

![無法啟動此應用程式](./media/this-application-could-not-be-started.png)

## <a name="net-framework-471"></a><span data-ttu-id="0f63e-110">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="0f63e-110">.NET Framework 4.7.1</span></span>

<span data-ttu-id="0f63e-111">.NET Framework 4.7.1 隨附於：</span><span class="sxs-lookup"><span data-stu-id="0f63e-111">The .NET Framework 4.7.1 is included with:</span></span>

* [<span data-ttu-id="0f63e-112">Windows 10 年秋季建立者更新 （版本 1709年）</span><span class="sxs-lookup"><span data-stu-id="0f63e-112">Windows 10 Fall Creators Update (version 1709)</span></span>](https://www.microsoft.com/software-download/windows10)
* [<span data-ttu-id="0f63e-113">Windows Server 2016 （版本 1709年）</span><span class="sxs-lookup"><span data-stu-id="0f63e-113">Windows Server 2016 (version 1709)</span></span>](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709)

> [!div class="button"]
[<span data-ttu-id="0f63e-114">下載.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="0f63e-114">Download .NET Framework 4.7.1</span></span>](https://www.microsoft.com/net/download/thank-you/net471?utm_source=ms-docs&utm_medium=referral)

<span data-ttu-id="0f63e-115">[.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47)可以用來執行建置 4.7.1 透過.NET Framework 4.0 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f63e-115">The [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) can be used to run applications built for the .NET Framework 4.0 through 4.7.1.</span></span>

<span data-ttu-id="0f63e-116">您可以安裝[.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47)上：</span><span class="sxs-lookup"><span data-stu-id="0f63e-116">You can install the [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) on:</span></span>

* <span data-ttu-id="0f63e-117">Windows 10 建立者更新 （版本 1703年）</span><span class="sxs-lookup"><span data-stu-id="0f63e-117">Windows 10 Creators Update (version 1703)</span></span>
* <span data-ttu-id="0f63e-118">Windows 10 年度更新 （版本 1607年）</span><span class="sxs-lookup"><span data-stu-id="0f63e-118">Windows 10 Anniversary Update (version 1607)</span></span>
* <span data-ttu-id="0f63e-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="0f63e-119">Windows Server 2016</span></span>

<span data-ttu-id="0f63e-120">不支援.NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="0f63e-120">The .NET Framework 4.7.1 is not supported on:</span></span>

* <span data-ttu-id="0f63e-121">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="0f63e-121">Windows 10 1507</span></span>
* <span data-ttu-id="0f63e-122">Windows 10 1511</span><span class="sxs-lookup"><span data-stu-id="0f63e-122">Windows 10 1511</span></span>

<span data-ttu-id="0f63e-123">如果您使用 Windows 10 1507年或 1511年，而且您想要安裝.NET Framework 4.7.1，您必須先升級至較新版的 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="0f63e-123">If you're using Windows 10 1507 or 1511 and you want to install the .NET Framework 4.7.1, you first need to upgrade to a later Windows 10 version.</span></span>

## <a name="net-framework-461"></a><span data-ttu-id="0f63e-124">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0f63e-124">.NET Framework 4.6.1</span></span>

<span data-ttu-id="0f63e-125">[.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981)是最新支援.NET Framework 版本的 Windows 10 1507年和 1511年。</span><span class="sxs-lookup"><span data-stu-id="0f63e-125">The [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) is the latest supported .NET Framework version on Windows 10 1507 and 1511.</span></span>

<span data-ttu-id="0f63e-126">.NET Framework 4.6.1 支援.NET Framework 4.0，透過 4.6.1 的建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f63e-126">The .NET Framework 4.6.1 supports apps built for the .NET Framework 4.0 through 4.6.1.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="0f63e-127">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="0f63e-127">.NET Framework 3.5</span></span>

<span data-ttu-id="0f63e-128">請依照指示[在 Windows 10 上安裝 .NET Framework 3.5](dotnet-35-windows-10.md)。</span><span class="sxs-lookup"><span data-stu-id="0f63e-128">Follow the instructions to install the [.NET Framework 3.5 on Windows 10](dotnet-35-windows-10.md).</span></span>

<span data-ttu-id="0f63e-129">.NET Framework 3.5 支援的.NET Framework 1.0 到 3.5 所建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f63e-129">The .NET Framework 3.5 supports apps built for the .NET Framework 1.0 through 3.5.</span></span>

## <a name="additional-information"></a><span data-ttu-id="0f63e-130">其他資訊</span><span class="sxs-lookup"><span data-stu-id="0f63e-130">Additional information</span></span>

<span data-ttu-id="0f63e-131">.NET framework 4.x 版本是舊版的就地更新。</span><span class="sxs-lookup"><span data-stu-id="0f63e-131">.NET Framework 4.x versions are in-place updates to earlier versions.</span></span> <span data-ttu-id="0f63e-132">這表示下列項目：</span><span class="sxs-lookup"><span data-stu-id="0f63e-132">That means the following:</span></span>

- <span data-ttu-id="0f63e-133">您可以只有一個版本的.NET framework 4.x 安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0f63e-133">You can only have one version of the .NET Framework 4.x installed on your machine.</span></span>

- <span data-ttu-id="0f63e-134">如果已安裝較新版本，您無法在電腦上安裝舊版的.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0f63e-134">You cannot install an earlier version of the .NET Framework on your machine if a later version is already installed.</span></span>

- <span data-ttu-id="0f63e-135">.NET framework 4.x 版本可以用來執行建置.NET Framework 4.0，透過該版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f63e-135">4.x versions of the .NET Framework can be used to run applications built for the .NET Framework 4.0 through that version.</span></span> <span data-ttu-id="0f63e-136">例如，.NET Framework 4.7 可以用來執行建置 4.7 透過.NET Framework 4.0 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f63e-136">For example, .NET Framework 4.7 can be used to run applications built for the .NET Framework 4.0 through 4.7.</span></span> <span data-ttu-id="0f63e-137">最新版本 (.NET Framework 4.7.1) 可以用來執行建置的應用程式將所有版本的.NET Framework 4.0 為開頭。</span><span class="sxs-lookup"><span data-stu-id="0f63e-137">The latest version (the .NET Framework 4.7.1) can be used to run applications built will all versions of the .NET Framework starting with 4.0.</span></span>

<span data-ttu-id="0f63e-138">如需可供下載的.NET framework 的所有版本的清單，請參閱[.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)頁面。</span><span class="sxs-lookup"><span data-stu-id="0f63e-138">For a list of all the versions of the .NET Framework available to download, see the [.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) page.</span></span>

## <a name="help"></a><span data-ttu-id="0f63e-139">說明</span><span class="sxs-lookup"><span data-stu-id="0f63e-139">Help</span></span>

<span data-ttu-id="0f63e-140">如果您無法取得安裝的.NET Framework 正確版本，您可以[連絡 Microsoft 以取得協助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。</span><span class="sxs-lookup"><span data-stu-id="0f63e-140">If you cannot get the correct version of the .NET Framework installed, you can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f63e-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f63e-141">See also</span></span>

<span data-ttu-id="0f63e-142">[.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span><span class="sxs-lookup"><span data-stu-id="0f63e-142">[.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span></span>  
<span data-ttu-id="0f63e-143">[疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md) </span><span class="sxs-lookup"><span data-stu-id="0f63e-143">[Troubleshoot blocked .NET Framework installations and uninstallations](troubleshoot-blocked-installations-and-uninstallations.md) </span></span>  
[<span data-ttu-id="0f63e-144">安裝.NET Framework 開發人員</span><span class="sxs-lookup"><span data-stu-id="0f63e-144">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
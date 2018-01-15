---
title: "在 Windows 10 上安裝 .NET Framework"
description: "了解如何在 Windows 10 或 Windows Server 2016 上安裝 .NET Framework。"
author: rlander
ms.author: mairaw
keywords: ".NET Framework, 安裝"
ms.date: 12/20/2017
ms.topic: article
ms.custom: updateeachrelease
ms.prod: .net-framework
ms.workload: dotnet
ms.openlocfilehash: bd588dff62e5d4ac1c1059e697a07598ba272042
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a><span data-ttu-id="b2675-104">在 Windows 10 和 Windows Server 2016 上安裝 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b2675-104">Install the .NET Framework on Windows 10 and Windows Server 2016</span></span>

<span data-ttu-id="b2675-105">在 Windows 上執行許多應用程式時需要 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="b2675-105">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="b2675-106">本文中的指示可協助您安裝所需的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="b2675-106">The instructions in this article should help you install the .NET Framework versions that you need.</span></span> <span data-ttu-id="b2675-107">[.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) 是提供的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b2675-107">The [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) is the latest available version.</span></span>

<span data-ttu-id="b2675-108">嘗試執行應用程式之後可能會進入此頁面，並會於您的電腦上看到類似如下的對話方塊：</span><span class="sxs-lookup"><span data-stu-id="b2675-108">You may have arrived on this page after trying to run an application and seeing a dialog on your machine similar to the following one:</span></span>

![無法啟動這個應用程式](./media/this-application-could-not-be-started.png)

## <a name="net-framework-471"></a><span data-ttu-id="b2675-110">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b2675-110">.NET Framework 4.7.1</span></span>

<span data-ttu-id="b2675-111">.NET Framework 4.7.1 隨附於下列項目中：</span><span class="sxs-lookup"><span data-stu-id="b2675-111">The .NET Framework 4.7.1 is included with:</span></span>

* [<span data-ttu-id="b2675-112">Windows 10 Fall Creators Update (版本 1709)</span><span class="sxs-lookup"><span data-stu-id="b2675-112">Windows 10 Fall Creators Update (version 1709)</span></span>](https://www.microsoft.com/software-download/windows10)
* [<span data-ttu-id="b2675-113">Windows Server，1709 版</span><span class="sxs-lookup"><span data-stu-id="b2675-113">Windows Server, version 1709</span></span>](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709)

> [!div class="button"]
[<span data-ttu-id="b2675-114">下載 .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b2675-114">Download .NET Framework 4.7.1</span></span>](https://www.microsoft.com/net/download/thank-you/net471?utm_source=ms-docs&utm_medium=referral)

<span data-ttu-id="b2675-115">[.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) 可用於執行專為 .NET Framework 4.0 到 4.7.1 建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2675-115">The [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) can be used to run applications built for the .NET Framework 4.0 through 4.7.1.</span></span>

<span data-ttu-id="b2675-116">您可將 [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) 安裝於：</span><span class="sxs-lookup"><span data-stu-id="b2675-116">You can install the [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) on:</span></span>

* <span data-ttu-id="b2675-117">Windows 10 Creators Update (版本 1703)</span><span class="sxs-lookup"><span data-stu-id="b2675-117">Windows 10 Creators Update (version 1703)</span></span>
* <span data-ttu-id="b2675-118">Windows 10 年度更新版 (版本 1607)</span><span class="sxs-lookup"><span data-stu-id="b2675-118">Windows 10 Anniversary Update (version 1607)</span></span>
* <span data-ttu-id="b2675-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b2675-119">Windows Server 2016</span></span>

<span data-ttu-id="b2675-120">以下項目不支援 .NET Framework 4.7.1：</span><span class="sxs-lookup"><span data-stu-id="b2675-120">The .NET Framework 4.7.1 is not supported on:</span></span>

* <span data-ttu-id="b2675-121">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="b2675-121">Windows 10 1507</span></span>
* <span data-ttu-id="b2675-122">Windows 10 1511</span><span class="sxs-lookup"><span data-stu-id="b2675-122">Windows 10 1511</span></span>

<span data-ttu-id="b2675-123">若目前使用 Windows 10 1507 或 1511，且希望安裝.NET Framework 4.7.1，即必須先升級至更新版的 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="b2675-123">If you're using Windows 10 1507 or 1511 and you want to install the .NET Framework 4.7.1, you first need to upgrade to a later Windows 10 version.</span></span>

## <a name="net-framework-462"></a><span data-ttu-id="b2675-124">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b2675-124">.NET Framework 4.6.2</span></span>

<span data-ttu-id="b2675-125">[.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) 是 Windows 10 1507 和 1511 支援之最新版 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="b2675-125">The [.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) is the latest supported .NET Framework version on Windows 10 1507 and 1511.</span></span>

<span data-ttu-id="b2675-126">.NET Framework 4.6.2 支援專為 .NET Framework 4.0 到 4.6.2 建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2675-126">The .NET Framework 4.6.2 supports apps built for the .NET Framework 4.0 through 4.6.2.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="b2675-127">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="b2675-127">.NET Framework 3.5</span></span>

<span data-ttu-id="b2675-128">請依照指示[在 Windows 10 上安裝 .NET Framework 3.5](dotnet-35-windows-10.md)。</span><span class="sxs-lookup"><span data-stu-id="b2675-128">Follow the instructions to install the [.NET Framework 3.5 on Windows 10](dotnet-35-windows-10.md).</span></span>

<span data-ttu-id="b2675-129">.NET Framework 3.5 支援專為 .NET Framework 1.0 到 3.5 建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2675-129">The .NET Framework 3.5 supports apps built for the .NET Framework 1.0 through 3.5.</span></span>

## <a name="additional-information"></a><span data-ttu-id="b2675-130">其他資訊</span><span class="sxs-lookup"><span data-stu-id="b2675-130">Additional information</span></span>

<span data-ttu-id="b2675-131">.NET Framework 4.x 版本是舊版的就地更新。</span><span class="sxs-lookup"><span data-stu-id="b2675-131">.NET Framework 4.x versions are in-place updates to earlier versions.</span></span> <span data-ttu-id="b2675-132">這表示：</span><span class="sxs-lookup"><span data-stu-id="b2675-132">That means the following:</span></span>

- <span data-ttu-id="b2675-133">您的電腦上只可安裝一個版本的 .NET framework 4.x。</span><span class="sxs-lookup"><span data-stu-id="b2675-133">You can only have one version of the .NET Framework 4.x installed on your machine.</span></span>

- <span data-ttu-id="b2675-134">若電腦上已安裝了更新的 .NET Framework 版本，就無法安裝舊版。</span><span class="sxs-lookup"><span data-stu-id="b2675-134">You cannot install an earlier version of the .NET Framework on your machine if a later version is already installed.</span></span>

- <span data-ttu-id="b2675-135">4.x 版的 .NET Framework 可用於執行專為 .NET Framework 4.0 及其小數點版本所建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2675-135">4.x versions of the .NET Framework can be used to run applications built for the .NET Framework 4.0 through that version.</span></span> <span data-ttu-id="b2675-136">例如，.NET Framework 4.7 可用於執行專為 .NET Framework 4.0 到 4.7 所建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2675-136">For example, .NET Framework 4.7 can be used to run applications built for the .NET Framework 4.0 through 4.7.</span></span> <span data-ttu-id="b2675-137">最新版本 (.NET Framework 4.7.1) 可用於執行專為所有從 4.0 開始的 .NET Framework 版本，所建置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2675-137">The latest version (the .NET Framework 4.7.1) can be used to run applications built will all versions of the .NET Framework starting with 4.0.</span></span>

<span data-ttu-id="b2675-138">如需所有所有可下載之 .NET Framework 版本的清單，請參閱 [.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)頁面。</span><span class="sxs-lookup"><span data-stu-id="b2675-138">For a list of all the versions of the .NET Framework available to download, see the [.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) page.</span></span>

## <a name="help"></a><span data-ttu-id="b2675-139">說明</span><span class="sxs-lookup"><span data-stu-id="b2675-139">Help</span></span>

<span data-ttu-id="b2675-140">若無法安裝正確的 .NET Framework 版本，可[連絡 Microsoft 取得協助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。</span><span class="sxs-lookup"><span data-stu-id="b2675-140">If you cannot get the correct version of the .NET Framework installed, you can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2675-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2675-141">See also</span></span>

<span data-ttu-id="b2675-142">[.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span><span class="sxs-lookup"><span data-stu-id="b2675-142">[.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span></span>  
<span data-ttu-id="b2675-143">[疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md) </span><span class="sxs-lookup"><span data-stu-id="b2675-143">[Troubleshoot blocked .NET Framework installations and uninstallations](troubleshoot-blocked-installations-and-uninstallations.md) </span></span>  
[<span data-ttu-id="b2675-144">安裝適用於開發人員的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b2675-144">Install the .NET Framework for developers</span></span>](guide-for-developers.md)

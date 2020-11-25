---
title: 重大變更： Blazor：已更新瀏覽器支援
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor：更新的瀏覽器支援
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 63b35aa8cb73bfb82c565007704375bac3737299
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760773"
---
# <a name="blazor-updated-browser-support"></a><span data-ttu-id="3fafa-103">Blazor：已更新瀏覽器支援</span><span class="sxs-lookup"><span data-stu-id="3fafa-103">Blazor: Updated browser support</span></span>

<span data-ttu-id="3fafa-104">ASP.NET Core 5.0 引進了 [新的 Blazor 功能](https://github.com/dotnet/aspnetcore/issues/21514)，其中有些功能與舊版瀏覽器不相容。</span><span class="sxs-lookup"><span data-stu-id="3fafa-104">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="3fafa-105">ASP.NET Core 5.0 中的 Blazor 所支援的瀏覽器清單已隨之更新。</span><span class="sxs-lookup"><span data-stu-id="3fafa-105">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="3fafa-106">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475)。</span><span class="sxs-lookup"><span data-stu-id="3fafa-106">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3fafa-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3fafa-107">Version introduced</span></span>

<span data-ttu-id="3fafa-108">5.0</span><span class="sxs-lookup"><span data-stu-id="3fafa-108">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3fafa-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="3fafa-109">Old behavior</span></span>

<span data-ttu-id="3fafa-110">Blazor Server 支援具有足夠 polyfill 的 Microsoft Internet Explorer 11。</span><span class="sxs-lookup"><span data-stu-id="3fafa-110">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="3fafa-111">Blazor 伺服器和 Blazor WebAssembly 也可在 [舊版 Microsoft Edge](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)中運作。</span><span class="sxs-lookup"><span data-stu-id="3fafa-111">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="3fafa-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="3fafa-112">New behavior</span></span>

<span data-ttu-id="3fafa-113">Microsoft Internet Explorer 11 不支援 ASP.NET Core 5.0 中的 Blazor 伺服器。</span><span class="sxs-lookup"><span data-stu-id="3fafa-113">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="3fafa-114">Blazor 伺服器和 Blazor WebAssembly 無法在舊版 Microsoft Edge 中完整運作。</span><span class="sxs-lookup"><span data-stu-id="3fafa-114">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3fafa-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="3fafa-115">Reason for change</span></span>

<span data-ttu-id="3fafa-116">ASP.NET Core 5.0 中的新 Blazor 功能與這些舊版瀏覽器不相容，因此會降低這些舊版瀏覽器的使用。</span><span class="sxs-lookup"><span data-stu-id="3fafa-116">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="3fafa-117">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="3fafa-117">For more information, see the following resources:</span></span>

* [<span data-ttu-id="3fafa-118">舊版 Microsoft Edge 的 Windows 支援也會在2021年3月9日結束</span><span class="sxs-lookup"><span data-stu-id="3fafa-118">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="3fafa-119">Microsoft 365 的應用程式和服務將于2021年8月17日結束 Microsoft Internet Explorer 11 的支援</span><span class="sxs-lookup"><span data-stu-id="3fafa-119">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a><span data-ttu-id="3fafa-120">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3fafa-120">Recommended action</span></span>

<span data-ttu-id="3fafa-121">從這些舊版瀏覽器升級至 [新的 Chromium 式 Microsoft Edge](https://www.microsoft.com/edge)。</span><span class="sxs-lookup"><span data-stu-id="3fafa-121">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="3fafa-122">對於需要支援這些舊版瀏覽器的 Blazor 應用程式，請使用 ASP.NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="3fafa-122">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="3fafa-123">ASP.NET Core 3.1 中的 Blazor 支援的瀏覽器清單未變更，並記載于 [支援的平臺](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1)上。</span><span class="sxs-lookup"><span data-stu-id="3fafa-123">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3fafa-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3fafa-124">Affected APIs</span></span>

<span data-ttu-id="3fafa-125">None</span><span class="sxs-lookup"><span data-stu-id="3fafa-125">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->

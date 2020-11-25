---
title: 重大變更： Blazor： ProtectedBrowserStorage 功能已移至共用架構
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： ProtectedBrowserStorage 功能已移至共用架構
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c8058adf8b66aef8dd011ea672cd306ae4de60a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760662"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="14bd6-103">Blazor： ProtectedBrowserStorage 功能已移至共用架構</span><span class="sxs-lookup"><span data-stu-id="14bd6-103">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="14bd6-104">在 ASP.NET Core 5.0 RC2 版中，此功能已 `ProtectedBrowserStorage` 移至 ASP.NET Core 的共用架構。</span><span class="sxs-lookup"><span data-stu-id="14bd6-104">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="14bd6-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="14bd6-105">Version introduced</span></span>

<span data-ttu-id="14bd6-106">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="14bd6-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="14bd6-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="14bd6-107">Old behavior</span></span>

<span data-ttu-id="14bd6-108">在 ASP.NET Core 5.0 Preview 8 中，此功能可作為 [AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) 套件的一部分，但是只能在 Blazor WebAssembly 中使用。</span><span class="sxs-lookup"><span data-stu-id="14bd6-108">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="14bd6-109">在 ASP.NET Core 5.0 RC1 中，此功能是 [AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) 的一部分，可參考 `Microsoft.AspNetCore.App` 共用架構。</span><span class="sxs-lookup"><span data-stu-id="14bd6-109">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="14bd6-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="14bd6-110">New behavior</span></span>

<span data-ttu-id="14bd6-111">在 ASP.NET Core 5.0 RC2 中，不再需要 NuGet 套件參考，也無法使用此功能。</span><span class="sxs-lookup"><span data-stu-id="14bd6-111">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="14bd6-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="14bd6-112">Reason for change</span></span>

<span data-ttu-id="14bd6-113">移至共用架構更適合客戶所預期的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="14bd6-113">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="14bd6-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="14bd6-114">Recommended action</span></span>

<span data-ttu-id="14bd6-115">如果從 ASP.NET Core 5.0 RC1 升級，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="14bd6-115">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="14bd6-116">`Microsoft.AspNetCore.Components.ProtectedBrowserStorage`從專案移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="14bd6-116">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="14bd6-117">將 `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` 取代為 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。</span><span class="sxs-lookup"><span data-stu-id="14bd6-117">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="14bd6-118">從您的類別中移除對的呼叫 `AddProtectedBrowserStorage` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="14bd6-118">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="14bd6-119">如果從 ASP.NET Core 5.0 Preview 8 升級，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="14bd6-119">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="14bd6-120">`Microsoft.AspNetCore.Components.Web.Extensions`從專案移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="14bd6-120">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="14bd6-121">將 `using Microsoft.AspNetCore.Components.Web.Extensions;` 取代為 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。</span><span class="sxs-lookup"><span data-stu-id="14bd6-121">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="14bd6-122">從您的類別中移除對的呼叫 `AddProtectedBrowserStorage` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="14bd6-122">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="14bd6-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="14bd6-123">Affected APIs</span></span>

<span data-ttu-id="14bd6-124">None</span><span class="sxs-lookup"><span data-stu-id="14bd6-124">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->

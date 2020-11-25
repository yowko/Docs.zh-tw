---
title: 重大變更：已移除 Pubternal Api
description: 瞭解已移除部分 pubternal 當地語系化 Api 的 ASP.NET Core 5.0 中的重大變更
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ae647d66b716175536edb3c978b027ebb7d3ddac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760467"
---
# <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="3d054-103">當地語系化：已移除 "Pubternal" Api</span><span class="sxs-lookup"><span data-stu-id="3d054-103">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="3d054-104">為了更妥善維護 ASP.NET Core 的公用 API 介面，已 :::no-loc text="\"pubternal\""::: 移除部分當地語系化 api。</span><span class="sxs-lookup"><span data-stu-id="3d054-104">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="3d054-105">:::no-loc text="\"pubternal\"":::API 具有 `public` 存取修飾詞，而且是在表示[內部](../../../../csharp/language-reference/keywords/internal.md)意圖的命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="3d054-105">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="3d054-106">如需討論，請參閱 [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291)。</span><span class="sxs-lookup"><span data-stu-id="3d054-106">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3d054-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3d054-107">Version introduced</span></span>

<span data-ttu-id="3d054-108">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="3d054-108">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3d054-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="3d054-109">Old behavior</span></span>

<span data-ttu-id="3d054-110">下列 Api 為 `public` ：</span><span class="sxs-lookup"><span data-stu-id="3d054-110">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="3d054-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 接受下列其中一個參數類型的函式多載：</span><span class="sxs-lookup"><span data-stu-id="3d054-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a><span data-ttu-id="3d054-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="3d054-112">New behavior</span></span>

<span data-ttu-id="3d054-113">下列清單概述這些變更：</span><span class="sxs-lookup"><span data-stu-id="3d054-113">The following list outlines the changes:</span></span>

- <span data-ttu-id="3d054-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`已成為，現在是 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="3d054-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="3d054-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`已成為，現在是 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="3d054-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="3d054-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 現在接受下列其中一個參數類型的函式多載 `internal` ：</span><span class="sxs-lookup"><span data-stu-id="3d054-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a><span data-ttu-id="3d054-117">變更的原因</span><span class="sxs-lookup"><span data-stu-id="3d054-117">Reason for change</span></span>

<span data-ttu-id="3d054-118">在 [aspnet/公告 # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)上更詳盡地說明， :::no-loc text="\"pubternal\""::: 類型已從 `public` API 介面中移除。</span><span class="sxs-lookup"><span data-stu-id="3d054-118">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="3d054-119">這些變更會將更多類別調整為該設計決策。</span><span class="sxs-lookup"><span data-stu-id="3d054-119">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="3d054-120">有問題的類別是為了團隊內部測試的擴充點。</span><span class="sxs-lookup"><span data-stu-id="3d054-120">The classes in question were intended as extension points for the team's internal testing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3d054-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3d054-121">Recommended action</span></span>

<span data-ttu-id="3d054-122">雖然不太可能，但有些應用程式可能會刻意或意外相依于這些 :::no-loc text="\"pubternal\""::: 類型。</span><span class="sxs-lookup"><span data-stu-id="3d054-122">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="3d054-123">請參閱 [新的行為](#new-behavior) 章節，以判斷如何從類型遷移。</span><span class="sxs-lookup"><span data-stu-id="3d054-123">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="3d054-124">如果您已識別出此變更之前所允許的公用 API，但目前尚未進行的案例，請在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)提出問題。</span><span class="sxs-lookup"><span data-stu-id="3d054-124">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3d054-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3d054-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->

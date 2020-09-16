---
ms.openlocfilehash: 62a5f56bb7fffc453623a2c3202f288a19110158
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539452"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="cefda-101">當地語系化：已移除 "Pubternal" Api</span><span class="sxs-lookup"><span data-stu-id="cefda-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="cefda-102">為了更妥善維護 ASP.NET Core 的公用 API 介面，已 :::no-loc text="\"pubternal\""::: 移除部分當地語系化 api。</span><span class="sxs-lookup"><span data-stu-id="cefda-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="cefda-103">:::no-loc text="\"pubternal\"":::API 具有 `public` 存取修飾詞，而且是在表示[內部](../../../../docs/csharp/language-reference/keywords/internal.md)意圖的命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="cefda-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../docs/csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="cefda-104">如需討論，請參閱 [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291)。</span><span class="sxs-lookup"><span data-stu-id="cefda-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cefda-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="cefda-105">Version introduced</span></span>

<span data-ttu-id="cefda-106">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="cefda-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cefda-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="cefda-107">Old behavior</span></span>

<span data-ttu-id="cefda-108">下列 Api 為 `public` ：</span><span class="sxs-lookup"><span data-stu-id="cefda-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="cefda-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 接受下列其中一個參數類型的函式多載：</span><span class="sxs-lookup"><span data-stu-id="cefda-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="cefda-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="cefda-110">New behavior</span></span>

<span data-ttu-id="cefda-111">下列清單概述這些變更：</span><span class="sxs-lookup"><span data-stu-id="cefda-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="cefda-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`已成為，現在是 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="cefda-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="cefda-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`已成為，現在是 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="cefda-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="cefda-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 現在接受下列其中一個參數類型的函式多載 `internal` ：</span><span class="sxs-lookup"><span data-stu-id="cefda-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="cefda-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="cefda-115">Reason for change</span></span>

<span data-ttu-id="cefda-116">在 [aspnet/公告 # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)上更詳盡地說明， :::no-loc text="\"pubternal\""::: 類型已從 `public` API 介面中移除。</span><span class="sxs-lookup"><span data-stu-id="cefda-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="cefda-117">這些變更會將更多類別調整為該設計決策。</span><span class="sxs-lookup"><span data-stu-id="cefda-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="cefda-118">有問題的類別是為了團隊內部測試的擴充點。</span><span class="sxs-lookup"><span data-stu-id="cefda-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cefda-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="cefda-119">Recommended action</span></span>

<span data-ttu-id="cefda-120">雖然不太可能，但有些應用程式可能會刻意或意外相依于這些 :::no-loc text="\"pubternal\""::: 類型。</span><span class="sxs-lookup"><span data-stu-id="cefda-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="cefda-121">請參閱 [新的行為](#new-behavior) 章節，以判斷如何從類型遷移。</span><span class="sxs-lookup"><span data-stu-id="cefda-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="cefda-122">如果您已識別出此變更之前所允許的公用 API，但目前尚未進行的案例，請在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)提出問題。</span><span class="sxs-lookup"><span data-stu-id="cefda-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="cefda-123">類別</span><span class="sxs-lookup"><span data-stu-id="cefda-123">Category</span></span>

<span data-ttu-id="cefda-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cefda-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cefda-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="cefda-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->

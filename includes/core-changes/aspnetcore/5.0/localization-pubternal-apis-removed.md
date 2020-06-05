---
ms.openlocfilehash: 2094da7ec94028c112d6683620ac1146a1544dab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446964"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="5e72d-101">當地語系化：已移除 "Pubternal" Api</span><span class="sxs-lookup"><span data-stu-id="5e72d-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="5e72d-102">為了更有效地維護 ASP.NET Core 的公用 API 介面，已 :::no-loc text="\"pubternal\""::: 移除部分當地語系化 api。</span><span class="sxs-lookup"><span data-stu-id="5e72d-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="5e72d-103">:::no-loc text="\"pubternal\"":::API 具有 `public` 存取修飾詞，並在表示[內部](/dotnet/csharp/language-reference/keywords/internal)意圖的命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="5e72d-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](/dotnet/csharp/language-reference/keywords/internal) intent.</span></span>

<span data-ttu-id="5e72d-104">如需討論，請參閱[dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291)。</span><span class="sxs-lookup"><span data-stu-id="5e72d-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5e72d-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5e72d-105">Version introduced</span></span>

<span data-ttu-id="5e72d-106">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="5e72d-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5e72d-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5e72d-107">Old behavior</span></span>

<span data-ttu-id="5e72d-108">下列 Api 是 `public` ：</span><span class="sxs-lookup"><span data-stu-id="5e72d-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="5e72d-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`函式多載接受下列其中一種參數類型：</span><span class="sxs-lookup"><span data-stu-id="5e72d-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="5e72d-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="5e72d-110">New behavior</span></span>

<span data-ttu-id="5e72d-111">下列清單列出變更的內容：</span><span class="sxs-lookup"><span data-stu-id="5e72d-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="5e72d-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`已成為，現在是 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="5e72d-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="5e72d-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`已成為，現在是 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="5e72d-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="5e72d-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`接受下列任一參數類型的函式多載現在是 `internal` ：</span><span class="sxs-lookup"><span data-stu-id="5e72d-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="5e72d-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="5e72d-115">Reason for change</span></span>

<span data-ttu-id="5e72d-116">在[aspnet/公告 # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)中更深入說明， :::no-loc text="\"pubternal\""::: 類型已從 `public` API 介面中移除。</span><span class="sxs-lookup"><span data-stu-id="5e72d-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="5e72d-117">這些變更會將更多類別調整為該設計決策。</span><span class="sxs-lookup"><span data-stu-id="5e72d-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="5e72d-118">有問題的類別是做為小組內部測試的延伸點。</span><span class="sxs-lookup"><span data-stu-id="5e72d-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5e72d-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5e72d-119">Recommended action</span></span>

<span data-ttu-id="5e72d-120">雖然不太可能，但有些應用程式可能會刻意或意外依賴 :::no-loc text="\"pubternal\""::: 類型。</span><span class="sxs-lookup"><span data-stu-id="5e72d-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="5e72d-121">請參閱[新的行為](#new-behavior)章節，以決定如何從類型中遷移。</span><span class="sxs-lookup"><span data-stu-id="5e72d-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="5e72d-122">如果您已識別出在此變更之前允許公用 API 的案例，但目前並不存在，請在[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)提出問題。</span><span class="sxs-lookup"><span data-stu-id="5e72d-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="5e72d-123">類別</span><span class="sxs-lookup"><span data-stu-id="5e72d-123">Category</span></span>

<span data-ttu-id="5e72d-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5e72d-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5e72d-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5e72d-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->

---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901872"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="40142-101">當地語系化：資源管理器具有區域性字串當地語系化器和標記為過時的區域性</span><span class="sxs-lookup"><span data-stu-id="40142-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="40142-102">[資源管理器與文化StringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)類和["與文化"](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170)介面成員通常是當地語系化使用者感到困惑的根源，尤其是在創建自己的`IStringLocalizer`實現時。</span><span class="sxs-lookup"><span data-stu-id="40142-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="40142-103">這些專案給使用者的印象是，實例`IStringLocalizer`是"按語言，按資源"。</span><span class="sxs-lookup"><span data-stu-id="40142-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="40142-104">實際上，實例應僅是"按資源"。</span><span class="sxs-lookup"><span data-stu-id="40142-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="40142-105">搜索的語言由執行`CultureInfo.CurrentUICulture`時確定。</span><span class="sxs-lookup"><span data-stu-id="40142-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="40142-106">為了消除混淆源，API 在 ASP.NET 酷 3.0 預覽 3 中標記為過時。</span><span class="sxs-lookup"><span data-stu-id="40142-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="40142-107">API 將在將來的版本中被刪除。</span><span class="sxs-lookup"><span data-stu-id="40142-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="40142-108">有關上下文，請參閱[點網/阿斯平核心#3324](https://github.com/dotnet/aspnetcore/issues/3324)。</span><span class="sxs-lookup"><span data-stu-id="40142-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="40142-109">有關討論，請參閱[點網/阿斯平核心#7756](https://github.com/dotnet/aspnetcore/issues/7756)。</span><span class="sxs-lookup"><span data-stu-id="40142-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40142-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="40142-110">Version introduced</span></span>

<span data-ttu-id="40142-111">3.0</span><span class="sxs-lookup"><span data-stu-id="40142-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="40142-112">舊的行為</span><span class="sxs-lookup"><span data-stu-id="40142-112">Old behavior</span></span>

<span data-ttu-id="40142-113">方法未標記為`Obsolete`。</span><span class="sxs-lookup"><span data-stu-id="40142-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="40142-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="40142-114">New behavior</span></span>

<span data-ttu-id="40142-115">方法被標記`Obsolete`。</span><span class="sxs-lookup"><span data-stu-id="40142-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="40142-116">更改原因</span><span class="sxs-lookup"><span data-stu-id="40142-116">Reason for change</span></span>

<span data-ttu-id="40142-117">API 表示不推薦的用例。</span><span class="sxs-lookup"><span data-stu-id="40142-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="40142-118">當地語系化設計存在混淆。</span><span class="sxs-lookup"><span data-stu-id="40142-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40142-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="40142-119">Recommended action</span></span>

<span data-ttu-id="40142-120">建議改為使用`ResourceManagerStringLocalizer`。</span><span class="sxs-lookup"><span data-stu-id="40142-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="40142-121">讓區域性由 設置`CurrentCulture`。</span><span class="sxs-lookup"><span data-stu-id="40142-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="40142-122">如果這不是一個選項，請創建並使用[資源管理器與文化字串當地語系化器](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)的副本。</span><span class="sxs-lookup"><span data-stu-id="40142-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="40142-123">類別</span><span class="sxs-lookup"><span data-stu-id="40142-123">Category</span></span>

<span data-ttu-id="40142-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40142-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40142-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="40142-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

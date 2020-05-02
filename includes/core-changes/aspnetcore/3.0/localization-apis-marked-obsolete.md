---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728344"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="d2308-101">當地語系化：標記為過時的 ResourceManagerWithCultureStringLocalizer 和 WithCulture</span><span class="sxs-lookup"><span data-stu-id="d2308-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="d2308-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)類別和[WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170)介面成員通常是當地語系化使用者的混淆來源，特別是在建立自己`IStringLocalizer`的執行時。</span><span class="sxs-lookup"><span data-stu-id="d2308-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="d2308-103">這些專案會讓使用者印象是， `IStringLocalizer`實例是「每一語言，每個資源」。</span><span class="sxs-lookup"><span data-stu-id="d2308-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="d2308-104">實際上，實例應該只是「每個資源」。</span><span class="sxs-lookup"><span data-stu-id="d2308-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="d2308-105">搜尋的語言是在執行時間由`CultureInfo.CurrentUICulture`所決定。</span><span class="sxs-lookup"><span data-stu-id="d2308-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="d2308-106">為了消除混淆的來源，在 ASP.NET Core 3.0 Preview 3 中，Api 已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="d2308-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="d2308-107">Api 將會在未來的版本中移除。</span><span class="sxs-lookup"><span data-stu-id="d2308-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="d2308-108">如需內容，請參閱[dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324)。</span><span class="sxs-lookup"><span data-stu-id="d2308-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="d2308-109">如需討論，請參閱[dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756)。</span><span class="sxs-lookup"><span data-stu-id="d2308-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d2308-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d2308-110">Version introduced</span></span>

<span data-ttu-id="d2308-111">3.0</span><span class="sxs-lookup"><span data-stu-id="d2308-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d2308-112">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d2308-112">Old behavior</span></span>

<span data-ttu-id="d2308-113">方法未標示為`Obsolete`。</span><span class="sxs-lookup"><span data-stu-id="d2308-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d2308-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="d2308-114">New behavior</span></span>

<span data-ttu-id="d2308-115">已標記`Obsolete`方法。</span><span class="sxs-lookup"><span data-stu-id="d2308-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d2308-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d2308-116">Reason for change</span></span>

<span data-ttu-id="d2308-117">Api 代表不建議的使用案例。</span><span class="sxs-lookup"><span data-stu-id="d2308-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="d2308-118">當地語系化的設計有一些混淆。</span><span class="sxs-lookup"><span data-stu-id="d2308-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d2308-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d2308-119">Recommended action</span></span>

<span data-ttu-id="d2308-120">建議`ResourceManagerStringLocalizer`改用。</span><span class="sxs-lookup"><span data-stu-id="d2308-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="d2308-121">讓文化特性由設定`CurrentCulture`。</span><span class="sxs-lookup"><span data-stu-id="d2308-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="d2308-122">如果這不是選項，請建立並使用[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)的複本。</span><span class="sxs-lookup"><span data-stu-id="d2308-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="d2308-123">類別</span><span class="sxs-lookup"><span data-stu-id="d2308-123">Category</span></span>

<span data-ttu-id="d2308-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2308-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d2308-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d2308-125">Affected APIs</span></span>

- [<span data-ttu-id="d2308-126">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="d2308-126">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [<span data-ttu-id="d2308-127">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="d2308-127">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

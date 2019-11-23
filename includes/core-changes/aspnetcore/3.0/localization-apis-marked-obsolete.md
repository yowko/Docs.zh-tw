---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394141"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="5b2e9-101">當地語系化：標記為過時的 ResourceManagerWithCultureStringLocalizer 和 WithCulture</span><span class="sxs-lookup"><span data-stu-id="5b2e9-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="5b2e9-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)類別和[WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170)介面成員通常是當地語系化使用者的混淆來源，特別是在建立自己的 `IStringLocalizer` 執行時。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="5b2e9-103">這些專案會讓使用者印象 `IStringLocalizer` 實例是「每一語言，每個資源」。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="5b2e9-104">實際上，實例應該只是「每個資源」。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="5b2e9-105">搜尋的語言是由 `CultureInfo.CurrentUICulture` 在執行時間決定。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="5b2e9-106">為了消除混淆的來源，在 ASP.NET Core 3.0 Preview 3 中，Api 已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="5b2e9-107">Api 將會在未來的版本中移除。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="5b2e9-108">如需相關內容，請參閱[aspnet/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324)。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-108">For context, see [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324).</span></span> <span data-ttu-id="5b2e9-109">如需討論，請參閱[aspnet/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756)。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-109">For discussion, see [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5b2e9-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5b2e9-110">Version introduced</span></span>

<span data-ttu-id="5b2e9-111">3.0</span><span class="sxs-lookup"><span data-stu-id="5b2e9-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5b2e9-112">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5b2e9-112">Old behavior</span></span>

<span data-ttu-id="5b2e9-113">方法未標示為 `Obsolete`。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5b2e9-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="5b2e9-114">New behavior</span></span>

<span data-ttu-id="5b2e9-115">方法會標示為 `Obsolete`。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5b2e9-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="5b2e9-116">Reason for change</span></span>

<span data-ttu-id="5b2e9-117">Api 代表不建議的使用案例。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="5b2e9-118">當地語系化的設計有一些混淆。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5b2e9-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5b2e9-119">Recommended action</span></span>

<span data-ttu-id="5b2e9-120">建議改用 `ResourceManagerStringLocalizer`。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="5b2e9-121">讓 `CurrentCulture`設定文化特性。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="5b2e9-122">如果這不是選項，請建立並使用[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)的複本。</span><span class="sxs-lookup"><span data-stu-id="5b2e9-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="5b2e9-123">類別</span><span class="sxs-lookup"><span data-stu-id="5b2e9-123">Category</span></span>

<span data-ttu-id="5b2e9-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5b2e9-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5b2e9-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5b2e9-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

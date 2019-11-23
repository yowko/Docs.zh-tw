---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394422"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="053d2-101">MVC： "Pubternal" 類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="053d2-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="053d2-102">在 ASP.NET Core 3.0 中，MVC 中的所有 "pubternal" 類型都會更新為在支援的命名空間中 `public`，或視需要 `internal`。</span><span class="sxs-lookup"><span data-stu-id="053d2-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="053d2-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="053d2-103">Change description</span></span>

<span data-ttu-id="053d2-104">在 ASP.NET Core 中，"pubternal" 類型會宣告為 `public`，但位於 `.Internal`尾碼命名空間中。</span><span class="sxs-lookup"><span data-stu-id="053d2-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="053d2-105">雖然這些類型是 `public`的，但它們沒有支援原則，而且可能會受到重大變更。</span><span class="sxs-lookup"><span data-stu-id="053d2-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="053d2-106">可惜的是，意外使用這些型別是很常見的，因而導致這些專案的重大變更，並限制維護架構的能力。</span><span class="sxs-lookup"><span data-stu-id="053d2-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="053d2-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="053d2-107">Version introduced</span></span>

<span data-ttu-id="053d2-108">3.0</span><span class="sxs-lookup"><span data-stu-id="053d2-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="053d2-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="053d2-109">Old behavior</span></span>

<span data-ttu-id="053d2-110">MVC 中的某些類型已 `public`，但在 `.Internal` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="053d2-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="053d2-111">這些類型沒有支援原則，而且受限於中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="053d2-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="053d2-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="053d2-112">New behavior</span></span>

<span data-ttu-id="053d2-113">所有這類類型都會更新為在支援的命名空間中 `public`，或標示為 `internal`。</span><span class="sxs-lookup"><span data-stu-id="053d2-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="053d2-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="053d2-114">Reason for change</span></span>

<span data-ttu-id="053d2-115">意外使用 "pubternal" 類型是常見的，這會導致這些專案的重大變更，並限制維護架構的能力。</span><span class="sxs-lookup"><span data-stu-id="053d2-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="053d2-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="053d2-116">Recommended action</span></span>

<span data-ttu-id="053d2-117">如果您使用已確實 `public` 的類型，並已移至新的、支援的命名空間，請更新您的參考以符合新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="053d2-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="053d2-118">如果您使用已標記為 `internal`的類型，您將需要尋找替代方案。</span><span class="sxs-lookup"><span data-stu-id="053d2-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="053d2-119">先前的 "pubternal" 類型絕不支援公開使用。</span><span class="sxs-lookup"><span data-stu-id="053d2-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="053d2-120">如果這些命名空間中有特定類型對您的應用程式很重要，請在[aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues)提出問題。</span><span class="sxs-lookup"><span data-stu-id="053d2-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span> <span data-ttu-id="053d2-121">您可以考慮 `public`的要求類型。</span><span class="sxs-lookup"><span data-stu-id="053d2-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="053d2-122">類別</span><span class="sxs-lookup"><span data-stu-id="053d2-122">Category</span></span>

<span data-ttu-id="053d2-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="053d2-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="053d2-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="053d2-124">Affected APIs</span></span>

<span data-ttu-id="053d2-125">這項變更包含下列命名空間中的類型：</span><span class="sxs-lookup"><span data-stu-id="053d2-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->

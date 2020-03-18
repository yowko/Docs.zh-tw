---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902018"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="b0ac0-101">MVC："公共"類型更改為內部</span><span class="sxs-lookup"><span data-stu-id="b0ac0-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="b0ac0-102">在 ASP.NET Core 3.0 中，MVC 中的所有"公共"類型都更新`public`為受支援的命名空間中`internal`或根據需要。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b0ac0-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="b0ac0-103">Change description</span></span>

<span data-ttu-id="b0ac0-104">在ASP.NET核心中，"公共"型別宣告為`public`，但駐留在`.Internal`尾碼命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="b0ac0-105">雖然這些類型的是`public`，但它們沒有支援策略，並且可能會進行重大更改。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="b0ac0-106">遺憾的是，意外使用這些類型很常見，導致這些專案的更改中斷，並限制了維護框架的能力。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b0ac0-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="b0ac0-107">Version introduced</span></span>

<span data-ttu-id="b0ac0-108">3.0</span><span class="sxs-lookup"><span data-stu-id="b0ac0-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b0ac0-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b0ac0-109">Old behavior</span></span>

<span data-ttu-id="b0ac0-110">MVC 中的某些類型`public`在`.Internal`命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="b0ac0-111">這些類型沒有支援策略，並且可能會進行重大更改。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b0ac0-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="b0ac0-112">New behavior</span></span>

<span data-ttu-id="b0ac0-113">所有此類類型都更新為在受`public`支援的命名空間中或標記為`internal`。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b0ac0-114">更改原因</span><span class="sxs-lookup"><span data-stu-id="b0ac0-114">Reason for change</span></span>

<span data-ttu-id="b0ac0-115">意外使用"pubternal"類型很常見，導致這些專案發生重大更改，並限制了維護框架的能力。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b0ac0-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b0ac0-116">Recommended action</span></span>

<span data-ttu-id="b0ac0-117">如果您使用的類型已變為真正`public`並且已移動到受支援的新命名空間中，請更新引用以匹配新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="b0ac0-118">如果您使用的類型已標記為`internal`，則需要查找替代類型。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="b0ac0-119">以前"酒吧"類型從未被支援用於公共用途。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="b0ac0-120">如果這些命名空間中的特定類型對應用至關重要，請在[dotnet/aspnetcore 上](https://github.com/dotnet/aspnetcore/issues)提交問題。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="b0ac0-121">可以考慮使請求的類型`public`。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="b0ac0-122">類別</span><span class="sxs-lookup"><span data-stu-id="b0ac0-122">Category</span></span>

<span data-ttu-id="b0ac0-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b0ac0-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b0ac0-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b0ac0-124">Affected APIs</span></span>

<span data-ttu-id="b0ac0-125">此更改包括以下命名空間中的類型：</span><span class="sxs-lookup"><span data-stu-id="b0ac0-125">This change includes types in the following namespaces:</span></span>

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

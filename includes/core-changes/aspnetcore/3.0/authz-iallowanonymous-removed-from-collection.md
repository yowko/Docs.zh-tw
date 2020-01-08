---
ms.openlocfilehash: 89af89d3580fd1396335a0cd8964b46c13d7637e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344308"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="0f50b-101">授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 移除。篩選</span><span class="sxs-lookup"><span data-stu-id="0f50b-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="0f50b-102">從 ASP.NET Core 3.0，MVC 不會針對在控制器和動作方法上探索到的[[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute)屬性加入[AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) 。</span><span class="sxs-lookup"><span data-stu-id="0f50b-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="0f50b-103">這項變更是針對 <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>的衍生性而在本機處理，但對於 <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> 和 <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> 的執行而言，這是一項重大變更。</span><span class="sxs-lookup"><span data-stu-id="0f50b-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="0f50b-104">包裝在[[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute)屬性中的這類執行，是在需要設定和相依性插入時，用來達成強型別、以屬性為基礎之授權的[常用](https://stackoverflow.com/a/41348219/608220)和支援方式。</span><span class="sxs-lookup"><span data-stu-id="0f50b-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f50b-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0f50b-105">Version introduced</span></span>

<span data-ttu-id="0f50b-106">3.0</span><span class="sxs-lookup"><span data-stu-id="0f50b-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0f50b-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="0f50b-107">Old behavior</span></span>

<span data-ttu-id="0f50b-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> 會出現在[AuthorizationFilterCoNtext 中。](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A)</span><span class="sxs-lookup"><span data-stu-id="0f50b-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="0f50b-109">測試介面的目前狀態是一種有效的方法，可覆寫或停用個別控制器方法上的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="0f50b-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0f50b-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="0f50b-110">New behavior</span></span>

<span data-ttu-id="0f50b-111">`IAllowAnonymous` 不會再出現在 `AuthorizationFilterContext.Filters` 集合中。</span><span class="sxs-lookup"><span data-stu-id="0f50b-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="0f50b-112">相依于舊行為的 `IAsyncAuthorizationFilter` 實，通常會造成間歇性的 HTTP 401 未經授權或 HTTP 403 禁止的回應。</span><span class="sxs-lookup"><span data-stu-id="0f50b-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0f50b-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="0f50b-113">Reason for change</span></span>

<span data-ttu-id="0f50b-114">ASP.NET Core 3.0 引進了新的端點路由策略。</span><span class="sxs-lookup"><span data-stu-id="0f50b-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f50b-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0f50b-115">Recommended action</span></span>

<span data-ttu-id="0f50b-116">搜尋端點中繼資料中的 `IAllowAnonymous`。</span><span class="sxs-lookup"><span data-stu-id="0f50b-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="0f50b-117">例如：</span><span class="sxs-lookup"><span data-stu-id="0f50b-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="0f50b-118">這項技術的範例可在[此 HasAllowAnonymous 方法](https://github.com/aspnet/AspNetCore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)中找到。</span><span class="sxs-lookup"><span data-stu-id="0f50b-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/aspnet/AspNetCore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="0f50b-119">分類</span><span class="sxs-lookup"><span data-stu-id="0f50b-119">Category</span></span>

<span data-ttu-id="0f50b-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f50b-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f50b-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0f50b-121">Affected APIs</span></span>

<span data-ttu-id="0f50b-122">None</span><span class="sxs-lookup"><span data-stu-id="0f50b-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

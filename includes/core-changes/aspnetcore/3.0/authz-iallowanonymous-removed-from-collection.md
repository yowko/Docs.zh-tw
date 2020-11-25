---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032333"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="2861d-101">授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 中移除。篩選器</span><span class="sxs-lookup"><span data-stu-id="2861d-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="2861d-102">從 ASP.NET Core 3.0 起，MVC 不會為在控制器和動作方法上探索到的[[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute)屬性新增[AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) 。</span><span class="sxs-lookup"><span data-stu-id="2861d-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="2861d-103">這項變更會在本機針對衍生的進行定址 <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute> ，但它是和實作為的重大變更 <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> 。</span><span class="sxs-lookup"><span data-stu-id="2861d-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="2861d-104">當需要設定和相依性插入時，在 [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) 屬性中包裝的這類實作為一種可達成強型別屬性型授權的 [常用](https://stackoverflow.com/a/41348219/608220) 和支援方法。</span><span class="sxs-lookup"><span data-stu-id="2861d-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2861d-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="2861d-105">Version introduced</span></span>

<span data-ttu-id="2861d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="2861d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2861d-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="2861d-107">Old behavior</span></span>

<span data-ttu-id="2861d-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> 出現在 [AuthorizationFilterCoNtext。篩選](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) 集合中。</span><span class="sxs-lookup"><span data-stu-id="2861d-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="2861d-109">對介面的存在情況進行測試，是覆寫或停用個別控制器方法上篩選的有效方法。</span><span class="sxs-lookup"><span data-stu-id="2861d-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2861d-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="2861d-110">New behavior</span></span>

<span data-ttu-id="2861d-111">`IAllowAnonymous` 不會再出現在 `AuthorizationFilterContext.Filters` 集合中。</span><span class="sxs-lookup"><span data-stu-id="2861d-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="2861d-112">`IAsyncAuthorizationFilter` 相依于舊行為的相依通常會導致間歇性的 HTTP 401 未經授權或 HTTP 403 禁止的回應。</span><span class="sxs-lookup"><span data-stu-id="2861d-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2861d-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="2861d-113">Reason for change</span></span>

<span data-ttu-id="2861d-114">ASP.NET Core 3.0 中引進了新的端點路由策略。</span><span class="sxs-lookup"><span data-stu-id="2861d-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2861d-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="2861d-115">Recommended action</span></span>

<span data-ttu-id="2861d-116">搜尋的端點中繼資料 `IAllowAnonymous` 。</span><span class="sxs-lookup"><span data-stu-id="2861d-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="2861d-117">例如：</span><span class="sxs-lookup"><span data-stu-id="2861d-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="2861d-118">這個 [HasAllowAnonymous 方法](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)會顯示這項技術的範例。</span><span class="sxs-lookup"><span data-stu-id="2861d-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="2861d-119">類別</span><span class="sxs-lookup"><span data-stu-id="2861d-119">Category</span></span>

<span data-ttu-id="2861d-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2861d-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2861d-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2861d-121">Affected APIs</span></span>

<span data-ttu-id="2861d-122">None</span><span class="sxs-lookup"><span data-stu-id="2861d-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

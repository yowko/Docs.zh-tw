---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901913"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="9b0db-101">授權：從授權篩選器上下文中刪除 IAllowAnonymous。篩檢程式</span><span class="sxs-lookup"><span data-stu-id="9b0db-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="9b0db-102">從 ASP.NET Core 3.0 起，MVC 不會為在控制器和操作方法上發現的[[允許匿名]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute)屬性添加[允許匿名篩選器](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter)。</span><span class="sxs-lookup"><span data-stu-id="9b0db-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="9b0db-103">此更改在本地針對 的衍生工具<xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>進行處理，但它是 和<xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter><xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter>實現的一個重大更改。</span><span class="sxs-lookup"><span data-stu-id="9b0db-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="9b0db-104">在[[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute)屬性中包裝的此類實現是一種[流行](https://stackoverflow.com/a/41348219/608220)且受支援的方式，用於在需要配置和依賴項注入時實現強型別、基於屬性的授權。</span><span class="sxs-lookup"><span data-stu-id="9b0db-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9b0db-105">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="9b0db-105">Version introduced</span></span>

<span data-ttu-id="9b0db-106">3.0</span><span class="sxs-lookup"><span data-stu-id="9b0db-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9b0db-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="9b0db-107">Old behavior</span></span>

<span data-ttu-id="9b0db-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>出現在[授權篩選器上下文.篩選器集合中](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A)。</span><span class="sxs-lookup"><span data-stu-id="9b0db-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="9b0db-109">測試介面的存在是重寫或禁用單個控制器方法上的篩選器的有效方法。</span><span class="sxs-lookup"><span data-stu-id="9b0db-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9b0db-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="9b0db-110">New behavior</span></span>

<span data-ttu-id="9b0db-111">`IAllowAnonymous`不再出現在集合中`AuthorizationFilterContext.Filters`。</span><span class="sxs-lookup"><span data-stu-id="9b0db-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="9b0db-112">`IAsyncAuthorizationFilter`依賴于舊行為的實現通常會導致間歇性 HTTP 401 未經授權的或 HTTP 403 禁止回應。</span><span class="sxs-lookup"><span data-stu-id="9b0db-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9b0db-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="9b0db-113">Reason for change</span></span>

<span data-ttu-id="9b0db-114">在 ASP.NET Core 3.0 中引入了新的端點路由策略。</span><span class="sxs-lookup"><span data-stu-id="9b0db-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9b0db-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9b0db-115">Recommended action</span></span>

<span data-ttu-id="9b0db-116">搜索 的終結點中繼資料`IAllowAnonymous`。</span><span class="sxs-lookup"><span data-stu-id="9b0db-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="9b0db-117">例如：</span><span class="sxs-lookup"><span data-stu-id="9b0db-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="9b0db-118">此技術的示例[見於此 HasAllow 匿名方法](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)。</span><span class="sxs-lookup"><span data-stu-id="9b0db-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="9b0db-119">類別</span><span class="sxs-lookup"><span data-stu-id="9b0db-119">Category</span></span>

<span data-ttu-id="9b0db-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9b0db-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9b0db-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9b0db-121">Affected APIs</span></span>

<span data-ttu-id="9b0db-122">None</span><span class="sxs-lookup"><span data-stu-id="9b0db-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

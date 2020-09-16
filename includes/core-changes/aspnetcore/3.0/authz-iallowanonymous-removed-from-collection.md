---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901913"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 中移除。篩選器

從 ASP.NET Core 3.0 起，MVC 不會為在控制器和動作方法上探索到的[[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute)屬性新增[AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) 。 這項變更會在本機針對衍生的進行定址 <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute> ，但它是和實作為的重大變更 <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> 。 當需要設定和相依性插入時，在 [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) 屬性中包裝的這類實作為一種可達成強型別屬性型授權的 [常用](https://stackoverflow.com/a/41348219/608220) 和支援方法。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> 出現在 [AuthorizationFilterCoNtext。篩選](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) 集合中。 對介面的存在情況進行測試，是覆寫或停用個別控制器方法上篩選的有效方法。

#### <a name="new-behavior"></a>新的行為

`IAllowAnonymous` 不會再出現在 `AuthorizationFilterContext.Filters` 集合中。 `IAsyncAuthorizationFilter` 相依于舊行為的相依通常會導致間歇性的 HTTP 401 未經授權或 HTTP 403 禁止的回應。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 3.0 中引進了新的端點路由策略。

#### <a name="recommended-action"></a>建議的動作

搜尋的端點中繼資料 `IAllowAnonymous` 。 例如：

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

這個 [HasAllowAnonymous 方法](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)會顯示這項技術的範例。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->

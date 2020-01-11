---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901913"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 移除。篩選

從 ASP.NET Core 3.0，MVC 不會針對在控制器和動作方法上探索到的[[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute)屬性加入[AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) 。 這項變更是針對 <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>的衍生性而在本機處理，但對於 <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> 和 <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> 的執行而言，這是一項重大變更。 包裝在[[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute)屬性中的這類執行，是在需要設定和相依性插入時，用來達成強型別、以屬性為基礎之授權的[常用](https://stackoverflow.com/a/41348219/608220)和支援方式。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> 會出現在[AuthorizationFilterCoNtext 中。](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) 測試介面的目前狀態是一種有效的方法，可覆寫或停用個別控制器方法上的篩選準則。

#### <a name="new-behavior"></a>新的行為

`IAllowAnonymous` 不會再出現在 `AuthorizationFilterContext.Filters` 集合中。 相依于舊行為的 `IAsyncAuthorizationFilter` 實，通常會造成間歇性的 HTTP 401 未經授權或 HTTP 403 禁止的回應。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 3.0 引進了新的端點路由策略。

#### <a name="recommended-action"></a>建議的動作

搜尋端點中繼資料中的 `IAllowAnonymous`。 例如：

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

這項技術的範例可在[此 HasAllowAnonymous 方法](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)中找到。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!--

#### Affected APIs

Not detectable via API analysis

-->

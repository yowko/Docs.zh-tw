---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901913"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>授權：從授權篩選器上下文中刪除 IAllowAnonymous。篩檢程式

從 ASP.NET Core 3.0 起，MVC 不會為在控制器和操作方法上發現的[[允許匿名]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute)屬性添加[允許匿名篩選器](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter)。 此更改在本地針對 的衍生工具<xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>進行處理，但它是 和<xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter><xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter>實現的一個重大更改。 在[[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute)屬性中包裝的此類實現是一種[流行](https://stackoverflow.com/a/41348219/608220)且受支援的方式，用於在需要配置和依賴項注入時實現強型別、基於屬性的授權。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>出現在[授權篩選器上下文.篩選器集合中](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A)。 測試介面的存在是重寫或禁用單個控制器方法上的篩選器的有效方法。

#### <a name="new-behavior"></a>新的行為

`IAllowAnonymous`不再出現在集合中`AuthorizationFilterContext.Filters`。 `IAsyncAuthorizationFilter`依賴于舊行為的實現通常會導致間歇性 HTTP 401 未經授權的或 HTTP 403 禁止回應。

#### <a name="reason-for-change"></a>更改原因

在 ASP.NET Core 3.0 中引入了新的端點路由策略。

#### <a name="recommended-action"></a>建議的動作

搜索 的終結點中繼資料`IAllowAnonymous`。 例如：

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

此技術的示例[見於此 HasAllow 匿名方法](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!--

#### Affected APIs

Not detectable via API analysis

-->

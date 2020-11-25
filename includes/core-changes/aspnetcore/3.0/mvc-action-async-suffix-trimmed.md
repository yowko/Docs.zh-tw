---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032389"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC：從控制器動作名稱中修剪的非同步尾碼

在定址 [dotnet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849)的過程中，ASP.NET Core MVC 預設會修剪 `Async` 動作名稱的尾碼。 從 ASP.NET Core 3.0 開始，這項變更會影響路由和連結產生。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

請考慮下列 ASP.NET Core MVC 控制器：

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

動作可透過路由傳送 `Product/ListAsync` 。 連結產生需要指定 `Async` 尾碼。 例如：

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>新的行為

在 ASP.NET Core 3.0 中，動作可透過進行路由傳送 `Product/List` 。 連結產生程式碼應該省略 `Async` 尾碼。 例如：

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

此變更不會影響使用屬性指定的名稱 `[ActionName]` 。 您可以在中將設定為，以停用新的行為 `MvcOptions.SuppressAsyncSuffixInActionNames` `false` `Startup.ConfigureServices` ：

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>變更的原因

依照慣例，非同步 .NET 方法的尾碼為 `Async` 。 不過，當方法定義 MVC 動作時，不需要使用 `Async` 尾碼。

#### <a name="recommended-action"></a>建議的動作

如果您的應用程式相依于保留名稱尾碼的 MVC 動作 `Async` ，請選擇下列其中一個緩和措施：

- 您 `[ActionName]` 可以使用屬性來保留原始名稱。
- 將設定為，以完全停用重新命名 `MvcOptions.SuppressAsyncSuffixInActionNames` `false` `Startup.ConfigureServices` ：

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

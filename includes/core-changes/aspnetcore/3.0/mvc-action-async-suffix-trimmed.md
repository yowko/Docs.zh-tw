---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901853"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC：從控制器動作名稱修剪的非同步尾碼

作為定址[dotnet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849)的一部分，ASP.NET Core MVC 預設會修剪動作名稱 `Async` 的尾碼。 從 ASP.NET Core 3.0 開始，這項變更會影響路由和連結產生。

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

動作可透過 `Product/ListAsync`路由傳送。 連結產生需要指定 `Async` 尾碼。 例如：

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>新的行為

在 ASP.NET Core 3.0 中，動作可透過 `Product/List`路由傳送。 連結產生程式碼應省略 `Async` 尾碼。 例如：

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

這種變更不會影響使用 `[ActionName]` 屬性指定的名稱。 將 `MvcOptions.SuppressAsyncSuffixInActionNames` 設定為 `Startup.ConfigureServices`中的 `false`，即可停用新的行為：

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>變更的原因

依照慣例，非同步 .NET 方法會加上 `Async`的尾碼。 不過，當方法定義 MVC 動作時，不需要使用 `Async` 尾碼。

#### <a name="recommended-action"></a>建議的動作

如果您的應用程式相依于 MVC 動作，保留名稱的 `Async` 尾碼，請選擇下列其中一個緩和措施：

- 使用 `[ActionName]` 屬性來保留原始名稱。
- 將 `Startup.ConfigureServices`中的 `MvcOptions.SuppressAsyncSuffixInActionNames` 設定為 `false`，以完全停用重新命名：

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

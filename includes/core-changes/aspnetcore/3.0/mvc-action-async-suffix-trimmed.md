---
ms.openlocfilehash: 503d61cb86c83e2f32ad40c60a127ae255ef71b0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198382"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC：從控制器動作名稱修剪的非同步尾碼

在定址[aspnet/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849)的過程中，ASP.NET Core MVC 預設會根據動作名稱修剪尾碼 `Async`。 從 ASP.NET Core 3.0 開始，這項變更會影響路由和連結產生。

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

此動作可透過 `Product/ListAsync` 來路由傳送。 連結產生需要指定 `Async` 尾碼。 例如:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>新的行為

在 ASP.NET Core 3.0 中，動作可透過 `Product/List` 來路由傳送。 連結產生程式碼應省略 `Async` 尾碼。 例如:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

這種變更不會影響使用 `[ActionName]` 屬性指定的名稱。 在 `Startup.ConfigureServices` 中，將 `MvcOptions.SuppressAsyncSuffixInActionNames` 設定為 `false`，即可停用新的行為：

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>變更的原因

依照慣例，非同步 .NET 方法會加上 `Async` 的尾碼。 不過，當方法定義 MVC 動作時，不需要使用 `Async` 尾碼。

#### <a name="recommended-action"></a>建議的動作

如果您的應用程式相依于 MVC 動作，並保留名稱的 `Async` 尾碼，請選擇下列其中一個緩和措施：

- 使用 `[ActionName]` 屬性來保留原始名稱。
- 在 `Startup.ConfigureServices` 中，將 `MvcOptions.SuppressAsyncSuffixInActionNames` 設定為 `false`，完全停用重新命名：

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

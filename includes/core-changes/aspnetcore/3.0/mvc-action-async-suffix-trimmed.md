---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901853"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC：從控制器操作名稱修剪的非同步尾碼

作為尋[址點網/aspnetcore_4849](https://github.com/dotnet/aspnetcore/issues/4849)的一部分，ASP.NET核心 MVC 預設`Async`從操作名稱中修剪尾碼。 從 ASP.NET 酷 3.0 開始，此更改會影響路由和鏈路生成。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

請考慮以下ASP.NET核心 MVC 控制器：

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

該操作可通過`Product/ListAsync`進行路由。 連結生成需要指定`Async`尾碼。 例如：

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>新的行為

在 ASP.NET 核心 3.0 中，操作`Product/List`可通過 進行路由。 連結生成代碼應省略`Async`尾碼。 例如：

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

此更改不會影響使用 屬性`[ActionName]`指定的名稱。 可以通過`MvcOptions.SuppressAsyncSuffixInActionNames``false`在 中`Startup.ConfigureServices`設置為 來禁用新行為：

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>更改原因

按照慣例，非同步 .NET 方法尾碼與`Async`。 但是，當方法定義 MVC 操作時，不宜使用`Async`尾碼。

#### <a name="recommended-action"></a>建議的動作

如果應用依賴于保留名稱尾碼的`Async`MVC 操作，請選擇以下緩解措施之一：

- 使用`[ActionName]`屬性保留原始名稱。
- 通過在`MvcOptions.SuppressAsyncSuffixInActionNames``false`中`Startup.ConfigureServices`設置為 完全禁用重命名：

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

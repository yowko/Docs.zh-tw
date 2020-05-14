---
ms.openlocfilehash: 52b9caf2d5b3d44c0c6349501dafc371541fdd70
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396343"
---
### <a name="pubternal-apis-removed"></a>已移除 "Pubternal" Api

為了更有效地維護 ASP.NET Core 的公用 API 介面，命名空間中的大部分類型 `*.Internal` （稱為 :::no-loc text="\"pubternal\""::: api）已經變成真正的內部。 這些命名空間中的成員絕不會被支援為公開 Api。 Api 可能會在次要版本中中斷，通常也會發生。 更新至 ASP.NET Core 3.0 時，相依于這些 Api 的程式碼會中斷。

如需詳細資訊，請參閱[dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932)和[dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

受影響的 Api 會以 `public` 存取修飾詞標示，並存在於 `*.Internal` 命名空間中。

#### <a name="new-behavior"></a>新的行為

受影響的 Api 會以 [internal （~/docs/csharp/language-reference/keywords/internal.md）] 存取修飾詞標示，而且無法再由該元件之外的程式碼使用。

#### <a name="reason-for-change"></a>變更的原因

這些 api 的指引 :::no-loc text="\"pubternal\""::: 是：

* 可能會變更，恕不另行通知。
* 不受限於 .NET 原則來防止中斷性變更。

離開 Api `public` （即使是在 `*.Internal` 命名空間中）對客戶造成混淆。

#### <a name="recommended-action"></a>建議的動作

停止使用這些 :::no-loc text="\"pubternal\""::: api。 如果您有關于替代 Api 的問題，請在[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)存放庫中開啟問題。

例如，請考慮 ASP.NET Core 2.2 專案中的下列 HTTP 要求緩衝處理常式代碼。 `EnableRewind`擴充方法存在於 `Microsoft.AspNetCore.Http.Internal` 命名空間中。

```csharp
HttpContext.Request.EnableRewind();
```

在 ASP.NET Core 3.0 專案中，以 `EnableRewind` 擴充方法的呼叫取代呼叫 `EnableBuffering` 。 要求緩衝功能的運作方式與過去相同。 `EnableBuffering`呼叫 now `internal` API。

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

在 `Microsoft.AspNetCore.*` 和 `Microsoft.Extensions.*` 命名空間中，具有 `Internal` 命名空間名稱中區段的所有 api。 例如：

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->

---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902018"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC："公共"類型更改為內部

在 ASP.NET Core 3.0 中，MVC 中的所有"公共"類型都更新`public`為受支援的命名空間中`internal`或根據需要。

#### <a name="change-description"></a>變更描述

在ASP.NET核心中，"公共"型別宣告為`public`，但駐留在`.Internal`尾碼命名空間中。 雖然這些類型的是`public`，但它們沒有支援策略，並且可能會進行重大更改。 遺憾的是，意外使用這些類型很常見，導致這些專案的更改中斷，並限制了維護框架的能力。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

MVC 中的某些類型`public`在`.Internal`命名空間中。 這些類型沒有支援策略，並且可能會進行重大更改。

#### <a name="new-behavior"></a>新的行為

所有此類類型都更新為在受`public`支援的命名空間中或標記為`internal`。

#### <a name="reason-for-change"></a>更改原因

意外使用"pubternal"類型很常見，導致這些專案發生重大更改，並限制了維護框架的能力。

#### <a name="recommended-action"></a>建議的動作

如果您使用的類型已變為真正`public`並且已移動到受支援的新命名空間中，請更新引用以匹配新的命名空間。

如果您使用的類型已標記為`internal`，則需要查找替代類型。 以前"酒吧"類型從未被支援用於公共用途。 如果這些命名空間中的特定類型對應用至關重要，請在[dotnet/aspnetcore 上](https://github.com/dotnet/aspnetcore/issues)提交問題。 可以考慮使請求的類型`public`。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

此更改包括以下命名空間中的類型：

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

<!--

#### Affected APIs

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

-->

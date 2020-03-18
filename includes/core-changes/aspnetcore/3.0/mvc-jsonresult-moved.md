---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901961"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC： JsonResult 移動到微軟.AspNetCore.Mvc.Core

`JsonResult`已移動到程式集`Microsoft.AspNetCore.Mvc.Core`。 此類型曾經在微軟中定義[。](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json) 向大多數使用者添加了`Microsoft.AspNetCore.Mvc.Formatters.Json`程式集級[[TypeForwardedto]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute)屬性以解決此問題。 使用協力廠商庫的應用可能會遇到問題。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 6

#### <a name="old-behavior"></a>舊的行為

使用基於 2.2 的庫的應用成功生成。

#### <a name="new-behavior"></a>新的行為

使用基於 2.2 的庫的應用編譯失敗。 提供了包含以下文本變體的錯誤：

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

有關此類問題的示例，請參閱[dotnet/aspnetcore_7220](https://github.com/dotnet/aspnetcore/issues/7220)。

#### <a name="reason-for-change"></a>更改原因

ASP.NET核心的組成的平臺級更改，如[aspnet/公告#325](https://github.com/aspnet/Announcements/issues/325)所述。

#### <a name="recommended-action"></a>建議的動作

根據 2.2 版本的庫編譯`Microsoft.AspNetCore.Mvc.Formatters.Json`可能需要重新編譯以解決所有消費者的問題。 如果受到影響，請與庫作者聯繫。 請求重新編譯庫以ASP.NET Core 3.0。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->

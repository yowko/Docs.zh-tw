---
ms.openlocfilehash: 96c2a32dd7cca91e965601d715bbd4625bba439a
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811251"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC： JsonResult 已移至 AspNetCore

`JsonResult` 已移至 `Microsoft.AspNetCore.Mvc.Core` 元件。 此類型是用來在 [Microsoft.AspNetCore.Mvc.Formatters.Js](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)中定義。 已將元件層級 [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) 屬性加入至， `Microsoft.AspNetCore.Mvc.Formatters.Json` 以解決大部分使用者的這個問題。 使用協力廠商程式庫的應用程式可能會發生問題。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 6

#### <a name="old-behavior"></a>舊的行為

使用以2.2 為基礎的程式庫的應用程式已成功建立。

#### <a name="new-behavior"></a>新的行為

使用以2.2 為基礎的程式庫的應用程式無法編譯。 提供了包含下列文字變化的錯誤：

```output
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

如需這類問題的範例，請參閱 [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220)。

#### <a name="reason-for-change"></a>變更的原因

以 [aspnet/公告 # 325](https://github.com/aspnet/Announcements/issues/325)所述的 ASP.NET Core 組合的平台層級變更。

#### <a name="recommended-action"></a>建議的動作

針對2.2 版編譯的程式庫 `Microsoft.AspNetCore.Mvc.Formatters.Json` 可能需要重新編譯，以解決所有取用者的問題。 如果受影響，請洽詢程式庫作者。 要求重新編譯程式庫，以 ASP.NET Core 3.0 為目標。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->

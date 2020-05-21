---
ms.openlocfilehash: 1356f3eee5e2d8090d7d96aafc07a19507a1aff1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721782"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC： JsonResult 已移至 AspNetCore. Core

`JsonResult`已移至 `Microsoft.AspNetCore.Mvc.Core` 元件。 這個類型是用來在[AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)中定義。 已將元件層級[[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute)屬性加入至， `Microsoft.AspNetCore.Mvc.Formatters.Json` 以解決大部分使用者的這個問題。 使用協力廠商程式庫的應用程式可能會遇到問題。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 6

#### <a name="old-behavior"></a>舊的行為

已成功使用以2.2 為基礎的程式庫組建應用程式。

#### <a name="new-behavior"></a>新的行為

使用以2.2 為基礎之程式庫的應用程式無法編譯。 提供的錯誤包含下列文字的變化：

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

如需這類問題的範例，請參閱[dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220)。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 組合的平台層級變更，如[aspnet/公告 # 325](https://github.com/aspnet/Announcements/issues/325)所述。

#### <a name="recommended-action"></a>建議的動作

針對2.2 版編譯的程式庫 `Microsoft.AspNetCore.Mvc.Formatters.Json` 可能需要重新編譯，才能解決所有取用者的問題。 如果受影響，請聯絡程式庫作者。 要求重新編譯程式庫至目標 ASP.NET Core 3.0。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->

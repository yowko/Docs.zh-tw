---
ms.openlocfilehash: a9545c66d3873b5114fe66e13c77ddc28e20020e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077601"
---
### <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a>Blazor： ProtectedBrowserStorage 功能已移至共用架構

在 ASP.NET Core 5.0 RC2 版中，此功能已 `ProtectedBrowserStorage` 移至 ASP.NET Core 的共用架構。

#### <a name="version-introduced"></a>引進的版本

5.0 RC2

#### <a name="old-behavior"></a>舊的行為

在 ASP.NET Core 5.0 Preview 8 中，此功能可作為 [AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) 套件的一部分，但是只能在 Blazor WebAssembly 中使用。

在 ASP.NET Core 5.0 RC1 中，此功能是 [AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) 的一部分，可參考 `Microsoft.AspNetCore.App` 共用架構。

#### <a name="new-behavior"></a>新的行為

在 ASP.NET Core 5.0 RC2 中，不再需要 NuGet 套件參考，也無法使用此功能。

#### <a name="reason-for-change"></a>變更的原因

移至共用架構更適合客戶所預期的使用者體驗。

#### <a name="recommended-action"></a>建議的動作

如果從 ASP.NET Core 5.0 RC1 升級，請完成下列步驟：

1. `Microsoft.AspNetCore.Components.ProtectedBrowserStorage`從專案移除套件參考。
1. 將 `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` 取代為 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。
1. 從您的類別中移除對的呼叫 `AddProtectedBrowserStorage` `Startup` 。

如果從 ASP.NET Core 5.0 Preview 8 升級，請完成下列步驟：

1. `Microsoft.AspNetCore.Components.Web.Extensions`從專案移除套件參考。
1. 將 `using Microsoft.AspNetCore.Components.Web.Extensions;` 取代為 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。
1. 從您的類別中移除對的呼叫 `AddProtectedBrowserStorage` `Startup` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->

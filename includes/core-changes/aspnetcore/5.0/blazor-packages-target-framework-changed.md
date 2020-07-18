---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416271"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor： NuGet 套件的目標 framework 已變更

Blazor 3.2 WebAssembly 專案已編譯成以 .NET Standard 2.1 （ `<TargetFramework>netstandard2.1</TargetFramework>` ）為目標。 在 ASP.NET Core 5.0 中，Blazor 伺服器和 Blazor WebAssembly 專案都是以 .NET 5.0 （）為目標 `<TargetFramework>net5.0</TargetFramework>` 。 為了更符合目標 framework 的變更，下列 Blazor 套件不再以 .NET Standard 2.1 為目標：

* [AspNetCore 元件](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [AspNetCore。授權](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [AspNetCore 的表單](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [AspNetCore。 Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [AspNetCore. WebAssembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [AspNetCore. WebAssembly. 驗證](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSInterop](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop. WebAssembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [WebAssembly. Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

如需討論，請參閱 GitHub 問題[dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 7

#### <a name="old-behavior"></a>舊的行為

在 Blazor 3.1 和3.2 中，套件是以 .NET Standard 2.1 和 .NET Core 3.1 為目標。

#### <a name="new-behavior"></a>新的行為

在 ASP.NET Core 5.0 中，套件會以 .NET 5.0 為目標。

#### <a name="reason-for-change"></a>變更的原因

已進行變更，使其更符合 .NET 目標架構的需求。

#### <a name="recommended-action"></a>建議的動作

Blazor 3.2 WebAssembly projects 應以 .NET 5.0 為目標，做為將其套件參考更新為 5. x.x. 的一部分。 參照其中一個封裝的程式庫可以根據其需求，以 .NET 5.0 或多目標為目標。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->

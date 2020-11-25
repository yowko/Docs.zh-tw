---
title: 重大變更： Blazor： NuGet 套件的目標 framework 已變更
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： NuGet 套件的目標 framework 已變更
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5515edc66ff9786f0d8f7e24e5fc28c71502567b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760665"
---
# <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor： NuGet 套件的目標 framework 已變更

Blazor 3.2 WebAssembly 專案已編譯為以 .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`) 為目標。 在 ASP.NET Core 5.0 中，Blazor 伺服器和 Blazor WebAssembly 專案都是以 .NET 5.0 () 為目標 `<TargetFramework>net5.0</TargetFramework>` 。 為了更加符合目標 framework 變更，下列 Blazor 套件不再以 .NET Standard 2.1 為目標：

* [AspNetCore 元件](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [AspNetCore。授權](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [AspNetCore. Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [AspNetCore Web 元件](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [AspNetCore. WebAssembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [AspNetCore. WebAssembly. 驗證](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSInterop](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop. WebAssembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [WebAssembly. Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 7

## <a name="old-behavior"></a>舊的行為

在 Blazor 3.1 和3.2 中，封裝的目標 .NET Standard 2.1 和 .NET Core 3.1。

## <a name="new-behavior"></a>新的行為

在 ASP.NET Core 5.0 中，封裝的目標是 .NET 5.0。

## <a name="reason-for-change"></a>變更的原因

已進行變更，使其更符合 .NET 目標 framework 的需求。

## <a name="recommended-action"></a>建議的動作

Blazor 3.2 WebAssembly 專案在將其套件參考更新為 5. x.x. 時，應以 .NET 5.0 為目標 參考其中一個套件的程式庫可以根據其需求，以 .NET 5.0 或多重目標為目標。

## <a name="affected-apis"></a>受影響的 API

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->

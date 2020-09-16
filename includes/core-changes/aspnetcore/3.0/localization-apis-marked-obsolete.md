---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728344"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>當地語系化： ResourceManagerWithCultureStringLocalizer 和 WithCulture 標示為過時

[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)類別和[WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170)介面成員通常是當地語系化的使用者混淆來源，特別是在建立自己的實作為時 `IStringLocalizer` 。 這些專案可讓使用者印象即「 `IStringLocalizer` 每個語言、每個資源」的實例。 實際上，實例應該只是「每個資源」。 搜尋的語言是 `CultureInfo.CurrentUICulture` 在執行時間決定。 為了消除混淆的來源，在 ASP.NET Core 3.0 Preview 3 中，Api 已標示為過時。 未來的版本將會移除 Api。

如需相關內容，請參閱 [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324)。 如需討論，請參閱 [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

方法未標示為 `Obsolete` 。

#### <a name="new-behavior"></a>新的行為

方法會標示為 `Obsolete` 。

#### <a name="reason-for-change"></a>變更的原因

Api 表示不建議的使用案例。 當地語系化的設計有一些混淆。

#### <a name="recommended-action"></a>建議的動作

建議改用 `ResourceManagerStringLocalizer` 。 讓文化特性由設定 `CurrentCulture` 。 如果這不是選項，請建立並使用 [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)的複本。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

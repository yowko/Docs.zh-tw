---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901872"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>當地語系化：資源管理器具有區域性字串當地語系化器和標記為過時的區域性

[資源管理器與文化StringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)類和["與文化"](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170)介面成員通常是當地語系化使用者感到困惑的根源，尤其是在創建自己的`IStringLocalizer`實現時。 這些專案給使用者的印象是，實例`IStringLocalizer`是"按語言，按資源"。 實際上，實例應僅是"按資源"。 搜索的語言由執行`CultureInfo.CurrentUICulture`時確定。 為了消除混淆源，API 在 ASP.NET 酷 3.0 預覽 3 中標記為過時。 API 將在將來的版本中被刪除。

有關上下文，請參閱[點網/阿斯平核心#3324](https://github.com/dotnet/aspnetcore/issues/3324)。 有關討論，請參閱[點網/阿斯平核心#7756](https://github.com/dotnet/aspnetcore/issues/7756)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

方法未標記為`Obsolete`。

#### <a name="new-behavior"></a>新的行為

方法被標記`Obsolete`。

#### <a name="reason-for-change"></a>更改原因

API 表示不推薦的用例。 當地語系化設計存在混淆。

#### <a name="recommended-action"></a>建議的動作

建議改為使用`ResourceManagerStringLocalizer`。 讓區域性由 設置`CurrentCulture`。 如果這不是一個選項，請創建並使用[資源管理器與文化字串當地語系化器](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)的副本。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

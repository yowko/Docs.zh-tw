---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394141"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>當地語系化：標記為過時的 ResourceManagerWithCultureStringLocalizer 和 WithCulture

[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)類別和[WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170)介面成員通常是當地語系化使用者的混淆來源，特別是在建立自己的 @no__t 2 執行時。 這些專案會讓使用者印象 @no__t 0 實例是「每一語言，每一資源」。 實際上，實例應該只是「每個資源」。 搜尋的語言是在執行時間由 `CultureInfo.CurrentUICulture` 所決定。 為了消除混淆的來源，在 ASP.NET Core 3.0 Preview 3 中，Api 已標示為過時。 Api 將會在未來的版本中移除。

如需相關內容，請參閱[aspnet/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324)。 如需討論，請參閱[aspnet/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

方法未標示為 `Obsolete`。

#### <a name="new-behavior"></a>新的行為

方法會標示 `Obsolete`。

#### <a name="reason-for-change"></a>變更的原因

Api 代表不建議的使用案例。 當地語系化的設計有一些混淆。

#### <a name="recommended-action"></a>建議的動作

建議改用 `ResourceManagerStringLocalizer`。 讓 `CurrentCulture` 設定文化特性。 如果這不是選項，請建立並使用[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)的複本。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->

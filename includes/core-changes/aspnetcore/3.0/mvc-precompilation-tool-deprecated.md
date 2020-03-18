---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901784"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC：預編譯工具已棄用

在 ASP.NET Core 1.1 中，引入了`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`（MVC 預編譯工具）包，以添加對 Razor 檔 *（.cshtml*檔） 發佈時間編譯的支援。 在ASP.NET核心 2.1 中，引入了[Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1)來擴展預編譯工具的功能。 Razor SDK 增加了對 Razor 檔的生成和發佈時間編譯的支援。 SDK 驗證 *.cshtml*檔在生成時間的正確性，同時提高應用啟動時間。 預設情況下，Razor SDK 處於打開狀態，無需手勢即可開始使用它。

在 ASP.NET Core 3.0 中，ASP.NET核心 1.1 時代 MVC 預編譯工具被刪除。 早期包版本將繼續在修補程式版本中接收重要的 Bug 和安全修補程式。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

該`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`包用於預編譯 MVC Razor 視圖。

#### <a name="new-behavior"></a>新的行為

Razor SDK 本機支援此功能。 程式`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`包不再更新。

#### <a name="reason-for-change"></a>更改原因

Razor SDK 提供了更多功能，並在生成時驗證 *.cshtml*檔的正確性。 SDK 還提高了應用啟動時間。

#### <a name="recommended-action"></a>建議的動作

對於ASP.NET Core 2.1 或更高版本的使用者，請更新以使用本機支援在[Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)中預編譯。 如果 Bug 或缺少功能阻止遷移到 Razor SDK，請在[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)上打開問題。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

### Affected APIs

Not detectable via API analysis

-->

---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901784"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC：先行編譯工具已被取代

在 ASP.NET Core 1.1 中，已引進 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` （MVC 先行編譯工具）封裝，以新增對 Razor 檔案（*cshtml*檔案）之發行時間編譯的支援。 在 ASP.NET Core 2.1 中，引進了[RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1)以擴充先行編譯工具的功能。 Razor SDK 新增了 Razor 檔案的組建和發行時間編譯支援。 SDK 會在組建期間驗證 *. cshtml*檔案的正確性，同時改善應用程式啟動時間。 Razor SDK 預設為開啟，而且不需要手勢就可以開始使用它。

在 ASP.NET Core 3.0 中，已移除 ASP.NET Core 1.1 年代 MVC 先行編譯工具。 較舊的套件版本會繼續在修補程式版本中收到重要的錯誤和安全性修正程式。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` 套件是用來預先編譯 MVC Razor views。

#### <a name="new-behavior"></a>新的行為

Razor SDK 原本就支援這種功能。 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` 套件已不再更新。

#### <a name="reason-for-change"></a>變更的原因

Razor SDK 會提供更多功能，並在組建時驗證 *. cshtml*檔案的正確性。 SDK 也會改善應用程式啟動時間。

#### <a name="recommended-action"></a>建議的動作

針對 ASP.NET Core 2.1 或更新版本的使用者，請更新以在[RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)中使用先行編譯的原生支援。 如果 bug 或遺漏功能導致無法遷移至 Razor SDK，請在[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)開啟問題。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

### Affected APIs

Not detectable via API analysis

-->

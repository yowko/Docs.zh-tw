---
ms.openlocfilehash: 641233df165a1c2208a2185f2b6e99077f9a59d3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394017"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC：先行編譯工具已被取代

在 ASP.NET Core 1.1 中，已引進 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` （MVC 先行編譯工具）封裝，以新增對 Razor 檔案（*cshtml*檔案）之發行時間編譯的支援。 在 ASP.NET Core 2.1 中，引進了[RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1)以擴充先行編譯工具的功能。 Razor SDK 新增了 Razor 檔案的組建和發行時間編譯支援。 SDK 會在組建期間驗證 *. cshtml*檔案的正確性，同時改善應用程式啟動時間。 Razor SDK 預設為開啟，而且不需要手勢就可以開始使用它。

在 ASP.NET Core 3.0 中，已移除 ASP.NET Core 1.1 年代 MVC 先行編譯工具。 較舊的套件版本會繼續在修補程式版本中收到重要的錯誤和安全性修正程式。 

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

@No__t 0 封裝是用來預先編譯 MVC Razor views。

#### <a name="new-behavior"></a>新的行為

Razor SDK 原本就支援這種功能。 已不再更新 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` 套件。

#### <a name="reason-for-change"></a>變更的原因

Razor SDK 會提供更多功能，並在組建時驗證 *. cshtml*檔案的正確性。 SDK 也會改善應用程式啟動時間。

#### <a name="recommended-action"></a>建議的動作

針對 ASP.NET Core 2.1 或更新版本的使用者，請更新以在[RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)中使用先行編譯的原生支援。 如果 bug 或遺漏功能導致無法遷移至 Razor SDK，請在[aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues)開啟問題。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

### Affected APIs

Not detectable via API analysis

-->

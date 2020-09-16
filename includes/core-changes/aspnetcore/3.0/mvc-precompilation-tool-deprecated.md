---
ms.openlocfilehash: 8395428e1729a00fc1af72cf53fe689ee95b5fdf
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721730"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC：先行編譯工具已淘汰

在 ASP.NET Core 1.1 中，導入了 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC 預先編譯工具) 封裝，以將 (Razor 檔案的發行時間編譯支援新增至) 的 *cshtml* 檔案。 在 ASP.NET Core 2.1 中引進了 [RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) ，以在先行編譯工具的功能上擴充。 Razor SDK 新增了 Razor 檔案的組建和發行時間編譯支援。 SDK 會在組建階段驗證 *cshtml* 檔案的正確性，同時改善應用程式啟動時間。 Razor SDK 預設為開啟，且不需要手勢即可開始使用。

在 ASP.NET Core 3.0 中，已移除 ASP.NET Core 1.1-紀元 MVC 先行編譯工具。 較舊的套件版本將繼續收到修補程式版本中的重要 bug 和安全性修正程式。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`封裝是用來預先編譯 MVC Razor views。

#### <a name="new-behavior"></a>新的行為

Razor SDK 原本就支援此功能。 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`套件不再更新。

#### <a name="reason-for-change"></a>變更的原因

Razor SDK 提供更多功能，並在組建時驗證 *cshtml* 檔案的正確性。 SDK 也可改善應用程式啟動時間。

#### <a name="recommended-action"></a>建議的動作

針對 ASP.NET Core 2.1 或更新版本的使用者，請更新以在 [RAZOR SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)中使用先行編譯的原生支援。 如果 bug 或遺失的功能無法遷移至 Razor SDK，請在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)開啟問題。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

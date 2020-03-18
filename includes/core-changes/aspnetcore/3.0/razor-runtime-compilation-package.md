---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344287"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor：運行時編譯移動到包

對 Razor 視圖和 Razor 頁面的運行時編譯的支援已移動到單獨的包中。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

運行時編譯可用，無需其他包。

#### <a name="new-behavior"></a>新的行為

該功能已移動到[Microsoft.AspNetCore.Mvc.Razor.運行時編譯](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)包。

以下 API 以前可用於`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`支援運行時編譯。 API 現在可通過`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`提供 。

- `RazorViewEngineOptions.FileProviders` 現在為 `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` 現在為 `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

此外，`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange`已被刪除。 預設情況下，通過引用包啟用檔更改的`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`重新編譯。

#### <a name="reason-for-change"></a>更改原因

此更改對於刪除 ASP.NET核心共用框架對 Roslyn 的依賴是必要的。

#### <a name="recommended-action"></a>建議的動作

需要運行時編譯或重新編譯 Razor 檔的應用應採取以下步驟：

1. 添加對包的`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`引用。
1. 更新專案`Startup.ConfigureServices`的方法以包括對`AddRazorRuntimeCompilation`的調用。 例如：

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

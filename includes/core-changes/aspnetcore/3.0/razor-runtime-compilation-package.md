---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344287"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor：將執行時間編譯移至封裝

Razor views 和 Razor Pages 的執行時間編譯支援已移至不同的封裝。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

執行時間編譯可供使用，而不需要額外的封裝。

#### <a name="new-behavior"></a>新的行為

此功能已移至 AspNetCore。 [microsoft.aspnetcore.mvc.razor.runtimecompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)套件。

以下是先前在 `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` 中提供的 Api，可支援執行時間編譯。 現在可透過 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`取得 Api。

- `RazorViewEngineOptions.FileProviders` 現在為 `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` 現在為 `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

此外，`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` 已移除。 預設會藉由參考 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 封裝來啟用檔案變更的重新編譯。

#### <a name="reason-for-change"></a>變更的原因

必須進行這項變更，才能移除 Roslyn 上的 ASP.NET Core 共用架構相依性。

#### <a name="recommended-action"></a>建議的動作

需要執行時間編譯或重新編譯 Razor 檔案的應用程式應該採取下列步驟：

1. 新增 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 封裝的參考。
1. 更新專案的 `Startup.ConfigureServices` 方法，以包含對 `AddRazorRuntimeCompilation`的呼叫。 例如：

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

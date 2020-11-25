---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032406"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor：執行時間編譯已移至封裝

Razor views 和 Razor Pages 的執行時間編譯支援已移至不同的封裝。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

可以使用執行時間編譯，而不需要額外的封裝。

#### <a name="new-behavior"></a>新的行為

此功能已移至 AspNetCore 的 [>microsoft.aspnetcore.mvc.razor.runtimecompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) 套件。

下列 Api 先前已可 `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` 用於，以支援執行時間編譯。 現在可透過使用 Api `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` 。

- `RazorViewEngineOptions.FileProviders` 現在為 `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` 現在為 `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

此外，已 `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` 移除。 藉由參考封裝，預設會啟用檔案變更的重新編譯 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 。

#### <a name="reason-for-change"></a>變更的原因

必須進行這項變更，才能移除 Roslyn 上的 ASP.NET Core 共用架構相依性。

#### <a name="recommended-action"></a>建議的動作

需要執行時間編譯或重新編譯 Razor 檔案的應用程式應該採取下列步驟：

1. 加入封裝的參考 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 。
1. 更新專案的 `Startup.ConfigureServices` 方法以包含的呼叫 `AddRazorRuntimeCompilation` 。 例如：

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

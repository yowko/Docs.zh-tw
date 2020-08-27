---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957678"
---
### <a name="razor-razortemplateengine-api-removed"></a>Razor：已移除 RazorTemplateEngine API

[RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API 已移除，並取代為 <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> 。

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

您可以建立並使用範本引擎來剖析和產生 Razor 檔案的程式碼。

#### <a name="new-behavior"></a>新的行為

`RazorProjectEngine` 您可以建立和提供與 `RazorTemplateEngine` 剖析和產生 Razor 檔案程式碼相同的資訊類型。 `RazorProjectEngine` 也提供額外層級的設定。

#### <a name="reason-for-change"></a>變更的原因

`RazorTemplateEngine` 太緊密地結合了現有的實施。 當您嘗試正確設定 Razor 剖析/產生管線時，此緊密結合會導致更多問題。

#### <a name="recommended-action"></a>建議的動作

使用 `RazorProjectEngine`，而不是 `RazorTemplateEngine`。 請思考一下下列範例。

##### <a name="create-and-configure-the-razorprojectengine"></a>建立並設定 RazorProjectEngine

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a>產生 Razor 檔案的程式碼

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [RazorTemplateEngineOptions](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->

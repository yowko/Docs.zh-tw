---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032400"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="26338-101">Razor：已移除 RazorTemplateEngine API</span><span class="sxs-lookup"><span data-stu-id="26338-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="26338-102">[RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API 已移除，並取代為 <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> 。</span><span class="sxs-lookup"><span data-stu-id="26338-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="26338-103">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215)。</span><span class="sxs-lookup"><span data-stu-id="26338-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="26338-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="26338-104">Version introduced</span></span>

<span data-ttu-id="26338-105">3.0</span><span class="sxs-lookup"><span data-stu-id="26338-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="26338-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="26338-106">Old behavior</span></span>

<span data-ttu-id="26338-107">您可以建立並使用範本引擎來剖析和產生 Razor 檔案的程式碼。</span><span class="sxs-lookup"><span data-stu-id="26338-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="26338-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="26338-108">New behavior</span></span>

<span data-ttu-id="26338-109">`RazorProjectEngine` 您可以建立和提供與 `RazorTemplateEngine` 剖析和產生 Razor 檔案程式碼相同的資訊類型。</span><span class="sxs-lookup"><span data-stu-id="26338-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="26338-110">`RazorProjectEngine` 也提供額外層級的設定。</span><span class="sxs-lookup"><span data-stu-id="26338-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="26338-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="26338-111">Reason for change</span></span>

<span data-ttu-id="26338-112">`RazorTemplateEngine` 太緊密地結合了現有的實施。</span><span class="sxs-lookup"><span data-stu-id="26338-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="26338-113">當您嘗試正確設定 Razor 剖析/產生管線時，此緊密結合會導致更多問題。</span><span class="sxs-lookup"><span data-stu-id="26338-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="26338-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="26338-114">Recommended action</span></span>

<span data-ttu-id="26338-115">使用 `RazorProjectEngine`，而不是 `RazorTemplateEngine`。</span><span class="sxs-lookup"><span data-stu-id="26338-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="26338-116">請思考一下下列範例。</span><span class="sxs-lookup"><span data-stu-id="26338-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="26338-117">建立並設定 RazorProjectEngine</span><span class="sxs-lookup"><span data-stu-id="26338-117">Create and configure the RazorProjectEngine</span></span>

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

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="26338-118">產生 Razor 檔案的程式碼</span><span class="sxs-lookup"><span data-stu-id="26338-118">Generate code for a Razor file</span></span>

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

#### <a name="category"></a><span data-ttu-id="26338-119">類別</span><span class="sxs-lookup"><span data-stu-id="26338-119">Category</span></span>

<span data-ttu-id="26338-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="26338-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="26338-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="26338-121">Affected APIs</span></span>

- [<span data-ttu-id="26338-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="26338-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="26338-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="26338-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->

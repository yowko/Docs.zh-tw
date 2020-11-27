---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032406"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="acc5d-101">Razor：執行時間編譯已移至封裝</span><span class="sxs-lookup"><span data-stu-id="acc5d-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="acc5d-102">Razor views 和 Razor Pages 的執行時間編譯支援已移至不同的封裝。</span><span class="sxs-lookup"><span data-stu-id="acc5d-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="acc5d-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="acc5d-103">Version introduced</span></span>

<span data-ttu-id="acc5d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="acc5d-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="acc5d-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="acc5d-105">Old behavior</span></span>

<span data-ttu-id="acc5d-106">可以使用執行時間編譯，而不需要額外的封裝。</span><span class="sxs-lookup"><span data-stu-id="acc5d-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="acc5d-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="acc5d-107">New behavior</span></span>

<span data-ttu-id="acc5d-108">此功能已移至 AspNetCore 的 [>microsoft.aspnetcore.mvc.razor.runtimecompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) 套件。</span><span class="sxs-lookup"><span data-stu-id="acc5d-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="acc5d-109">下列 Api 先前已可 `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` 用於，以支援執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="acc5d-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="acc5d-110">現在可透過使用 Api `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` 。</span><span class="sxs-lookup"><span data-stu-id="acc5d-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="acc5d-111">`RazorViewEngineOptions.FileProviders` 現在為 `MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="acc5d-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="acc5d-112">`RazorViewEngineOptions.AdditionalCompilationReferences` 現在為 `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="acc5d-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="acc5d-113">此外，已 `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` 移除。</span><span class="sxs-lookup"><span data-stu-id="acc5d-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="acc5d-114">藉由參考封裝，預設會啟用檔案變更的重新編譯 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 。</span><span class="sxs-lookup"><span data-stu-id="acc5d-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="acc5d-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="acc5d-115">Reason for change</span></span>

<span data-ttu-id="acc5d-116">必須進行這項變更，才能移除 Roslyn 上的 ASP.NET Core 共用架構相依性。</span><span class="sxs-lookup"><span data-stu-id="acc5d-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="acc5d-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="acc5d-117">Recommended action</span></span>

<span data-ttu-id="acc5d-118">需要執行時間編譯或重新編譯 Razor 檔案的應用程式應該採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="acc5d-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="acc5d-119">加入封裝的參考 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 。</span><span class="sxs-lookup"><span data-stu-id="acc5d-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="acc5d-120">更新專案的 `Startup.ConfigureServices` 方法以包含的呼叫 `AddRazorRuntimeCompilation` 。</span><span class="sxs-lookup"><span data-stu-id="acc5d-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="acc5d-121">例如：</span><span class="sxs-lookup"><span data-stu-id="acc5d-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="acc5d-122">類別</span><span class="sxs-lookup"><span data-stu-id="acc5d-122">Category</span></span>

<span data-ttu-id="acc5d-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="acc5d-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="acc5d-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="acc5d-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

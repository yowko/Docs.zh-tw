---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344287"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="01abd-101">Razor：將執行時間編譯移至封裝</span><span class="sxs-lookup"><span data-stu-id="01abd-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="01abd-102">Razor views 和 Razor Pages 的執行時間編譯支援已移至不同的封裝。</span><span class="sxs-lookup"><span data-stu-id="01abd-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01abd-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="01abd-103">Version introduced</span></span>

<span data-ttu-id="01abd-104">3.0</span><span class="sxs-lookup"><span data-stu-id="01abd-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="01abd-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="01abd-105">Old behavior</span></span>

<span data-ttu-id="01abd-106">執行時間編譯可供使用，而不需要額外的封裝。</span><span class="sxs-lookup"><span data-stu-id="01abd-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="01abd-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="01abd-107">New behavior</span></span>

<span data-ttu-id="01abd-108">此功能已移至 AspNetCore。 [microsoft.aspnetcore.mvc.razor.runtimecompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)套件。</span><span class="sxs-lookup"><span data-stu-id="01abd-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="01abd-109">以下是先前在 `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` 中提供的 Api，可支援執行時間編譯。</span><span class="sxs-lookup"><span data-stu-id="01abd-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="01abd-110">現在可透過 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`取得 Api。</span><span class="sxs-lookup"><span data-stu-id="01abd-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="01abd-111">`RazorViewEngineOptions.FileProviders` 現在為 `MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="01abd-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="01abd-112">`RazorViewEngineOptions.AdditionalCompilationReferences` 現在為 `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="01abd-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="01abd-113">此外，`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` 已移除。</span><span class="sxs-lookup"><span data-stu-id="01abd-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="01abd-114">預設會藉由參考 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 封裝來啟用檔案變更的重新編譯。</span><span class="sxs-lookup"><span data-stu-id="01abd-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="01abd-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="01abd-115">Reason for change</span></span>

<span data-ttu-id="01abd-116">必須進行這項變更，才能移除 Roslyn 上的 ASP.NET Core 共用架構相依性。</span><span class="sxs-lookup"><span data-stu-id="01abd-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01abd-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="01abd-117">Recommended action</span></span>

<span data-ttu-id="01abd-118">需要執行時間編譯或重新編譯 Razor 檔案的應用程式應該採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="01abd-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="01abd-119">新增 `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` 封裝的參考。</span><span class="sxs-lookup"><span data-stu-id="01abd-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="01abd-120">更新專案的 `Startup.ConfigureServices` 方法，以包含對 `AddRazorRuntimeCompilation`的呼叫。</span><span class="sxs-lookup"><span data-stu-id="01abd-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="01abd-121">例如：</span><span class="sxs-lookup"><span data-stu-id="01abd-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="01abd-122">分類</span><span class="sxs-lookup"><span data-stu-id="01abd-122">Category</span></span>

<span data-ttu-id="01abd-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="01abd-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01abd-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="01abd-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

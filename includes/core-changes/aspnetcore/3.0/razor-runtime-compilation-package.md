---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344287"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="a91ac-101">Razor：運行時編譯移動到包</span><span class="sxs-lookup"><span data-stu-id="a91ac-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="a91ac-102">對 Razor 視圖和 Razor 頁面的運行時編譯的支援已移動到單獨的包中。</span><span class="sxs-lookup"><span data-stu-id="a91ac-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a91ac-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="a91ac-103">Version introduced</span></span>

<span data-ttu-id="a91ac-104">3.0</span><span class="sxs-lookup"><span data-stu-id="a91ac-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a91ac-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="a91ac-105">Old behavior</span></span>

<span data-ttu-id="a91ac-106">運行時編譯可用，無需其他包。</span><span class="sxs-lookup"><span data-stu-id="a91ac-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a91ac-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="a91ac-107">New behavior</span></span>

<span data-ttu-id="a91ac-108">該功能已移動到[Microsoft.AspNetCore.Mvc.Razor.運行時編譯](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)包。</span><span class="sxs-lookup"><span data-stu-id="a91ac-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="a91ac-109">以下 API 以前可用於`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`支援運行時編譯。</span><span class="sxs-lookup"><span data-stu-id="a91ac-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="a91ac-110">API 現在可通過`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`提供 。</span><span class="sxs-lookup"><span data-stu-id="a91ac-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="a91ac-111">`RazorViewEngineOptions.FileProviders` 現在為 `MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="a91ac-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="a91ac-112">`RazorViewEngineOptions.AdditionalCompilationReferences` 現在為 `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="a91ac-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="a91ac-113">此外，`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange`已被刪除。</span><span class="sxs-lookup"><span data-stu-id="a91ac-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="a91ac-114">預設情況下，通過引用包啟用檔更改的`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`重新編譯。</span><span class="sxs-lookup"><span data-stu-id="a91ac-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a91ac-115">更改原因</span><span class="sxs-lookup"><span data-stu-id="a91ac-115">Reason for change</span></span>

<span data-ttu-id="a91ac-116">此更改對於刪除 ASP.NET核心共用框架對 Roslyn 的依賴是必要的。</span><span class="sxs-lookup"><span data-stu-id="a91ac-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a91ac-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a91ac-117">Recommended action</span></span>

<span data-ttu-id="a91ac-118">需要運行時編譯或重新編譯 Razor 檔的應用應採取以下步驟：</span><span class="sxs-lookup"><span data-stu-id="a91ac-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="a91ac-119">添加對包的`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`引用。</span><span class="sxs-lookup"><span data-stu-id="a91ac-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="a91ac-120">更新專案`Startup.ConfigureServices`的方法以包括對`AddRazorRuntimeCompilation`的調用。</span><span class="sxs-lookup"><span data-stu-id="a91ac-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="a91ac-121">例如：</span><span class="sxs-lookup"><span data-stu-id="a91ac-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="a91ac-122">類別</span><span class="sxs-lookup"><span data-stu-id="a91ac-122">Category</span></span>

<span data-ttu-id="a91ac-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a91ac-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a91ac-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a91ac-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

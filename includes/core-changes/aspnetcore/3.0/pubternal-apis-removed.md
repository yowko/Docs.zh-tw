---
ms.openlocfilehash: 224cd3c7897c64ef05baba7d3d31dbe5ac0dd610
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606270"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="1320e-101">已移除 "Pubternal" Api</span><span class="sxs-lookup"><span data-stu-id="1320e-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="1320e-102">為了更妥善維護 ASP.NET Core 的公用 API 介面，命名空間中的大部分類型 `*.Internal` (稱為 :::no-loc text="\"pubternal\""::: api) 已成為真正的內部。</span><span class="sxs-lookup"><span data-stu-id="1320e-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="1320e-103">這些命名空間中的成員絕對不能被支援為公眾對應的 Api。</span><span class="sxs-lookup"><span data-stu-id="1320e-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="1320e-104">Api 可能會在次要版本中中斷，且通常會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="1320e-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="1320e-105">更新為 ASP.NET Core 3.0 時，相依于這些 Api 的程式碼會中斷。</span><span class="sxs-lookup"><span data-stu-id="1320e-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="1320e-106">如需詳細資訊，請參閱 [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) 和 [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312)。</span><span class="sxs-lookup"><span data-stu-id="1320e-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1320e-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1320e-107">Version introduced</span></span>

<span data-ttu-id="1320e-108">3.0</span><span class="sxs-lookup"><span data-stu-id="1320e-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1320e-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1320e-109">Old behavior</span></span>

<span data-ttu-id="1320e-110">受影響的 Api 會以 `public` 存取修飾詞標示，並存在於 `*.Internal` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1320e-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1320e-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="1320e-111">New behavior</span></span>

<span data-ttu-id="1320e-112">受影響的 Api 會標示 [內部](../../../../docs/csharp/language-reference/keywords/internal.md) 存取修飾詞，且不會再由該元件之外的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="1320e-112">The affected APIs are marked with the [internal](../../../../docs/csharp/language-reference/keywords/internal.md) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1320e-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="1320e-113">Reason for change</span></span>

<span data-ttu-id="1320e-114">這些 api 的指導方針 :::no-loc text="\"pubternal\""::: 是：</span><span class="sxs-lookup"><span data-stu-id="1320e-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="1320e-115">可能會變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="1320e-115">Could change without notice.</span></span>
* <span data-ttu-id="1320e-116">不受限於 .NET 原則以防止重大變更。</span><span class="sxs-lookup"><span data-stu-id="1320e-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="1320e-117">`public`即使在命名空間中，仍 (api `*.Internal`) 對客戶感到混淆。</span><span class="sxs-lookup"><span data-stu-id="1320e-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1320e-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1320e-118">Recommended action</span></span>

<span data-ttu-id="1320e-119">停止使用這些 :::no-loc text="\"pubternal\""::: api。</span><span class="sxs-lookup"><span data-stu-id="1320e-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="1320e-120">如果您有關于替代 Api 的問題，請在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) 存放庫中開啟問題。</span><span class="sxs-lookup"><span data-stu-id="1320e-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="1320e-121">例如，請考慮 ASP.NET Core 2.2 專案中的下列 HTTP 要求緩衝程式碼。</span><span class="sxs-lookup"><span data-stu-id="1320e-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="1320e-122">`EnableRewind`擴充方法存在於 `Microsoft.AspNetCore.Http.Internal` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1320e-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="1320e-123">在 ASP.NET Core 3.0 專案中， `EnableRewind` 使用擴充方法的呼叫來取代呼叫 `EnableBuffering` 。</span><span class="sxs-lookup"><span data-stu-id="1320e-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="1320e-124">要求緩衝功能的運作方式與過去一樣。</span><span class="sxs-lookup"><span data-stu-id="1320e-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="1320e-125">`EnableBuffering` 呼叫 now `internal` API。</span><span class="sxs-lookup"><span data-stu-id="1320e-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="1320e-126">類別</span><span class="sxs-lookup"><span data-stu-id="1320e-126">Category</span></span>

<span data-ttu-id="1320e-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1320e-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1320e-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1320e-128">Affected APIs</span></span>

<span data-ttu-id="1320e-129">和命名空間中的所有 Api `Microsoft.AspNetCore.*` `Microsoft.Extensions.*` 都具有 `Internal` 命名空間名稱中的區段。</span><span class="sxs-lookup"><span data-stu-id="1320e-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="1320e-130">例如：</span><span class="sxs-lookup"><span data-stu-id="1320e-130">For example:</span></span>

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->

---
ms.openlocfilehash: dc9f37ae0cd6eef2c67e62421571290bba1c2233
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394222"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="eb2aa-101">MVC：從控制器動作名稱修剪的非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="eb2aa-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="eb2aa-102">在定址[aspnet/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849)的過程中，ASP.NET Core MVC 預設會根據動作名稱修剪尾碼 `Async`。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-102">As part of addressing [aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="eb2aa-103">從 ASP.NET Core 3.0 開始，這項變更會影響路由和連結產生。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eb2aa-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="eb2aa-104">Version introduced</span></span>

<span data-ttu-id="eb2aa-105">3.0</span><span class="sxs-lookup"><span data-stu-id="eb2aa-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="eb2aa-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="eb2aa-106">Old behavior</span></span>

<span data-ttu-id="eb2aa-107">請考慮下列 ASP.NET Core MVC 控制器：</span><span class="sxs-lookup"><span data-stu-id="eb2aa-107">Consider the following ASP.NET Core MVC controller:</span></span>

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

<span data-ttu-id="eb2aa-108">此動作可透過 `Product/ListAsync` 來路由傳送。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="eb2aa-109">連結產生需要指定 `Async` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="eb2aa-110">例如:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="eb2aa-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="eb2aa-111">New behavior</span></span>

<span data-ttu-id="eb2aa-112">在 ASP.NET Core 3.0 中，動作可透過 `Product/List` 來路由傳送。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="eb2aa-113">連結產生程式碼應省略 `Async` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="eb2aa-114">例如:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="eb2aa-115">這種變更不會影響使用 `[ActionName]` 屬性指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="eb2aa-116">在 `Startup.ConfigureServices` 中，將 `MvcOptions.SuppressAsyncSuffixInActionNames` 設定為 `false`，即可停用新的行為：</span><span class="sxs-lookup"><span data-stu-id="eb2aa-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="eb2aa-117">變更的原因</span><span class="sxs-lookup"><span data-stu-id="eb2aa-117">Reason for change</span></span>

<span data-ttu-id="eb2aa-118">依照慣例，非同步 .NET 方法會加上 `Async` 的尾碼。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="eb2aa-119">不過，當方法定義 MVC 動作時，不需要使用 `Async` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eb2aa-120">建議的動作</span><span class="sxs-lookup"><span data-stu-id="eb2aa-120">Recommended action</span></span>

<span data-ttu-id="eb2aa-121">如果您的應用程式相依于 MVC 動作，並保留名稱的 `Async` 尾碼，請選擇下列其中一個緩和措施：</span><span class="sxs-lookup"><span data-stu-id="eb2aa-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="eb2aa-122">使用 `[ActionName]` 屬性來保留原始名稱。</span><span class="sxs-lookup"><span data-stu-id="eb2aa-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="eb2aa-123">在 `Startup.ConfigureServices` 中，將 `MvcOptions.SuppressAsyncSuffixInActionNames` 設定為 `false`，完全停用重新命名：</span><span class="sxs-lookup"><span data-stu-id="eb2aa-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="category"></a><span data-ttu-id="eb2aa-124">分類</span><span class="sxs-lookup"><span data-stu-id="eb2aa-124">Category</span></span>

<span data-ttu-id="eb2aa-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eb2aa-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eb2aa-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="eb2aa-126">Affected APIs</span></span>

<span data-ttu-id="eb2aa-127">無</span><span class="sxs-lookup"><span data-stu-id="eb2aa-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

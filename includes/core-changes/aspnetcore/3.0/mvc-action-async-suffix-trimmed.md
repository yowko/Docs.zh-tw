---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032389"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="bed9f-101">MVC：從控制器動作名稱中修剪的非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="bed9f-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="bed9f-102">在定址 [dotnet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849)的過程中，ASP.NET Core MVC 預設會修剪 `Async` 動作名稱的尾碼。</span><span class="sxs-lookup"><span data-stu-id="bed9f-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="bed9f-103">從 ASP.NET Core 3.0 開始，這項變更會影響路由和連結產生。</span><span class="sxs-lookup"><span data-stu-id="bed9f-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bed9f-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bed9f-104">Version introduced</span></span>

<span data-ttu-id="bed9f-105">3.0</span><span class="sxs-lookup"><span data-stu-id="bed9f-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bed9f-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="bed9f-106">Old behavior</span></span>

<span data-ttu-id="bed9f-107">請考慮下列 ASP.NET Core MVC 控制器：</span><span class="sxs-lookup"><span data-stu-id="bed9f-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="bed9f-108">動作可透過路由傳送 `Product/ListAsync` 。</span><span class="sxs-lookup"><span data-stu-id="bed9f-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="bed9f-109">連結產生需要指定 `Async` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="bed9f-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="bed9f-110">例如：</span><span class="sxs-lookup"><span data-stu-id="bed9f-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="bed9f-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="bed9f-111">New behavior</span></span>

<span data-ttu-id="bed9f-112">在 ASP.NET Core 3.0 中，動作可透過進行路由傳送 `Product/List` 。</span><span class="sxs-lookup"><span data-stu-id="bed9f-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="bed9f-113">連結產生程式碼應該省略 `Async` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="bed9f-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="bed9f-114">例如：</span><span class="sxs-lookup"><span data-stu-id="bed9f-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="bed9f-115">此變更不會影響使用屬性指定的名稱 `[ActionName]` 。</span><span class="sxs-lookup"><span data-stu-id="bed9f-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="bed9f-116">您可以在中將設定為，以停用新的行為 `MvcOptions.SuppressAsyncSuffixInActionNames` `false` `Startup.ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="bed9f-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="bed9f-117">變更的原因</span><span class="sxs-lookup"><span data-stu-id="bed9f-117">Reason for change</span></span>

<span data-ttu-id="bed9f-118">依照慣例，非同步 .NET 方法的尾碼為 `Async` 。</span><span class="sxs-lookup"><span data-stu-id="bed9f-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="bed9f-119">不過，當方法定義 MVC 動作時，不需要使用 `Async` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="bed9f-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bed9f-120">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bed9f-120">Recommended action</span></span>

<span data-ttu-id="bed9f-121">如果您的應用程式相依于保留名稱尾碼的 MVC 動作 `Async` ，請選擇下列其中一個緩和措施：</span><span class="sxs-lookup"><span data-stu-id="bed9f-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="bed9f-122">您 `[ActionName]` 可以使用屬性來保留原始名稱。</span><span class="sxs-lookup"><span data-stu-id="bed9f-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="bed9f-123">將設定為，以完全停用重新命名 `MvcOptions.SuppressAsyncSuffixInActionNames` `false` `Startup.ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="bed9f-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="bed9f-124">類別</span><span class="sxs-lookup"><span data-stu-id="bed9f-124">Category</span></span>

<span data-ttu-id="bed9f-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bed9f-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bed9f-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bed9f-126">Affected APIs</span></span>

<span data-ttu-id="bed9f-127">無</span><span class="sxs-lookup"><span data-stu-id="bed9f-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

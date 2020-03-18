---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901853"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="cf3ec-101">MVC：從控制器操作名稱修剪的非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="cf3ec-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="cf3ec-102">作為尋[址點網/aspnetcore_4849](https://github.com/dotnet/aspnetcore/issues/4849)的一部分，ASP.NET核心 MVC 預設`Async`從操作名稱中修剪尾碼。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="cf3ec-103">從 ASP.NET 酷 3.0 開始，此更改會影響路由和鏈路生成。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cf3ec-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="cf3ec-104">Version introduced</span></span>

<span data-ttu-id="cf3ec-105">3.0</span><span class="sxs-lookup"><span data-stu-id="cf3ec-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cf3ec-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="cf3ec-106">Old behavior</span></span>

<span data-ttu-id="cf3ec-107">請考慮以下ASP.NET核心 MVC 控制器：</span><span class="sxs-lookup"><span data-stu-id="cf3ec-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="cf3ec-108">該操作可通過`Product/ListAsync`進行路由。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="cf3ec-109">連結生成需要指定`Async`尾碼。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="cf3ec-110">例如：</span><span class="sxs-lookup"><span data-stu-id="cf3ec-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="cf3ec-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="cf3ec-111">New behavior</span></span>

<span data-ttu-id="cf3ec-112">在 ASP.NET 核心 3.0 中，操作`Product/List`可通過 進行路由。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="cf3ec-113">連結生成代碼應省略`Async`尾碼。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="cf3ec-114">例如：</span><span class="sxs-lookup"><span data-stu-id="cf3ec-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="cf3ec-115">此更改不會影響使用 屬性`[ActionName]`指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="cf3ec-116">可以通過`MvcOptions.SuppressAsyncSuffixInActionNames``false`在 中`Startup.ConfigureServices`設置為 來禁用新行為：</span><span class="sxs-lookup"><span data-stu-id="cf3ec-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="cf3ec-117">更改原因</span><span class="sxs-lookup"><span data-stu-id="cf3ec-117">Reason for change</span></span>

<span data-ttu-id="cf3ec-118">按照慣例，非同步 .NET 方法尾碼與`Async`。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="cf3ec-119">但是，當方法定義 MVC 操作時，不宜使用`Async`尾碼。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cf3ec-120">建議的動作</span><span class="sxs-lookup"><span data-stu-id="cf3ec-120">Recommended action</span></span>

<span data-ttu-id="cf3ec-121">如果應用依賴于保留名稱尾碼的`Async`MVC 操作，請選擇以下緩解措施之一：</span><span class="sxs-lookup"><span data-stu-id="cf3ec-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="cf3ec-122">使用`[ActionName]`屬性保留原始名稱。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="cf3ec-123">通過在`MvcOptions.SuppressAsyncSuffixInActionNames``false`中`Startup.ConfigureServices`設置為 完全禁用重命名：</span><span class="sxs-lookup"><span data-stu-id="cf3ec-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="cf3ec-124">類別</span><span class="sxs-lookup"><span data-stu-id="cf3ec-124">Category</span></span>

<span data-ttu-id="cf3ec-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cf3ec-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf3ec-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="cf3ec-126">Affected APIs</span></span>

<span data-ttu-id="cf3ec-127">None</span><span class="sxs-lookup"><span data-stu-id="cf3ec-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

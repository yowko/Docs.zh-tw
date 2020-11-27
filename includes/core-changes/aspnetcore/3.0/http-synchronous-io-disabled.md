---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032365"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="d8822-101">HTTP：所有伺服器中的同步 IO 已停用</span><span class="sxs-lookup"><span data-stu-id="d8822-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="d8822-102">從 ASP.NET Core 3.0 開始，預設會停用同步伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="d8822-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d8822-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d8822-103">Change description</span></span>

<span data-ttu-id="d8822-104">`AllowSynchronousIO` 是每部伺服器中的選項，可啟用或停用同步 IO Api `HttpRequest.Body.Read` ，例如、 `HttpResponse.Body.Write` 和 `Stream.Flush` 。</span><span class="sxs-lookup"><span data-stu-id="d8822-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="d8822-105">這些 Api 很久就是執行緒耗盡的來源，而應用程式會停止回應。</span><span class="sxs-lookup"><span data-stu-id="d8822-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="d8822-106">從 ASP.NET Core 3.0 Preview 3 開始，預設會停用這些同步作業。</span><span class="sxs-lookup"><span data-stu-id="d8822-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="d8822-107">受影響的伺服器：</span><span class="sxs-lookup"><span data-stu-id="d8822-107">Affected servers:</span></span>

- <span data-ttu-id="d8822-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="d8822-108">Kestrel</span></span>
- <span data-ttu-id="d8822-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="d8822-109">HttpSys</span></span>
- <span data-ttu-id="d8822-110">IIS 同進程</span><span class="sxs-lookup"><span data-stu-id="d8822-110">IIS in-process</span></span>
- <span data-ttu-id="d8822-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="d8822-111">TestServer</span></span>

<span data-ttu-id="d8822-112">預期的錯誤如下：</span><span class="sxs-lookup"><span data-stu-id="d8822-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="d8822-113">每一部伺服器都有一個 `AllowSynchronousIO` 選項，可控制這個行為，而所有的預設值都是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="d8822-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="d8822-114">也可以根據每個要求覆寫此行為，以暫時降低風險。</span><span class="sxs-lookup"><span data-stu-id="d8822-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="d8822-115">例如：</span><span class="sxs-lookup"><span data-stu-id="d8822-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="d8822-116">如果您 `TextWriter` 在中有或另一個呼叫同步 API 的資料流程遇到問題 `Dispose` ，請改為呼叫新的 `DisposeAsync` api。</span><span class="sxs-lookup"><span data-stu-id="d8822-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="d8822-117">如需討論，請參閱 [dotnet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644)。</span><span class="sxs-lookup"><span data-stu-id="d8822-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d8822-118">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d8822-118">Version introduced</span></span>

<span data-ttu-id="d8822-119">3.0</span><span class="sxs-lookup"><span data-stu-id="d8822-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d8822-120">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d8822-120">Old behavior</span></span>

<span data-ttu-id="d8822-121">`HttpRequest.Body.Read``HttpResponse.Body.Write` `Stream.Flush` 預設允許、和。</span><span class="sxs-lookup"><span data-stu-id="d8822-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d8822-122">新的行為</span><span class="sxs-lookup"><span data-stu-id="d8822-122">New behavior</span></span>

<span data-ttu-id="d8822-123">預設不允許這些同步的 Api：</span><span class="sxs-lookup"><span data-stu-id="d8822-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="d8822-124">預期的錯誤如下：</span><span class="sxs-lookup"><span data-stu-id="d8822-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="d8822-125">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d8822-125">Reason for change</span></span>

<span data-ttu-id="d8822-126">這些同步 Api 很久就是執行緒耗盡的來源，而應用程式會停止回應。</span><span class="sxs-lookup"><span data-stu-id="d8822-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="d8822-127">從 ASP.NET Core 3.0 Preview 3 開始，同步作業預設為停用。</span><span class="sxs-lookup"><span data-stu-id="d8822-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d8822-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d8822-128">Recommended action</span></span>

<span data-ttu-id="d8822-129">使用方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="d8822-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="d8822-130">也可以根據每個要求覆寫此行為，以暫時降低風險。</span><span class="sxs-lookup"><span data-stu-id="d8822-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="d8822-131">類別</span><span class="sxs-lookup"><span data-stu-id="d8822-131">Category</span></span>

<span data-ttu-id="d8822-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d8822-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d8822-133">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d8822-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->

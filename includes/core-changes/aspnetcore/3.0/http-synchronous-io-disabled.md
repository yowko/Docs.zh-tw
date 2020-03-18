---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901776"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="37820-101">HTTP：在所有伺服器上禁用同步 IO</span><span class="sxs-lookup"><span data-stu-id="37820-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="37820-102">從 ASP.NET 酷 3.0 開始，預設情況下禁用同步伺服器操作。</span><span class="sxs-lookup"><span data-stu-id="37820-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="37820-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="37820-103">Change description</span></span>

<span data-ttu-id="37820-104">`AllowSynchronousIO`是每個伺服器中啟用或禁用同步 IO API 的選項，如`HttpRequest.Body.Read` `HttpResponse.Body.Write`。`Stream.Flush`和 。</span><span class="sxs-lookup"><span data-stu-id="37820-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="37820-105">長期以來，這些 API 一直是執行緒不足和應用程式掛起的來源。</span><span class="sxs-lookup"><span data-stu-id="37820-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="37820-106">從 ASP.NET 酷 3.0 預覽 3 中開始，預設情況下將禁用這些同步操作。</span><span class="sxs-lookup"><span data-stu-id="37820-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="37820-107">受影響的伺服器：</span><span class="sxs-lookup"><span data-stu-id="37820-107">Affected servers:</span></span>

- <span data-ttu-id="37820-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="37820-108">Kestrel</span></span>
- <span data-ttu-id="37820-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="37820-109">HttpSys</span></span>
- <span data-ttu-id="37820-110">IIS 在流程中</span><span class="sxs-lookup"><span data-stu-id="37820-110">IIS in-process</span></span>
- <span data-ttu-id="37820-111">測試伺服器</span><span class="sxs-lookup"><span data-stu-id="37820-111">TestServer</span></span>

<span data-ttu-id="37820-112">預期錯誤類似于：</span><span class="sxs-lookup"><span data-stu-id="37820-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="37820-113">每個伺服器都有一`AllowSynchronousIO`個選項，用於控制此行為，並且所有伺服器的預設值現在`false`為 。</span><span class="sxs-lookup"><span data-stu-id="37820-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="37820-114">也可以根據請求重寫該行為作為臨時緩解。</span><span class="sxs-lookup"><span data-stu-id="37820-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="37820-115">例如：</span><span class="sxs-lookup"><span data-stu-id="37820-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="37820-116">如果在 中調用同步`TextWriter`API 的或其他流時遇到問題`Dispose`，請改為調用`DisposeAsync`新的 API。</span><span class="sxs-lookup"><span data-stu-id="37820-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="37820-117">有關討論，請參閱[點網/阿斯平核心#7644](https://github.com/dotnet/aspnetcore/issues/7644)。</span><span class="sxs-lookup"><span data-stu-id="37820-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="37820-118">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="37820-118">Version introduced</span></span>

<span data-ttu-id="37820-119">3.0</span><span class="sxs-lookup"><span data-stu-id="37820-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="37820-120">舊的行為</span><span class="sxs-lookup"><span data-stu-id="37820-120">Old behavior</span></span>

<span data-ttu-id="37820-121">`HttpRequest.Body.Read`，`HttpResponse.Body.Write`預設情況下`Stream.Flush`允許。</span><span class="sxs-lookup"><span data-stu-id="37820-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="37820-122">新的行為</span><span class="sxs-lookup"><span data-stu-id="37820-122">New behavior</span></span>

<span data-ttu-id="37820-123">預設情況下不允許這些同步 API：</span><span class="sxs-lookup"><span data-stu-id="37820-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="37820-124">預期錯誤類似于：</span><span class="sxs-lookup"><span data-stu-id="37820-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="37820-125">更改原因</span><span class="sxs-lookup"><span data-stu-id="37820-125">Reason for change</span></span>

<span data-ttu-id="37820-126">這些同步 API 長期以來一直是執行緒不足和應用程式掛起的來源。</span><span class="sxs-lookup"><span data-stu-id="37820-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="37820-127">從 ASP.NET 酷 3.0 預覽 3 中開始，預設情況下將禁用同步操作。</span><span class="sxs-lookup"><span data-stu-id="37820-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="37820-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="37820-128">Recommended action</span></span>

<span data-ttu-id="37820-129">使用方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="37820-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="37820-130">也可以根據請求重寫該行為作為臨時緩解。</span><span class="sxs-lookup"><span data-stu-id="37820-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="37820-131">類別</span><span class="sxs-lookup"><span data-stu-id="37820-131">Category</span></span>

<span data-ttu-id="37820-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37820-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="37820-133">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="37820-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->

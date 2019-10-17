---
ms.openlocfilehash: ab7c097f6b65d539117e5a6ef38eb67b24695a32
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394203"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="81309-101">HTTP：所有伺服器中的同步 IO 已停用</span><span class="sxs-lookup"><span data-stu-id="81309-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="81309-102">從 ASP.NET Core 3.0 開始，預設會停用同步伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="81309-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81309-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="81309-103">Change description</span></span>

<span data-ttu-id="81309-104">`AllowSynchronousIO` 是每部伺服器中的選項，可啟用或停用同步 IO Api，如 `HttpRequest.Body.Read`、`HttpResponse.Body.Write` 和 `Stream.Flush`。</span><span class="sxs-lookup"><span data-stu-id="81309-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="81309-105">這些 Api 長期以來都是執行緒耗盡和應用程式停止回應的來源。</span><span class="sxs-lookup"><span data-stu-id="81309-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="81309-106">從 ASP.NET Core 3.0 Preview 3 開始，預設會停用這些同步作業。</span><span class="sxs-lookup"><span data-stu-id="81309-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="81309-107">受影響的伺服器：</span><span class="sxs-lookup"><span data-stu-id="81309-107">Affected servers:</span></span>

- <span data-ttu-id="81309-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="81309-108">Kestrel</span></span>
- <span data-ttu-id="81309-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="81309-109">HttpSys</span></span>
- <span data-ttu-id="81309-110">IIS 同進程</span><span class="sxs-lookup"><span data-stu-id="81309-110">IIS in-process</span></span>
- <span data-ttu-id="81309-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="81309-111">TestServer</span></span>

<span data-ttu-id="81309-112">預期的錯誤如下：</span><span class="sxs-lookup"><span data-stu-id="81309-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="81309-113">每一部伺服器都有 `AllowSynchronousIO` 選項可控制此行為，而所有伺服器的預設值現在都會 `false`。</span><span class="sxs-lookup"><span data-stu-id="81309-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="81309-114">您也可以根據每個要求來覆寫此行為，以做為暫時的緩和措施。</span><span class="sxs-lookup"><span data-stu-id="81309-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="81309-115">例如:</span><span class="sxs-lookup"><span data-stu-id="81309-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="81309-116">如果您在 `Dispose` 中 @no__t 或另一個資料流程呼叫同步 API 時遇到問題，請改為呼叫新的 `DisposeAsync` API。</span><span class="sxs-lookup"><span data-stu-id="81309-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="81309-117">如需討論，請參閱[aspnet/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644)。</span><span class="sxs-lookup"><span data-stu-id="81309-117">For discussion, see [aspnet/AspNetCore#7644](https://github.com/aspnet/AspNetCore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81309-118">引進的版本</span><span class="sxs-lookup"><span data-stu-id="81309-118">Version introduced</span></span>

<span data-ttu-id="81309-119">3.0</span><span class="sxs-lookup"><span data-stu-id="81309-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="81309-120">舊的行為</span><span class="sxs-lookup"><span data-stu-id="81309-120">Old behavior</span></span>

<span data-ttu-id="81309-121">預設允許 `HttpRequest.Body.Read`、`HttpResponse.Body.Write` 和 `Stream.Flush`。</span><span class="sxs-lookup"><span data-stu-id="81309-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="81309-122">新的行為</span><span class="sxs-lookup"><span data-stu-id="81309-122">New behavior</span></span>

<span data-ttu-id="81309-123">預設不允許這些同步 Api：</span><span class="sxs-lookup"><span data-stu-id="81309-123">These synchronous APIs are disallowed by default:</span></span> 

<span data-ttu-id="81309-124">預期的錯誤如下：</span><span class="sxs-lookup"><span data-stu-id="81309-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="81309-125">變更的原因</span><span class="sxs-lookup"><span data-stu-id="81309-125">Reason for change</span></span>

<span data-ttu-id="81309-126">這些同步 Api 長期以來都是執行緒耗盡和應用程式停止回應的來源。</span><span class="sxs-lookup"><span data-stu-id="81309-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="81309-127">從 ASP.NET Core 3.0 Preview 3 開始，預設會停用同步作業。</span><span class="sxs-lookup"><span data-stu-id="81309-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81309-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="81309-128">Recommended action</span></span>

<span data-ttu-id="81309-129">使用方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="81309-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="81309-130">您也可以根據每個要求來覆寫此行為，以做為暫時的緩和措施。</span><span class="sxs-lookup"><span data-stu-id="81309-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="81309-131">分類</span><span class="sxs-lookup"><span data-stu-id="81309-131">Category</span></span>

<span data-ttu-id="81309-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="81309-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81309-133">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="81309-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->

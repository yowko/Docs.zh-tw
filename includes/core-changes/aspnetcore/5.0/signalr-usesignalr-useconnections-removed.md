---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291655"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="f92ff-101">SignalR：已移除 UseSignalR 和 UseConnections 方法</span><span class="sxs-lookup"><span data-stu-id="f92ff-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="f92ff-102">在 ASP.NET Core 3.0 中，SignalR 採用了端點路由。</span><span class="sxs-lookup"><span data-stu-id="f92ff-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="f92ff-103">在這項變更中， <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> 、 <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> 和某些相關的方法已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="f92ff-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="f92ff-104">在 ASP.NET Core 5.0 中，已移除這些過時的方法。</span><span class="sxs-lookup"><span data-stu-id="f92ff-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="f92ff-105">如需完整的方法清單，請參閱 [受影響的 api](#affected-apis)。</span><span class="sxs-lookup"><span data-stu-id="f92ff-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="f92ff-106">如需此問題的討論，請參閱 [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082)。</span><span class="sxs-lookup"><span data-stu-id="f92ff-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f92ff-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f92ff-107">Version introduced</span></span>

<span data-ttu-id="f92ff-108">5.0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="f92ff-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f92ff-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="f92ff-109">Old behavior</span></span>

<span data-ttu-id="f92ff-110">您可以使用或方法，在中介軟體管線中註冊 SignalR 中樞和連接處理常式 `UseSignalR` `UseConnections` 。</span><span class="sxs-lookup"><span data-stu-id="f92ff-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f92ff-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="f92ff-111">New behavior</span></span>

<span data-ttu-id="f92ff-112">SignalR 中樞和連接處理常式應該在中 <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> 使用 <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> 和擴充方法來註冊 <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> 。</span><span class="sxs-lookup"><span data-stu-id="f92ff-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f92ff-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="f92ff-113">Reason for change</span></span>

<span data-ttu-id="f92ff-114">舊方法具有未與 ASP.NET Core 中其他路由元件互動的自訂路由邏輯。</span><span class="sxs-lookup"><span data-stu-id="f92ff-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="f92ff-115">在 ASP.NET Core 3.0 中引進了新的一般用途路由系統（稱為端點路由）。</span><span class="sxs-lookup"><span data-stu-id="f92ff-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="f92ff-116">端點路由已啟用 SignalR，可與其他路由元件互動。</span><span class="sxs-lookup"><span data-stu-id="f92ff-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="f92ff-117">切換至此模型可讓使用者瞭解端點路由的所有優點。</span><span class="sxs-lookup"><span data-stu-id="f92ff-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="f92ff-118">因此，舊的方法已移除。</span><span class="sxs-lookup"><span data-stu-id="f92ff-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f92ff-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f92ff-119">Recommended action</span></span>

<span data-ttu-id="f92ff-120">移除 `UseSignalR` `UseConnections` 從專案的方法呼叫或的程式碼 `Startup.Configure` 。</span><span class="sxs-lookup"><span data-stu-id="f92ff-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="f92ff-121">將它取代為 `MapHub` `MapConnectionHandler` 呼叫主體內或的呼叫 `UseEndpoints` 。</span><span class="sxs-lookup"><span data-stu-id="f92ff-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="f92ff-122">例如：</span><span class="sxs-lookup"><span data-stu-id="f92ff-122">For example:</span></span>

<span data-ttu-id="f92ff-123">**舊版程式碼：**</span><span class="sxs-lookup"><span data-stu-id="f92ff-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="f92ff-124">**新程式碼：**</span><span class="sxs-lookup"><span data-stu-id="f92ff-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="f92ff-125">一般情況下，您先前的 `MapHub` 和 `MapConnectionHandler` 呼叫可以直接從的主體傳送 `UseSignalR` 到，而 `UseConnections` `UseEndpoints` 不需要任何變更。</span><span class="sxs-lookup"><span data-stu-id="f92ff-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="f92ff-126">類別</span><span class="sxs-lookup"><span data-stu-id="f92ff-126">Category</span></span>

<span data-ttu-id="f92ff-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f92ff-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f92ff-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f92ff-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->

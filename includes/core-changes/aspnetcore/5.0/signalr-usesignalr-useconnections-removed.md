---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291655"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="5915f-101">信號R：使用信號R和使用連接方法被刪除</span><span class="sxs-lookup"><span data-stu-id="5915f-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="5915f-102">在ASP.NET核心3.0中，SignalR 採用了端點路由。</span><span class="sxs-lookup"><span data-stu-id="5915f-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="5915f-103">作為更改的一部分，<xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>和<xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>以及一些相關方法被標記為過時。</span><span class="sxs-lookup"><span data-stu-id="5915f-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="5915f-104">在ASP.NET Core 5.0 中，刪除了這些過時的方法。</span><span class="sxs-lookup"><span data-stu-id="5915f-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="5915f-105">有關方法的完整清單，請參閱受影響的[API。](#affected-apis)</span><span class="sxs-lookup"><span data-stu-id="5915f-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="5915f-106">有關此問題的討論，請參閱[dotnet/aspnetcore_20082](https://github.com/dotnet/aspnetcore/issues/20082)。</span><span class="sxs-lookup"><span data-stu-id="5915f-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5915f-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="5915f-107">Version introduced</span></span>

<span data-ttu-id="5915f-108">5.0 預覽 3</span><span class="sxs-lookup"><span data-stu-id="5915f-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5915f-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5915f-109">Old behavior</span></span>

<span data-ttu-id="5915f-110">信號R 集線器和連接處理常式可以使用 或`UseSignalR``UseConnections`方法在中介軟體管道中註冊。</span><span class="sxs-lookup"><span data-stu-id="5915f-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5915f-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="5915f-111">New behavior</span></span>

<span data-ttu-id="5915f-112">信號R 集線器和連接處理常式應在<xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A>中使用<xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A>和<xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A>上的<xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>擴充方法在 中註冊。</span><span class="sxs-lookup"><span data-stu-id="5915f-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5915f-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="5915f-113">Reason for change</span></span>

<span data-ttu-id="5915f-114">舊方法具有自訂路由邏輯，該邏輯不與 ASP.NET Core 中的其他路由元件進行交互。</span><span class="sxs-lookup"><span data-stu-id="5915f-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="5915f-115">在ASP.NET Core 3.0 中引入了一個新的通用路由系統，稱為端點路由。</span><span class="sxs-lookup"><span data-stu-id="5915f-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="5915f-116">端點路由使 SignalR 能夠與其他路由元件進行交互。</span><span class="sxs-lookup"><span data-stu-id="5915f-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="5915f-117">切換到此模型可使使用者實現端點路由的全部優勢。</span><span class="sxs-lookup"><span data-stu-id="5915f-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="5915f-118">因此，舊方法已被刪除。</span><span class="sxs-lookup"><span data-stu-id="5915f-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5915f-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5915f-119">Recommended action</span></span>

<span data-ttu-id="5915f-120">刪除調用`UseSignalR`或`UseConnections`從專案`Startup.Configure`方法調用的代碼。</span><span class="sxs-lookup"><span data-stu-id="5915f-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="5915f-121">將其替換為 對`MapHub`的`MapConnectionHandler`調用 正文中的 調用 或`UseEndpoints`， 分別替換為 。</span><span class="sxs-lookup"><span data-stu-id="5915f-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="5915f-122">例如：</span><span class="sxs-lookup"><span data-stu-id="5915f-122">For example:</span></span>

<span data-ttu-id="5915f-123">**舊代碼：**</span><span class="sxs-lookup"><span data-stu-id="5915f-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="5915f-124">**新程式碼：**</span><span class="sxs-lookup"><span data-stu-id="5915f-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="5915f-125">通常，`MapHub`您的以前和`MapConnectionHandler`呼叫可以直接從正文`UseSignalR`轉移到`UseConnections``UseEndpoints`，無需更改。</span><span class="sxs-lookup"><span data-stu-id="5915f-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="5915f-126">類別</span><span class="sxs-lookup"><span data-stu-id="5915f-126">Category</span></span>

<span data-ttu-id="5915f-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5915f-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5915f-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5915f-128">Affected APIs</span></span>

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

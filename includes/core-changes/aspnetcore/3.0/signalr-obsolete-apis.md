---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032425"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="5ae98-101">SignalR： UseSignalR 和 UseConnections 方法已標記為過時</span><span class="sxs-lookup"><span data-stu-id="5ae98-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="5ae98-102">`UseConnections` `UseSignalR` 在 ASP.NET Core 3.0 中，方法和類別和類別 `ConnectionsRouteBuilder` `HubRouteBuilder` 會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="5ae98-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5ae98-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5ae98-103">Version introduced</span></span>

<span data-ttu-id="5ae98-104">3.0</span><span class="sxs-lookup"><span data-stu-id="5ae98-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5ae98-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5ae98-105">Old behavior</span></span>

<span data-ttu-id="5ae98-106">已使用或設定 SignalR 中樞 `UseSignalR` 路由 `UseConnections` 。</span><span class="sxs-lookup"><span data-stu-id="5ae98-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5ae98-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="5ae98-107">New behavior</span></span>

<span data-ttu-id="5ae98-108">設定路由的舊方式已過時，並以端點路由取代。</span><span class="sxs-lookup"><span data-stu-id="5ae98-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5ae98-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="5ae98-109">Reason for change</span></span>

<span data-ttu-id="5ae98-110">中介軟體正在移至新的端點路由系統。</span><span class="sxs-lookup"><span data-stu-id="5ae98-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="5ae98-111">新增中介軟體的舊方法是已過時。</span><span class="sxs-lookup"><span data-stu-id="5ae98-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5ae98-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5ae98-112">Recommended action</span></span>

<span data-ttu-id="5ae98-113">以 `UseEndpoints` 取代 `UseSignalR`：</span><span class="sxs-lookup"><span data-stu-id="5ae98-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="5ae98-114">**舊版程式碼：**</span><span class="sxs-lookup"><span data-stu-id="5ae98-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="5ae98-115">**新程式碼：**</span><span class="sxs-lookup"><span data-stu-id="5ae98-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="5ae98-116">類別</span><span class="sxs-lookup"><span data-stu-id="5ae98-116">Category</span></span>

<span data-ttu-id="5ae98-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5ae98-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5ae98-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5ae98-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->

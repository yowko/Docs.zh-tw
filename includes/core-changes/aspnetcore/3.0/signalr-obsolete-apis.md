---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394465"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="311e2-101">信號R：使用信號R和使用連接方法標記為過時</span><span class="sxs-lookup"><span data-stu-id="311e2-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="311e2-102">方法和`UseConnections``UseSignalR`類`ConnectionsRouteBuilder`，並在`HubRouteBuilder`ASP.NET Core 3.0 中標記為過時。</span><span class="sxs-lookup"><span data-stu-id="311e2-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="311e2-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="311e2-103">Version introduced</span></span>

<span data-ttu-id="311e2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="311e2-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="311e2-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="311e2-105">Old behavior</span></span>

<span data-ttu-id="311e2-106">SignalR 中心路由已使用`UseSignalR``UseConnections`或 配置。</span><span class="sxs-lookup"><span data-stu-id="311e2-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="311e2-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="311e2-107">New behavior</span></span>

<span data-ttu-id="311e2-108">配置路由的舊方法已過時，並替換為終結點路由。</span><span class="sxs-lookup"><span data-stu-id="311e2-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="311e2-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="311e2-109">Reason for change</span></span>

<span data-ttu-id="311e2-110">中介軟體正在移動到新的端點路由系統。</span><span class="sxs-lookup"><span data-stu-id="311e2-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="311e2-111">添加中介軟體的舊方法已經過時了。</span><span class="sxs-lookup"><span data-stu-id="311e2-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="311e2-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="311e2-112">Recommended action</span></span>

<span data-ttu-id="311e2-113">以 `UseEndpoints` 取代 `UseSignalR`：</span><span class="sxs-lookup"><span data-stu-id="311e2-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="311e2-114">**舊代碼：**</span><span class="sxs-lookup"><span data-stu-id="311e2-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="311e2-115">**新程式碼：**</span><span class="sxs-lookup"><span data-stu-id="311e2-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="311e2-116">類別</span><span class="sxs-lookup"><span data-stu-id="311e2-116">Category</span></span>

<span data-ttu-id="311e2-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="311e2-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="311e2-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="311e2-118">Affected APIs</span></span>

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

---
title: 重大變更：已移除 SignalR： UseSignalR 和 UseConnections 方法
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 SignalR： UseSignalR 和 UseConnections 方法已移除
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1b1fce04518e69927cdc1650cc1e19107cc81e3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760466"
---
# <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR：已移除 UseSignalR 和 UseConnections 方法

在 ASP.NET Core 3.0 中，SignalR 採用了端點路由。 在這項變更中， <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> 、 <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> 和某些相關的方法已標示為過時。 在 ASP.NET Core 5.0 中，已移除這些過時的方法。 如需完整的方法清單，請參閱 [受影響的 api](#affected-apis)。

如需此問題的討論，請參閱 [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 3

## <a name="old-behavior"></a>舊的行為

您可以使用或方法，在中介軟體管線中註冊 SignalR 中樞和連接處理常式 `UseSignalR` `UseConnections` 。

## <a name="new-behavior"></a>新的行為

SignalR 中樞和連接處理常式應該在中 <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> 使用 <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> 和擴充方法來註冊 <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> 。

## <a name="reason-for-change"></a>變更的原因

舊方法具有未與 ASP.NET Core 中其他路由元件互動的自訂路由邏輯。 在 ASP.NET Core 3.0 中引進了新的一般用途路由系統（稱為端點路由）。 端點路由已啟用 SignalR，可與其他路由元件互動。 切換至此模型可讓使用者瞭解端點路由的所有優點。 因此，舊的方法已移除。

## <a name="recommended-action"></a>建議的動作

移除 `UseSignalR` `UseConnections` 從專案的方法呼叫或的程式碼 `Startup.Configure` 。 將它取代為 `MapHub` `MapConnectionHandler` 呼叫主體內或的呼叫 `UseEndpoints` 。 例如：

**舊版程式碼：**

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

**新程式碼：**

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

一般情況下，您先前的 `MapHub` 和 `MapConnectionHandler` 呼叫可以直接從的主體傳送 `UseSignalR` 到，而 `UseConnections` `UseEndpoints` 不需要任何變更。

## <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->

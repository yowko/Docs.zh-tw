---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291655"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>信號R：使用信號R和使用連接方法被刪除

在ASP.NET核心3.0中，SignalR 採用了端點路由。 作為更改的一部分，<xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>和<xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>以及一些相關方法被標記為過時。 在ASP.NET Core 5.0 中，刪除了這些過時的方法。 有關方法的完整清單，請參閱受影響的[API。](#affected-apis)

有關此問題的討論，請參閱[dotnet/aspnetcore_20082](https://github.com/dotnet/aspnetcore/issues/20082)。

#### <a name="version-introduced"></a>介紹的版本

5.0 預覽 3

#### <a name="old-behavior"></a>舊的行為

信號R 集線器和連接處理常式可以使用 或`UseSignalR``UseConnections`方法在中介軟體管道中註冊。

#### <a name="new-behavior"></a>新的行為

信號R 集線器和連接處理常式應在<xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A>中使用<xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A>和<xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A>上的<xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>擴充方法在 中註冊。

#### <a name="reason-for-change"></a>更改原因

舊方法具有自訂路由邏輯，該邏輯不與 ASP.NET Core 中的其他路由元件進行交互。 在ASP.NET Core 3.0 中引入了一個新的通用路由系統，稱為端點路由。 端點路由使 SignalR 能夠與其他路由元件進行交互。 切換到此模型可使使用者實現端點路由的全部優勢。 因此，舊方法已被刪除。

#### <a name="recommended-action"></a>建議的動作

刪除調用`UseSignalR`或`UseConnections`從專案`Startup.Configure`方法調用的代碼。 將其替換為 對`MapHub`的`MapConnectionHandler`調用 正文中的 調用 或`UseEndpoints`， 分別替換為 。 例如：

**舊代碼：**

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

通常，`MapHub`您的以前和`MapConnectionHandler`呼叫可以直接從正文`UseSignalR`轉移到`UseConnections``UseEndpoints`，無需更改。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

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

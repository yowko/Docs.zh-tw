---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032419"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR：已移除 HubConnection ResetSendPing 和 ResetTimeout 方法

`ResetSendPing`和 `ResetTimeout` 方法已從 SignalR API 中移除 `HubConnection` 。 這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中已公開。 從 ASP.NET Core 3.0 Preview 4 版開始，將無法使用這些方法。 如需討論，請參閱 [dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

Api 已可供使用。

#### <a name="new-behavior"></a>新的行為

Api 已移除。

#### <a name="reason-for-change"></a>變更的原因

這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中已公開。

#### <a name="recommended-action"></a>建議的動作

請勿使用這些方法。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901918"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR：已移除 HubConnection ResetSendPing 和 ResetTimeout 方法

`ResetSendPing` 和 `ResetTimeout` 方法已從 SignalR `HubConnection` API 移除。 這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中公開。 從 ASP.NET Core 3.0 Preview 4 版本開始，這些方法將無法使用。 如需討論，請參閱[dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

Api 可供使用。

#### <a name="new-behavior"></a>新的行為

Api 已移除。

#### <a name="reason-for-change"></a>變更的原因

這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中公開。

#### <a name="recommended-action"></a>建議的動作

請勿使用這些方法。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

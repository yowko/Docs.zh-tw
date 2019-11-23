---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394022"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR：已移除 HubConnection ResetSendPing 和 ResetTimeout 方法

`ResetSendPing` 和 `ResetTimeout` 方法已從 SignalR `HubConnection` API 移除。 這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中公開。 從 ASP.NET Core 3.0 Preview 4 版本開始，這些方法將無法使用。 如需討論，請參閱[aspnet/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543)。

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

---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901918"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>信號R：已刪除集線器連接重置發送和重置超時方法

和`ResetSendPing``ResetTimeout`方法從 SignalR `HubConnection` API 中刪除。 這些方法最初隻供內部使用，但在ASP.NET核心2.2中公開。 這些方法在ASP.NET酷睿 3.0 預覽版 4 版中不可用。 有關討論，請參閱[點網/阿斯平核心#8543](https://github.com/dotnet/aspnetcore/issues/8543)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

API 可用。

#### <a name="new-behavior"></a>新的行為

將刪除 API。

#### <a name="reason-for-change"></a>更改原因

這些方法最初隻供內部使用，但在ASP.NET核心2.2中公開。

#### <a name="recommended-action"></a>建議的動作

不要使用這些方法。

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

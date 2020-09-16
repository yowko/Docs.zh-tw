---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901617"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR：已取代 HandshakeProtocol SuccessHandshakeData

[HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27)欄位已移除，並以協助程式方法取代，該方法會產生指定特定的成功交握回應 `IHubProtocol` 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`HandshakeProtocol.SuccessHandshakeData` 是 `public static ReadOnlyMemory<byte>` 欄位。

#### <a name="new-behavior"></a>新的行為

`HandshakeProtocol.SuccessHandshakeData` 已由傳回 `static` `GetSuccessfulHandshake(IHubProtocol protocol)` 以指定通訊協定為基礎的方法所取代 `ReadOnlyMemory<byte>` 。

#### <a name="reason-for-change"></a>變更的原因

其他欄位已新增至不是常數的交握 _回應_ ，而且會根據選取的通訊協定而變更。

#### <a name="recommended-action"></a>建議的動作

無。 此類型不是設計用來從使用者程式碼使用。 這是 `public` 可以在 SignalR 伺服器和用戶端之間共用的。 它也可以由以 .NET 撰寫的客戶 SignalR 用戶端使用。 SignalR 的**使用者**應該不會受到這項變更的影響。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->

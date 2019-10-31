---
ms.openlocfilehash: e9278320ee3fdf9e6b89698d187f047c309ea791
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198381"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR： HandshakeProtocol. SuccessHandshakeData 已取代

已移除[HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27)欄位，並將它取代為 helper 方法，以根據特定 `IHubProtocol` 產生成功的交握回應。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`HandshakeProtocol.SuccessHandshakeData` 是 `public static ReadOnlyMemory<byte>` 欄位。

#### <a name="new-behavior"></a>新的行為

`HandshakeProtocol.SuccessHandshakeData` 已由 `static` `GetSuccessfulHandshake(IHubProtocol protocol)` 方法取代，其會根據指定的通訊協定傳回 `ReadOnlyMemory<byte>`。

#### <a name="reason-for-change"></a>變更的原因

其他欄位已新增至不是常數的交握_回應_，而且會根據選取的通訊協定而變更。

#### <a name="recommended-action"></a>建議的動作

無。 此類型不是設計用來從使用者程式碼使用。 它 `public`，因此可以在 SignalR 伺服器與用戶端之間共用。 它也可以由以 .NET 撰寫的客戶 SignalR 用戶端使用。 SignalR 的**使用者**不應該受到這項變更的影響。

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->

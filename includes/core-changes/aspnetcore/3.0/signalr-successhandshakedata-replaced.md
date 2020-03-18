---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901617"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>信號R：握手協定.成功握手資料被替換

["握手協定.成功握手資料"](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27)欄位被刪除，並替換為説明器方法，該方法在給定特定`IHubProtocol`的情況下生成成功的握手回應。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`HandshakeProtocol.SuccessHandshakeData`是一`public static ReadOnlyMemory<byte>`個領域。

#### <a name="new-behavior"></a>新的行為

`HandshakeProtocol.SuccessHandshakeData`已替換為`static``GetSuccessfulHandshake(IHubProtocol protocol)`基於指定協定返回 的方法`ReadOnlyMemory<byte>`。

#### <a name="reason-for-change"></a>更改原因

其他欄位已添加到握手_回應_中，這些欄位是非常量的，並且會根據所選協定進行更改。

#### <a name="recommended-action"></a>建議的動作

無。 此類型不是為從使用者代碼使用而設計的。 它是`public`，因此可以在 SignalR 伺服器和用戶端之間共用。 它也可以由以 .NET 編寫的客戶 SignalR 用戶端使用。 SignalR**的使用者**不應受此更改的影響。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->

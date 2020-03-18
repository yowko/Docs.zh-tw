---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394414"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel：傳輸抽象被刪除並公開

作為遠離"pubternal"API 的一部分，Kestrel 傳輸層 API 作為`Microsoft.AspNetCore.Connections.Abstractions`庫中的公共介面公開。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

- `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions`庫中提供了與傳輸相關的抽象。
- 該`ListenOptions.NoDelay`屬性可用。

#### <a name="new-behavior"></a>新的行為

- 該`IConnectionListener`介面在`Microsoft.AspNetCore.Connections.Abstractions`庫中引入，以公開`...Transport.Abstractions`庫中最常用的功能。
- 現在`NoDelay`可在傳輸選項 （`LibuvTransportOptions`和`SocketTransportOptions`） 中提供 。
- `SchedulingMode`不再可用。

#### <a name="reason-for-change"></a>更改原因

ASP.NET核心 3.0 已遠離"公共"API。

#### <a name="recommended-action"></a>建議的動作

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

### Affected APIs

Not detectable via API analysis

-->

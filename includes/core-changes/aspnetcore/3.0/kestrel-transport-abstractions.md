---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721130"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel：已移除並設為公用的傳輸抽象概念

在離開「pubternal」 Api 的過程中，Kestrel 傳輸層 Api 會公開為程式庫中的公用介面 `Microsoft.AspNetCore.Connections.Abstractions` 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

- 程式庫中提供傳輸相關的抽象概念 `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` 。
- `ListenOptions.NoDelay`屬性可用。

#### <a name="new-behavior"></a>新的行為

- `IConnectionListener`介面是在程式庫中引進 `Microsoft.AspNetCore.Connections.Abstractions` ，用以公開程式庫中最常用的功能 `...Transport.Abstractions` 。
- `NoDelay`現在可在傳輸選項（ `LibuvTransportOptions` 和）中取得 `SocketTransportOptions` 。
- `SchedulingMode`已無法再使用。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 3.0 已從 "pubternal" Api 中移除。

#### <a name="recommended-action"></a>建議的動作

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

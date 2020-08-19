---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557957"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>MulticastOption。群組不接受 null 值

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 不再接受的值 `null` 。 如果您將屬性設定為 `null` ， <xref:System.ArgumentNullException> 就會擲回。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中，您可以將 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 屬性設定為 `null` 。 如果 <xref:System.Net.Sockets.MulticastOption> 稍後傳遞至 <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> ，則執行時間會擲回 <xref:System.NullReferenceException> 。

在 .NET 5.0 和更新版本中， <xref:System.ArgumentNullException> 如果您將屬性設定為，就會擲回 `null` 。

#### <a name="reason-for-change"></a>變更的原因

為了與架構設計指導方針一致，屬性已更新為如果值為，則會擲回 <xref:System.ArgumentNullException> `null` 。

#### <a name="recommended-action"></a>建議的動作

請確定您未將設定 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 為 `null` 。

#### <a name="category"></a>類別

網路功能

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->

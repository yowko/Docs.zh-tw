---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859634"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a>WebClient 地說 cancelasync 不一定會立即取消

從 .NET Core 2.0 開始，如果<xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType>已開始提取回應，呼叫就不會立即取消要求。

#### <a name="change-description"></a>變更描述

先前呼叫<xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType>會立即取消要求。 從 .NET Core 2.0 開始，只有<xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType>在回應尚未開始提取時，呼叫才會立即取消要求。 如果已開始提取回應，則只會在讀取完整的回應之後，才會取消要求。

這項變更已實行， <xref:System.Net.WebClient>因為 API 已淘汰而改用<xref:System.Net.Http.HttpClient>。

#### <a name="version-introduced"></a>引進的版本

2.0

#### <a name="recommended-action"></a>建議的動作

<xref:System.Net.WebClient?displayProperty=fullName>請使用<xref:System.Net.Http.HttpClient?displayProperty=fullName>類別，而不是已被取代的。

#### <a name="category"></a>類別

網路功能

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->

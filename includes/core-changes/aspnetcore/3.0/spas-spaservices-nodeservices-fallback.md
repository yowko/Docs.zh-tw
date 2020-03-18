---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522674"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Spa服務和節點服務不再回退到主控台記錄器

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>並且<xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType>不會顯示主控台日誌，除非配置了日誌記錄。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`Microsoft.AspNetCore.SpaServices`用於`Microsoft.AspNetCore.NodeServices`在未配置日誌記錄時自動創建主控台記錄器。

#### <a name="new-behavior"></a>新的行為

`Microsoft.AspNetCore.SpaServices`並且`Microsoft.AspNetCore.NodeServices`不會顯示主控台日誌，除非配置了日誌記錄。

#### <a name="reason-for-change"></a>更改原因

需要與其他ASP.NET核心包實現日誌記錄的方式保持一致。

#### <a name="recommended-action"></a>建議的動作

如果需要舊行為，要配置主控台日誌記錄，請添加到`services.AddLogging(builder => builder.AddConsole())`方法。 `Setup.ConfigureServices`

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!--

#### Affected APIs

Not detectable via API analysis

-->

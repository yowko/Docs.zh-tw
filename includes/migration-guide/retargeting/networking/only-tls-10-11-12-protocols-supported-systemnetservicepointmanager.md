---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615625"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>在 System.Net.ServicePointManager 和 System.Net.Security.SslStream 只支援 Tls 1.0、1.1 及 1.2 通訊協定

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6 開始，只有 <xref:System.Net.ServicePointManager> 和 <xref:System.Net.Security.SslStream> 類別可以使用 Tls1.0、Tls1.1 或 Tls 1.2 這三種通訊協定之一。 不支援 SSL3.0 通訊協定與 RC4 編碼器。

#### <a name="suggestion"></a>建議

建議的緩和措施是將伺服器端應用程式升級至 Tls1.0、Tls1.1 或 Tls1.2。 如果這並不可行，或是用戶端應用程式已中斷，則可使用 <xref:System.AppContext?displayProperty=fullName> 類別搭配下列兩種方式之一，停用這項功能：

- 以程式設計方式設定上的相容性參數 <xref:System.AppContext?displayProperty=fullName> ，如[這裡](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)所述。
- 將下列程式行加入至 app.config 檔案的 `<runtime>` 區段：

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.6         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>

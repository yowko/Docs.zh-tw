---
ms.openlocfilehash: 5c86be598ab6196ecf4da05451c7f22d2be52c12
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614344"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>ServicePointManager.SecurityProtocol 的預設值是 SecurityProtocolType.System.Default

#### <a name="details"></a>詳細資料

從以 .NET Framework 4.7 為目標的應用程式開始，<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 屬性是 <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>。 這項變更可以讓以 SslStream 為基礎的 .NET Framework 網路 API (例如 FTP、HTTPS 及 SMTP) 繼承作業系統的預設安全性通訊協定，而不要使用由 .NET Framework 定義的硬式編碼值。 預設值會依作業系統和系統管理員執行的任何自訂設定而異。 如需每個 Windows 作業系統版本中預設 SChannel 通訊協定的資訊，請參閱 [Protocols in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-) (TLS/SSL 中的通訊協定 (Schannel SSP))。</p>目標是舊版 .NET Framework 的應用程式，<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 屬性的預設值視目標的 .NET framework 版本而定。 如需詳細資訊，請參閱[從 .NET Framework 4.5.2 移轉到 4.6 的重定目標變更的網路區段](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking)。

#### <a name="suggestion"></a>建議

這項變更會影響目標為 .NET Framework 4.7 或更新版本的應用程式。 如果您偏好使用定義的通訊協定，而不是依賴系統預設，您可以明確設定 <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 屬性的值。 如果不需要這項變更，您可以新增設定至 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段，以退出宣告。 下列範例顯示 `<runtime>` 區段及 `Switch.System.Net.DontEnableSystemDefaultTlsVersions` 選擇退出參數：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSystemDefaultTlsVersions=true" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>

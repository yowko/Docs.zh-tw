---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760202"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>WCF 訊息安全性現在能夠使用 TLS1.1 和 TLS1.2

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.7 開始，除了 SSL3.0 和 TLS1.0 之外，客戶還可以透過應用程式組態設定，在 WCF 訊息安全性設定 TLS1.1 或 TLS1.2。|
|建議|在 .NET Framework 4.7 中，預設會停用 WCF 訊息安全性中的 TLS1.1 和 TLS1.2 支援。 您可以將下行新增到 app.config 或 web.config 檔案的 <code>&lt;runtime&gt;</code> 區段來啟用它：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7|
|類型|正在重定目標|


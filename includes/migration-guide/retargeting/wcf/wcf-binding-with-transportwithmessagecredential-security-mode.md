---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614353"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>使用 TransportWithMessageCredential 安全性模式的 WCF 繫結

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6.1 開始，使用 TransportWithMessageCredential 安全性模式的 WCF 繫結可以設定以接收具有不帶正負號 &quot;to&quot; 標頭的非對稱安全性金鑰訊息。根據預設，不帶正負號的 &quot;to&quot; 標頭會繼續在 .NET Framework 4.6.1 中遭到拒絕。 其只有在應用程式使用 Switch.System.ServiceModel.AllowUnsignedToHeader 組態參數來接受此新的作業模式時才會接受。

#### <a name="suggestion"></a>建議

由於這是可選擇加入的功能，因此不會影響現有應用程式的行為。<br/>若要控制是否使用新的行為，請使用下列組態設定：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 透明 |
| 版本 | 4.6.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>

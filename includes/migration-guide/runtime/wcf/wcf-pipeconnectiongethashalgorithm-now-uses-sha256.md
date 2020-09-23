---
ms.openlocfilehash: 9f5f238e3d4222af1da3a1713e1b3e65de6e6f49
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91025342"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm 現在會使用 SHA256

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7.1 開始，Windows Communication Foundation 會使用 SHA256 雜湊來產生具名管道的隨機名稱。 在 .NET Framework 4.7 和舊版中，它已使用 SHA1 雜湊。

#### <a name="suggestion"></a>建議

如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 `<runtime>` 區段中新增下列程式行來退出變更：

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>
```

| Name    | 值   |
|:--------|:--------|
| 範圍   | Minor   |
| 版本 | 4.7.1   |
| 類型    | 執行階段 |

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->

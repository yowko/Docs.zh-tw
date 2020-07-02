---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614380"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>預設 SignedXML 和 SignedXMS 演算法變更為 SHA256

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7 和更早版本中，某些作業的 SignedXML 和 SignedCMS 預設為 SHA1。從 .NET Framework 4.7.1 開始，針對這些作業預設會啟用 SHA256。 這項變更是必要的，因為 SHA1 不再被視為是安全的方法。

#### <a name="suggestion"></a>建議

有兩個新內容參數值可以控制預設使用 SHA1 (不安全) 還是 SHA256：

- Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms
- Switch.System。UseInsecureHashAlgorithms 適用于以 .NET Framework 4.7.1 和更新版本為目標的應用程式，如果不想使用 SHA256，您可以將下列設定參數新增至您應用程式佈建檔的[runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)區段，將預設值還原為 SHA1：

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

若為以 .NET Framework 4.7.1 和更早版本為目標的應用程式，您可以新增下列設定參數到應用程式設定檔的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，選擇加入此變更：

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>

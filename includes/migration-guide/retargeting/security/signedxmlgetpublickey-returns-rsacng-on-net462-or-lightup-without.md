---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616035"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey RSACng 會在 net462 (或 lightup) 上傳回 RSACng，而無重定目標變更

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6.2 開始，<xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> 方法所傳回的物件具象類型 (毫不奇怪地) 從 CryptoServiceProvider 實作變更為 Cng 實作。 這是因為實作從使用 `certificate.PublicKey.Key` 變更為使用內部 `certificate.GetAnyPublicKey`，它會轉送給 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>。

#### <a name="suggestion"></a>建議

從在 .NET Framework 4.7.1 上執行的應用程式開始，您可以使用 .NET Framework 4.6.1 和更早版本中預設使用的 CryptoServiceProvider 實作，方法是將下列設定參數新增至您應用程式設定檔的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段：

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>

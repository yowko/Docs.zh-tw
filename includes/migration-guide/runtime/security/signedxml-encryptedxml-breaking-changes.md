---
ms.openlocfilehash: 5c8ea3565fbe599dd53a71ba8bd339704f7d7f8a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496399"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml 和 EncryptedXml 重大變更

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 中，<xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> 和 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> 的安全性修正會導致不同的執行階段行為。 例如，<ul><li>如果文件具有包含相同 <code>id</code> 屬性的多個項目，且簽章將目標設為這些項目之一以作為簽章的根項目，該文件現在會視為無效。</li><li>在參考中使用非標準 XPath 轉換演算法的文件現在都視為無效。</li><li>在參考中使用非標準 XSLT 轉換演算法的文件現在會視為無效。</li><li>任何使用外部資源中斷簽章的程式都無法這麼做。</li></ul>

#### <a name="suggestion"></a>建議

開發人員可能想要檢閱 <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> 和 <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>，以及衍生自 <xref:System.Security.Cryptography.Xml.Transform> 之類型的使用方式，因為文件收件者可能無法處理它。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6.2|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.Xml.Transform`
- `T:System.Security.Cryptography.Xml.XmlDsigXPathTransform`
- `T:System.Security.Cryptography.Xml.XmlDsigXsltTransform`

-->

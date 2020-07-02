---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620116"
---
### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT 樣式表例外狀況訊息已變更

#### <a name="details"></a>詳細資料

在 .NET Framework 4.5 中，當 XSLT 檔太複雜時，錯誤訊息的文字為 &quot; 樣式表單太複雜。 &quot;在舊版中，錯誤訊息是「 &quot; XSLT 編譯錯誤」。 &quot;相依于錯誤訊息文字的應用程式代碼將不再有效。 不過，例外狀況類型會保持不變，因此這項變更應該不會產生實際影響。

#### <a name="suggestion"></a>建議

請將依據此錯誤狀況之例外狀況訊息的任何應用程式程式碼更新為預期會有新訊息，或是 (甚至更佳的做法) 將程式碼更新為只依據尚未變更的例外狀況類型 (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>)。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: eafbdd2d42977381fb4d77748a3c9a2595ff2936
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620055"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a>在序列化以無法存取的成員隱藏可存取成員的類型時，XmlSerializer 會失敗

#### <a name="details"></a>詳細資料

序列化衍生的類型時，如果類型包含無法存取的欄位或屬性，而此欄位或屬性隱藏 (透過 'new' 關鍵字) 先前在基底類型上可存取 (例如，公用) 之相同名稱的欄位或屬性，<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 可能會失敗。

#### <a name="suggestion"></a>建議

請使隱藏成員可供 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 存取 (例如，將其設為公開) 來解決這個問題。此外，下列組態設定會還原為 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 行為，以修正此問題：<pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: eafbdd2d42977381fb4d77748a3c9a2595ff2936
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620055"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a><span data-ttu-id="a34e4-101">在序列化以無法存取的成員隱藏可存取成員的類型時，XmlSerializer 會失敗</span><span class="sxs-lookup"><span data-stu-id="a34e4-101">XmlSerializer fails while serializing a type that hides an accessible member with an inaccessible one</span></span>

#### <a name="details"></a><span data-ttu-id="a34e4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a34e4-102">Details</span></span>

<span data-ttu-id="a34e4-103">序列化衍生的類型時，如果類型包含無法存取的欄位或屬性，而此欄位或屬性隱藏 (透過 'new' 關鍵字) 先前在基底類型上可存取 (例如，公用) 之相同名稱的欄位或屬性，<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="a34e4-103">When serializing a derived type, the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> can fail if the type contains an inaccessible field or property that hides (via the 'new' keyword) a field or property of the same name that was previously accessible (public, for example) on the base type.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a34e4-104">建議</span><span class="sxs-lookup"><span data-stu-id="a34e4-104">Suggestion</span></span>

<span data-ttu-id="a34e4-105">請使隱藏成員可供 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 存取 (例如，將其設為公開) 來解決這個問題。此外，下列組態設定會還原為 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 行為，以修正此問題：</span><span class="sxs-lookup"><span data-stu-id="a34e4-105">This problem can be solved by making the new, hiding member accessible to the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (by marking it public, for example).Alternatively, the following config setting will revert to 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> behavior, which will fix the problem:</span></span><pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="a34e4-106">名稱</span><span class="sxs-lookup"><span data-stu-id="a34e4-106">Name</span></span>    | <span data-ttu-id="a34e4-107">值</span><span class="sxs-lookup"><span data-stu-id="a34e4-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a34e4-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="a34e4-108">Scope</span></span>   |<span data-ttu-id="a34e4-109">Minor</span><span class="sxs-lookup"><span data-stu-id="a34e4-109">Minor</span></span>|
|<span data-ttu-id="a34e4-110">版本</span><span class="sxs-lookup"><span data-stu-id="a34e4-110">Version</span></span>|<span data-ttu-id="a34e4-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a34e4-111">4.5</span></span>|
|<span data-ttu-id="a34e4-112">類型</span><span class="sxs-lookup"><span data-stu-id="a34e4-112">Type</span></span>|<span data-ttu-id="a34e4-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="a34e4-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a34e4-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a34e4-114">Affected APIs</span></span>

-<xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType></li></ul>|

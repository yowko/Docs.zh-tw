---
ms.openlocfilehash: fdec6671cbf2dae0d72dfaec07f162058b38cf9d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620112"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a><span data-ttu-id="68a2e-101">XmlTextReader DTD 實體展開限制為 10,000,000 個字元</span><span class="sxs-lookup"><span data-stu-id="68a2e-101">XmlTextReader DTD entity expansion is limited to 10,000,000 characters</span></span>

#### <a name="details"></a><span data-ttu-id="68a2e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="68a2e-102">Details</span></span>

<span data-ttu-id="68a2e-103">DTD 實體展開現在限制為 10,000,000 個字元。</span><span class="sxs-lookup"><span data-stu-id="68a2e-103">DTD entity expansion is now limited to 10,000,000 characters.</span></span> <span data-ttu-id="68a2e-104">載入無 DTD 實體展開或 DTD 實體展開受限的 XML 檔案並不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="68a2e-104">Loading XML files without DTD entity expansion or with limited DTD entity expansion is unaffected.</span></span> <span data-ttu-id="68a2e-105">若檔案具有展開至超過 10,000,000 個字元的 DTD 實體，則會載入失敗，而且現在會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="68a2e-105">Files with DTD entities that expand to more than 10,000,000 characters fail to load, and now throw an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="68a2e-106">建議</span><span class="sxs-lookup"><span data-stu-id="68a2e-106">Suggestion</span></span>

<span data-ttu-id="68a2e-107">如果 DTD 實體展開的限制太低，可以使用 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> 屬性覆寫值 10,000,000。</span><span class="sxs-lookup"><span data-stu-id="68a2e-107">If the limit of DTD entity expansion is too low 10,000,000, the value can be overridden with the <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> property.</span></span> <span data-ttu-id="68a2e-108">具有適當 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> 值的 <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> 可以傳遞至採用 <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (即 <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>) 的 <code>XmlReader.Create</code></span><span class="sxs-lookup"><span data-stu-id="68a2e-108">An <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> with the proper <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> value can be passed to <code>XmlReader.Create</code> that takes <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (ie. <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)</span></span>

| <span data-ttu-id="68a2e-109">名稱</span><span class="sxs-lookup"><span data-stu-id="68a2e-109">Name</span></span>    | <span data-ttu-id="68a2e-110">值</span><span class="sxs-lookup"><span data-stu-id="68a2e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="68a2e-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="68a2e-111">Scope</span></span>   |<span data-ttu-id="68a2e-112">Edge</span><span class="sxs-lookup"><span data-stu-id="68a2e-112">Edge</span></span>|
|<span data-ttu-id="68a2e-113">版本</span><span class="sxs-lookup"><span data-stu-id="68a2e-113">Version</span></span>|<span data-ttu-id="68a2e-114">4.5</span><span class="sxs-lookup"><span data-stu-id="68a2e-114">4.5</span></span>|
|<span data-ttu-id="68a2e-115">類型</span><span class="sxs-lookup"><span data-stu-id="68a2e-115">Type</span></span>|<span data-ttu-id="68a2e-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="68a2e-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="68a2e-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="68a2e-117">Affected APIs</span></span>

-<xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)></li></ul>|

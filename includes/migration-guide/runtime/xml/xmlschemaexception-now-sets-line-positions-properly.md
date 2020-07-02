---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620111"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="029e4-101">XmlSchemaException 現在會正確設定行位置</span><span class="sxs-lookup"><span data-stu-id="029e4-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="029e4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="029e4-102">Details</span></span>

<span data-ttu-id="029e4-103">如果將 <xref:System.Xml.Linq.LoadOptions.SetLineInfo> 值傳遞至 Load 方法且發生驗證錯誤，則 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 屬性現在會包含行資訊。</span><span class="sxs-lookup"><span data-stu-id="029e4-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="029e4-104">建議</span><span class="sxs-lookup"><span data-stu-id="029e4-104">Suggestion</span></span>

<span data-ttu-id="029e4-105">您應該更新假設不會設定 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 的例外狀況處理程式碼，因為當使用 SetLineInfo 載入 XML 時，現在會正確設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="029e4-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="029e4-106">名稱</span><span class="sxs-lookup"><span data-stu-id="029e4-106">Name</span></span>    | <span data-ttu-id="029e4-107">值</span><span class="sxs-lookup"><span data-stu-id="029e4-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="029e4-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="029e4-108">Scope</span></span>   |<span data-ttu-id="029e4-109">Edge</span><span class="sxs-lookup"><span data-stu-id="029e4-109">Edge</span></span>|
|<span data-ttu-id="029e4-110">版本</span><span class="sxs-lookup"><span data-stu-id="029e4-110">Version</span></span>|<span data-ttu-id="029e4-111">4.5</span><span class="sxs-lookup"><span data-stu-id="029e4-111">4.5</span></span>|
|<span data-ttu-id="029e4-112">類型</span><span class="sxs-lookup"><span data-stu-id="029e4-112">Type</span></span>|<span data-ttu-id="029e4-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="029e4-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="029e4-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="029e4-114">Affected APIs</span></span>

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

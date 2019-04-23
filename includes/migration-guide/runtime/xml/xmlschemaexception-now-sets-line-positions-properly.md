---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803455"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="89ad2-101">XmlSchemaException 現在會正確設定行位置</span><span class="sxs-lookup"><span data-stu-id="89ad2-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="89ad2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="89ad2-102">Details</span></span>|<span data-ttu-id="89ad2-103">如果將 <xref:System.Xml.Linq.LoadOptions.SetLineInfo> 值傳遞至 Load 方法且發生驗證錯誤，則 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 屬性現在會包含行資訊。</span><span class="sxs-lookup"><span data-stu-id="89ad2-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="89ad2-104">建議</span><span class="sxs-lookup"><span data-stu-id="89ad2-104">Suggestion</span></span>|<span data-ttu-id="89ad2-105">您應該更新假設不會設定 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 的例外狀況處理程式碼，因為當使用 SetLineInfo 載入 XML 時，現在會正確設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="89ad2-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="89ad2-106">範圍</span><span class="sxs-lookup"><span data-stu-id="89ad2-106">Scope</span></span>|<span data-ttu-id="89ad2-107">Edge</span><span class="sxs-lookup"><span data-stu-id="89ad2-107">Edge</span></span>|
|<span data-ttu-id="89ad2-108">版本</span><span class="sxs-lookup"><span data-stu-id="89ad2-108">Version</span></span>|<span data-ttu-id="89ad2-109">4.5</span><span class="sxs-lookup"><span data-stu-id="89ad2-109">4.5</span></span>|
|<span data-ttu-id="89ad2-110">類型</span><span class="sxs-lookup"><span data-stu-id="89ad2-110">Type</span></span>|<span data-ttu-id="89ad2-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="89ad2-111">Runtime</span></span>|
|<span data-ttu-id="89ad2-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="89ad2-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

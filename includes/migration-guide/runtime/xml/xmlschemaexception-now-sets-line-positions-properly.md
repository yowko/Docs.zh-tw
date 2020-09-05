---
ms.openlocfilehash: 04d1c1162dc79bbcb0578c6661466f4d58a57acc
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496749"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="3d1a0-101">XmlSchemaException 現在會正確設定行位置</span><span class="sxs-lookup"><span data-stu-id="3d1a0-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="3d1a0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3d1a0-102">Details</span></span>

<span data-ttu-id="3d1a0-103">如果將 <xref:System.Xml.Linq.LoadOptions.SetLineInfo> 值傳遞至 Load 方法且發生驗證錯誤，則 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 屬性現在會包含行資訊。</span><span class="sxs-lookup"><span data-stu-id="3d1a0-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3d1a0-104">建議</span><span class="sxs-lookup"><span data-stu-id="3d1a0-104">Suggestion</span></span>

<span data-ttu-id="3d1a0-105">您應該更新假設不會設定 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 的例外狀況處理程式碼，因為當使用 SetLineInfo 載入 XML 時，現在會正確設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="3d1a0-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="3d1a0-106">名稱</span><span class="sxs-lookup"><span data-stu-id="3d1a0-106">Name</span></span>    | <span data-ttu-id="3d1a0-107">值</span><span class="sxs-lookup"><span data-stu-id="3d1a0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d1a0-108">範圍</span><span class="sxs-lookup"><span data-stu-id="3d1a0-108">Scope</span></span>   |<span data-ttu-id="3d1a0-109">Edge</span><span class="sxs-lookup"><span data-stu-id="3d1a0-109">Edge</span></span>|
|<span data-ttu-id="3d1a0-110">版本</span><span class="sxs-lookup"><span data-stu-id="3d1a0-110">Version</span></span>|<span data-ttu-id="3d1a0-111">4.5</span><span class="sxs-lookup"><span data-stu-id="3d1a0-111">4.5</span></span>|
|<span data-ttu-id="3d1a0-112">類型</span><span class="sxs-lookup"><span data-stu-id="3d1a0-112">Type</span></span>|<span data-ttu-id="3d1a0-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="3d1a0-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3d1a0-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3d1a0-114">Affected APIs</span></span>

- <xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Xml.Linq.LoadOptions.SetLineInfo`

-->

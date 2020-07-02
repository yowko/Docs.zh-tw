---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620087"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="11fb7-101">FlowDocument 可能會顯示額外的文字行</span><span class="sxs-lookup"><span data-stu-id="11fb7-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="11fb7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="11fb7-102">Details</span></span>

<span data-ttu-id="11fb7-103">在某些情況下，相較於 <xref:System.Windows.Documents.FlowDocument> 項目在 .NET Framework 4.0 上執行時的顯示方式，其在 .NET Framework 4.5 上執行時，會顯示額外的文字行。</span><span class="sxs-lookup"><span data-stu-id="11fb7-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="11fb7-104">沒有任何已知的變更情況會導致文字顯示不良或無法辨識，但它可能會導致顯示之前已從 <xref:System.Windows.Documents.FlowDocument> 檢視表中省略的文字。</span><span class="sxs-lookup"><span data-stu-id="11fb7-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="11fb7-105">建議</span><span class="sxs-lookup"><span data-stu-id="11fb7-105">Suggestion</span></span>

<span data-ttu-id="11fb7-106">在某些情況下，將顯示項目的 PageHeight 屬性減 1 可以還原先前顯示的行數。</span><span class="sxs-lookup"><span data-stu-id="11fb7-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="11fb7-107">名稱</span><span class="sxs-lookup"><span data-stu-id="11fb7-107">Name</span></span>    | <span data-ttu-id="11fb7-108">值</span><span class="sxs-lookup"><span data-stu-id="11fb7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="11fb7-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="11fb7-109">Scope</span></span>   |<span data-ttu-id="11fb7-110">Edge</span><span class="sxs-lookup"><span data-stu-id="11fb7-110">Edge</span></span>|
|<span data-ttu-id="11fb7-111">版本</span><span class="sxs-lookup"><span data-stu-id="11fb7-111">Version</span></span>|<span data-ttu-id="11fb7-112">4.5</span><span class="sxs-lookup"><span data-stu-id="11fb7-112">4.5</span></span>|
|<span data-ttu-id="11fb7-113">類型</span><span class="sxs-lookup"><span data-stu-id="11fb7-113">Type</span></span>|<span data-ttu-id="11fb7-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="11fb7-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="11fb7-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="11fb7-115">Affected APIs</span></span>

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|

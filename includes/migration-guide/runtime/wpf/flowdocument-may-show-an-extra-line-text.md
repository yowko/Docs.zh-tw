---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379567"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="e4dda-101">FlowDocument 可能會顯示額外的文字行</span><span class="sxs-lookup"><span data-stu-id="e4dda-101">FlowDocument may show an extra line of text</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e4dda-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e4dda-102">Details</span></span>|<span data-ttu-id="e4dda-103">在某些情況下，相較於 <xref:System.Windows.Documents.FlowDocument> 項目在 .NET Framework 4.0 上執行時的顯示方式，其在 .NET Framework 4.5 上執行時，會顯示額外的文字行。</span><span class="sxs-lookup"><span data-stu-id="e4dda-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="e4dda-104">沒有任何已知的變更情況會導致文字顯示不良或無法辨識，但它可能會導致顯示之前已從 <xref:System.Windows.Documents.FlowDocument> 檢視表中省略的文字。</span><span class="sxs-lookup"><span data-stu-id="e4dda-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>|
|<span data-ttu-id="e4dda-105">建議</span><span class="sxs-lookup"><span data-stu-id="e4dda-105">Suggestion</span></span>|<span data-ttu-id="e4dda-106">在某些情況下，將顯示項目的 PageHeight 屬性減 1 可以還原先前顯示的行數。</span><span class="sxs-lookup"><span data-stu-id="e4dda-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>|
|<span data-ttu-id="e4dda-107">範圍</span><span class="sxs-lookup"><span data-stu-id="e4dda-107">Scope</span></span>|<span data-ttu-id="e4dda-108">Edge</span><span class="sxs-lookup"><span data-stu-id="e4dda-108">Edge</span></span>|
|<span data-ttu-id="e4dda-109">版本</span><span class="sxs-lookup"><span data-stu-id="e4dda-109">Version</span></span>|<span data-ttu-id="e4dda-110">4.5</span><span class="sxs-lookup"><span data-stu-id="e4dda-110">4.5</span></span>|
|<span data-ttu-id="e4dda-111">類型</span><span class="sxs-lookup"><span data-stu-id="e4dda-111">Type</span></span>|<span data-ttu-id="e4dda-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="e4dda-112">Runtime</span></span>|
|<span data-ttu-id="e4dda-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e4dda-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

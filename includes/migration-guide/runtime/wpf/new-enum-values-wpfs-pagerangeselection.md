---
ms.openlocfilehash: edd194fef27d97976f1ff45daec1cd56382bbb55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803502"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="0bcd0-101">WPF PageRangeSelection 中的新列舉值</span><span class="sxs-lookup"><span data-stu-id="0bcd0-101">New enum values in WPF's PageRangeSelection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0bcd0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0bcd0-102">Details</span></span>|<span data-ttu-id="0bcd0-103">兩個新成員 (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=name> 和 <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=name>) 已新增至 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> 列舉。</span><span class="sxs-lookup"><span data-stu-id="0bcd0-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=name> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=name>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> enum.</span></span>|
|<span data-ttu-id="0bcd0-104">建議</span><span class="sxs-lookup"><span data-stu-id="0bcd0-104">Suggestion</span></span>|<span data-ttu-id="0bcd0-105">在大多數情況下，這些變更不會影響使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bcd0-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="0bcd0-106">不過，您應該修改與 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> 型別的 <xref:System.Enum.GetNames(System.Type)> 或 <xref:System.Enum.GetValues(System.Type)> 呼叫中現有的特定項目數目相依的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bcd0-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=name> type should be modified, though.</span></span>|
|<span data-ttu-id="0bcd0-107">範圍</span><span class="sxs-lookup"><span data-stu-id="0bcd0-107">Scope</span></span>|<span data-ttu-id="0bcd0-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0bcd0-108">Edge</span></span>|
|<span data-ttu-id="0bcd0-109">版本</span><span class="sxs-lookup"><span data-stu-id="0bcd0-109">Version</span></span>|<span data-ttu-id="0bcd0-110">4.5</span><span class="sxs-lookup"><span data-stu-id="0bcd0-110">4.5</span></span>|
|<span data-ttu-id="0bcd0-111">類型</span><span class="sxs-lookup"><span data-stu-id="0bcd0-111">Type</span></span>|<span data-ttu-id="0bcd0-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="0bcd0-112">Runtime</span></span>|
|<span data-ttu-id="0bcd0-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0bcd0-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|

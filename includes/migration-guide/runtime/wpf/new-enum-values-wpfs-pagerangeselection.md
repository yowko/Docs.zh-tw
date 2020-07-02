---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620095"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="308a8-101">WPF PageRangeSelection 中的新列舉值</span><span class="sxs-lookup"><span data-stu-id="308a8-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="308a8-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="308a8-102">Details</span></span>

<span data-ttu-id="308a8-103">兩個新成員 (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> 和 <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) 已新增至 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 列舉。</span><span class="sxs-lookup"><span data-stu-id="308a8-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="308a8-104">建議</span><span class="sxs-lookup"><span data-stu-id="308a8-104">Suggestion</span></span>

<span data-ttu-id="308a8-105">在大多數情況下，這些變更不會影響使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="308a8-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="308a8-106">不過，您應該修改與 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 型別的 <xref:System.Enum.GetNames(System.Type)> 或 <xref:System.Enum.GetValues(System.Type)> 呼叫中現有的特定項目數目相依的程式碼。</span><span class="sxs-lookup"><span data-stu-id="308a8-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="308a8-107">名稱</span><span class="sxs-lookup"><span data-stu-id="308a8-107">Name</span></span>    | <span data-ttu-id="308a8-108">值</span><span class="sxs-lookup"><span data-stu-id="308a8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="308a8-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="308a8-109">Scope</span></span>   |<span data-ttu-id="308a8-110">Edge</span><span class="sxs-lookup"><span data-stu-id="308a8-110">Edge</span></span>|
|<span data-ttu-id="308a8-111">版本</span><span class="sxs-lookup"><span data-stu-id="308a8-111">Version</span></span>|<span data-ttu-id="308a8-112">4.5</span><span class="sxs-lookup"><span data-stu-id="308a8-112">4.5</span></span>|
|<span data-ttu-id="308a8-113">類型</span><span class="sxs-lookup"><span data-stu-id="308a8-113">Type</span></span>|<span data-ttu-id="308a8-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="308a8-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="308a8-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="308a8-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|

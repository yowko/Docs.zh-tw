---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622024"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="52a09-101">從 CellEditEnding 處理常式呼叫 DataGrid.CommitEdit 會卸除焦點</span><span class="sxs-lookup"><span data-stu-id="52a09-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="52a09-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="52a09-102">Details</span></span>

<span data-ttu-id="52a09-103">從其中一個 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的 <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> 事件處理常式呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit> 會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 失去焦點。</span><span class="sxs-lookup"><span data-stu-id="52a09-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="52a09-104">建議</span><span class="sxs-lookup"><span data-stu-id="52a09-104">Suggestion</span></span>

<span data-ttu-id="52a09-105">此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。</span><span class="sxs-lookup"><span data-stu-id="52a09-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="52a09-106">或者，您也可以在呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> 之後明確重新選取 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>，來避免此 Bug。</span><span class="sxs-lookup"><span data-stu-id="52a09-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="52a09-107">名稱</span><span class="sxs-lookup"><span data-stu-id="52a09-107">Name</span></span>    | <span data-ttu-id="52a09-108">值</span><span class="sxs-lookup"><span data-stu-id="52a09-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="52a09-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="52a09-109">Scope</span></span>   |<span data-ttu-id="52a09-110">Edge</span><span class="sxs-lookup"><span data-stu-id="52a09-110">Edge</span></span>|
|<span data-ttu-id="52a09-111">版本</span><span class="sxs-lookup"><span data-stu-id="52a09-111">Version</span></span>|<span data-ttu-id="52a09-112">4.5</span><span class="sxs-lookup"><span data-stu-id="52a09-112">4.5</span></span>|
|<span data-ttu-id="52a09-113">類型</span><span class="sxs-lookup"><span data-stu-id="52a09-113">Type</span></span>|<span data-ttu-id="52a09-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="52a09-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52a09-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="52a09-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

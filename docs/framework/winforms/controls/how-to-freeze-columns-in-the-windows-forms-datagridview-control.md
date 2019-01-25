---
title: HOW TO：凍結 Windows Form DataGridView 控制項中的資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: b7a657af2d6caf2217aedf56422f135f0b2d667e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619408"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b2bff-102">HOW TO：凍結 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="b2bff-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b2bff-103">當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。</span><span class="sxs-lookup"><span data-stu-id="b2bff-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="b2bff-104">例如，在顯示包含許多資料行的客戶資訊資料表時，如果其他資料行可在可見區域外捲動時，仍一直顯示客戶的名稱，將會非常有用。</span><span class="sxs-lookup"><span data-stu-id="b2bff-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="b2bff-105">若要達到這種行為，您可以凍結控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="b2bff-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="b2bff-106">當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 (如果是從右至左的字集，則會凍結右邊的所有資料行)。</span><span class="sxs-lookup"><span data-stu-id="b2bff-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="b2bff-107">凍結的資料行會留在原處，而其他所有資料行則可以捲動。</span><span class="sxs-lookup"><span data-stu-id="b2bff-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2bff-108">如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。</span><span class="sxs-lookup"><span data-stu-id="b2bff-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="b2bff-109">使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。</span><span class="sxs-lookup"><span data-stu-id="b2bff-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="b2bff-110">資料行的 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> 屬性會決定資料行在格線內是否一律顯示。</span><span class="sxs-lookup"><span data-stu-id="b2bff-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="b2bff-111">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="b2bff-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="b2bff-112">另請參閱[How to:凍結資料行中的 Windows Form DataGridView 控制項使用設計工具](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="b2bff-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="b2bff-113">以程式設計方式凍結資料行</span><span class="sxs-lookup"><span data-stu-id="b2bff-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="b2bff-114">將 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b2bff-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2bff-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b2bff-115">Compiling the Code</span></span>  
 <span data-ttu-id="b2bff-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b2bff-116">This example requires:</span></span>  
  
-   <span data-ttu-id="b2bff-117">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項 ，包含名為 `AddToCartButton` 的資料行。</span><span class="sxs-lookup"><span data-stu-id="b2bff-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="b2bff-118"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b2bff-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bff-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2bff-119">See also</span></span>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b2bff-120">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="b2bff-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="b2bff-121">如何：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="b2bff-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)

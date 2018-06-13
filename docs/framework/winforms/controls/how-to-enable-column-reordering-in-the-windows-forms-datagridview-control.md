---
title: 如何：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: fbcafae2cb4e4cc320c31794269355d6312b95b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532580"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="eab16-102">如何：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="eab16-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="eab16-103">當您在 <xref:System.Windows.Forms.DataGridView> 控制項中啟用資料行重新調整順序，使用者可以使用滑鼠拖曳資料行標頭，將資料行移至新的位置。</span><span class="sxs-lookup"><span data-stu-id="eab16-103">When you enable column reordering in the <xref:System.Windows.Forms.DataGridView> control, users can move a column to a new position by dragging the column header with the mouse.</span></span> <span data-ttu-id="eab16-104">在 <xref:System.Windows.Forms.DataGridView> 控制項中，<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> 屬性值會決定使用者是否能將資料行移至不同位置。</span><span class="sxs-lookup"><span data-stu-id="eab16-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property value determines whether users can move columns to different positions.</span></span>  
  
 <span data-ttu-id="eab16-105">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="eab16-105">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="eab16-106">另請參閱[How to： 啟用資料行重新調整順序中使用 Windows Form DataGridView 控制項設計工具](http://msdn.microsoft.com/library/8xwtyc86\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="eab16-106">Also see [How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/8xwtyc86\(v=vs.110\))</span></span>  
  
### <a name="to-enable-column-reordering-programmatically"></a><span data-ttu-id="eab16-107">以程式設計方式啟用資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="eab16-107">To enable column reordering programmatically</span></span>  
  
-   <span data-ttu-id="eab16-108">將 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="eab16-108">Set the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eab16-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="eab16-109">Compiling the Code</span></span>  
 <span data-ttu-id="eab16-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="eab16-110">This example requires:</span></span>  
  
-   <span data-ttu-id="eab16-111">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="eab16-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="eab16-112"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="eab16-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab16-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eab16-113">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="eab16-114">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="eab16-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="eab16-115">操作說明：凍結 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="eab16-115">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)

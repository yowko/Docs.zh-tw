---
title: HOW TO：讓唯讀的 Windows Form DataGridView 控制項中的資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: cad80a7b242622802b5897d9903c765a877e6fd4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718355"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="03023-102">HOW TO：讓唯讀的 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="03023-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="03023-103">並非所有資料都是可編輯的。</span><span class="sxs-lookup"><span data-stu-id="03023-103">Not all data is meant for editing.</span></span> <span data-ttu-id="03023-104">在 <xref:System.Windows.Forms.DataGridView> 控制項中，資料行 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> 屬性值會決定使用者是否能編輯該資料行中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="03023-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="03023-105">如需如何將控制項設完全唯讀的資訊，請參閱[How to:防止資料列中新增和刪除 Windows Form DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)。</span><span class="sxs-lookup"><span data-stu-id="03023-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="03023-106">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="03023-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="03023-107">另請參閱[How to:資料行設為唯讀模式中的 Windows Form DataGridView 控制項使用設計工具](make-columns-read-only-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="03023-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="03023-108">以程式設計方式將資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="03023-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="03023-109">將 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="03023-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03023-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="03023-110">Compiling the Code</span></span>  
 <span data-ttu-id="03023-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="03023-111">This example requires:</span></span>  
  
-   <span data-ttu-id="03023-112">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，包含名為 `CompanyName` 的資料行。</span><span class="sxs-lookup"><span data-stu-id="03023-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="03023-113">
  <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="03023-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03023-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03023-114">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="03023-115">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="03023-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="03023-116">如何：防止資料列新增與 Windows Form DataGridView 控制項中刪除</span><span class="sxs-lookup"><span data-stu-id="03023-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)

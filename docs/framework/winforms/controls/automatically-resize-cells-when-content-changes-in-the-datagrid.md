---
title: HOW TO：在 Windows Forms DataGridView 控制項的內容變更時自動調整儲存格大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: 7acd7777ede726b9dfed2b821e4248a0ebf7797f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182490"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a35a8-102">HOW TO：在 Windows Forms DataGridView 控制項的內容變更時自動調整儲存格大小</span><span class="sxs-lookup"><span data-stu-id="a35a8-102">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a35a8-103">您可以將 <xref:System.Windows.Forms.DataGridView> 控制項設定為每當內容變更就自動調整其資料列、資料行和標頭大小，讓儲存格的大小永遠足以容納並顯示所有的值，不發生內容截斷的情況。</span><span class="sxs-lookup"><span data-stu-id="a35a8-103">You can configure the <xref:System.Windows.Forms.DataGridView> control to resize its rows, columns, and headers automatically whenever content changes, so that cells are always large enough to display their values without clipping.</span></span>  
  
 <span data-ttu-id="a35a8-104">您有許多選項可限制使用哪些儲存格來決定新的大小。</span><span class="sxs-lookup"><span data-stu-id="a35a8-104">You have many options to restrict which cells are used to determine the new sizes.</span></span> <span data-ttu-id="a35a8-105">例如，您可以只根據目前顯示之資料列中的值，將控制項設定為自動調整其資料行的寬度。</span><span class="sxs-lookup"><span data-stu-id="a35a8-105">For example, you can configure the control to automatically resize the width of its columns based only on the values in rows that are currently displayed.</span></span> <span data-ttu-id="a35a8-106">如此一來，就可以避免在使用大量的資料列時效率低落，雖然在這種情況下，有時您也可能想要自行使用調整大小方法 (例如 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> ) 來調整大小。</span><span class="sxs-lookup"><span data-stu-id="a35a8-106">With this, you can avoid inefficiency when working with large numbers of rows, although in this case, you might want to use sizing methods such as <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> to adjust sizes at times of your choosing.</span></span>  
  
 <span data-ttu-id="a35a8-107">如需稽核的詳細資訊，請參閱 [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a35a8-107">For more information about automatic resizing, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="a35a8-108">下列程式碼範例示範可供自動調整大小的選項。</span><span class="sxs-lookup"><span data-stu-id="a35a8-108">The following code example demonstrates the options available for automatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a35a8-109">範例</span><span class="sxs-lookup"><span data-stu-id="a35a8-109">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a35a8-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a35a8-110">Compiling the Code</span></span>  
 <span data-ttu-id="a35a8-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="a35a8-111">This example requires:</span></span>  
  
-   <span data-ttu-id="a35a8-112">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="a35a8-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="a35a8-113">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="a35a8-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a35a8-114">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a35a8-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a35a8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a35a8-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="a35a8-116">調整 Windows Form DataGridView 控制項中資料行和資料列的大小</span><span class="sxs-lookup"><span data-stu-id="a35a8-116">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a35a8-117">Windows Form DataGridView 控制項中的調整大小選項</span><span class="sxs-lookup"><span data-stu-id="a35a8-117">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a35a8-118">HOW TO：以程式設計方式調整儲存格大小使符合 Windows Forms DataGridView 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="a35a8-118">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)

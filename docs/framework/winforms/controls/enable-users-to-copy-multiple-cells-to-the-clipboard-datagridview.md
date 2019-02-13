---
title: HOW TO：讓使用者能夠將多個儲存格複製到剪貼簿中，從 Windows Form DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: b8b466aac35f928be66b46a2fe840945847f4bc6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220253"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="5f2a3-102">HOW TO：讓使用者能夠將多個儲存格複製到剪貼簿中，從 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5f2a3-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5f2a3-103">當您啟用儲存格複製時，會使其他應用程式可以透過 <xref:System.Windows.Forms.Clipboard> 輕易存取 <xref:System.Windows.Forms.DataGridView> 控制項中的資料。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="5f2a3-104">選取之儲存格的值會轉換為字串，並加入剪貼簿，針對 [記事本] 和 Excel 等應用程式以 Tab 鍵分隔文字值貼入，而針對 Word 等應用程式以 HTML 格式資料表貼入。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="5f2a3-105">您可以將儲存格複製設定為僅複製儲存格的值、包含剪貼簿資料中的資料列和資料行標頭文字，或僅在使用者選取整個資料列或資料行時包含標頭文字。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="5f2a3-106">根據選取模式，使用者可以選取多個儲存格的離線群組。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="5f2a3-107">當使用者複製儲存格至剪貼簿時，並不會複製未有選取之儲存格的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="5f2a3-108">所有其他資料列或資料行會變成複製到剪貼簿之資料的資料表中的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="5f2a3-109">這些資料列或資料行中的未選取儲存格會以空白預留位置複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="5f2a3-110">若要啟用儲存格複製</span><span class="sxs-lookup"><span data-stu-id="5f2a3-110">To enable cell copying</span></span>  
  
-   <span data-ttu-id="5f2a3-111">設定 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="5f2a3-112">範例</span><span class="sxs-lookup"><span data-stu-id="5f2a3-112">Example</span></span>  
 <span data-ttu-id="5f2a3-113">下列完整的程式碼範例示範儲存格如何複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="5f2a3-114">此範例包含一個按鈕，會使用 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> 方法將選取的儲存格複製到剪貼簿，並在文字方塊中顯示剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f2a3-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5f2a3-115">Compiling the Code</span></span>  
 <span data-ttu-id="5f2a3-116">此程式碼需要：</span><span class="sxs-lookup"><span data-stu-id="5f2a3-116">This code requires:</span></span>  
  
-   <span data-ttu-id="5f2a3-117">N:System 和 N:System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5f2a3-118">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5f2a3-119">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="5f2a3-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2a3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f2a3-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="5f2a3-121">選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="5f2a3-121">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)

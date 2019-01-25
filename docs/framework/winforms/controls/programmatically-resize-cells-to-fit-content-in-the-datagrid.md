---
title: HOW TO：以程式設計方式調整大小以符合內容，在 Windows Form DataGridView 控制項中的資料格
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: 1f7ca8e506e4062a9181267e06b4ce207642bf06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707813"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3a605-102">HOW TO：以程式設計方式調整大小以符合內容，在 Windows Form DataGridView 控制項中的資料格</span><span class="sxs-lookup"><span data-stu-id="3a605-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3a605-103">您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項方法來調整資料列、資料行和標頭的大小，讓它們可以顯示完整的值，而不至發生截斷狀況。</span><span class="sxs-lookup"><span data-stu-id="3a605-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="3a605-104">您有時可使用這些方法來調整您選擇的 <xref:System.Windows.Forms.DataGridView> 項目大小。</span><span class="sxs-lookup"><span data-stu-id="3a605-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="3a605-105">此外，您可以將控制項設定為每當內容變更時，就自動調整這些項目的大小。</span><span class="sxs-lookup"><span data-stu-id="3a605-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="3a605-106">不過，在使用大型資料集或資料經常變更時，這樣做可能會沒有效率。</span><span class="sxs-lookup"><span data-stu-id="3a605-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="3a605-107">如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3a605-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="3a605-108">一般而言，只有在從資料來源載入新資料或當使用者已編輯某個值時，才會以程式設計方式調整 <xref:System.Windows.Forms.DataGridView> 項目，以符合項目的內容大小。</span><span class="sxs-lookup"><span data-stu-id="3a605-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="3a605-109">這對於最佳化效能很有用，不過如果想讓使用者使用滑鼠手動調整資料列和資料行的大小，這也非常有用。</span><span class="sxs-lookup"><span data-stu-id="3a605-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="3a605-110">下列程式碼範例示範以程式設計方式調整大小時可使用的選項。</span><span class="sxs-lookup"><span data-stu-id="3a605-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a605-111">範例</span><span class="sxs-lookup"><span data-stu-id="3a605-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3a605-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3a605-112">Compiling the Code</span></span>  
 <span data-ttu-id="3a605-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3a605-113">This example requires:</span></span>  
  
-   <span data-ttu-id="3a605-114">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3a605-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3a605-115">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="3a605-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3a605-116">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3a605-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="3a605-117">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="3a605-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a605-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a605-118">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="3a605-119">調整 Windows Forms DataGridView 控制項中資料行和資料列的大小</span><span class="sxs-lookup"><span data-stu-id="3a605-119">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3a605-120">Windows Forms DataGridView 控制項中的調整大小選項</span><span class="sxs-lookup"><span data-stu-id="3a605-120">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3a605-121">如何：自動調整大小的資料格，當 Windows Form DataGridView 控制項中的內容變更</span><span class="sxs-lookup"><span data-stu-id="3a605-121">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)

---
title: 如何：自訂 Windows Form DataGridView 控制項的排序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 34a92af246e1145e8d0d1d6874b2d64d7dee7846
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749479"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0faac-102">如何：自訂 Windows Form DataGridView 控制項的排序</span><span class="sxs-lookup"><span data-stu-id="0faac-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0faac-103"><xref:System.Windows.Forms.DataGridView> 控制項提供自動排序，但是根據您的需求，您可能需要自訂排序作業。</span><span class="sxs-lookup"><span data-stu-id="0faac-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="0faac-104">例如，您可以使用程式設計排序建立替代的使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="0faac-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="0faac-105">或者為了在排序時獲得更大的彈性，您可以處理 <xref:System.Windows.Forms.DataGridView.SortCompare> 事件或呼叫 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(IComparer)` 多載，例如排序多個資料行。</span><span class="sxs-lookup"><span data-stu-id="0faac-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="0faac-106">下列程式碼範例示範自訂排序的三種方法。</span><span class="sxs-lookup"><span data-stu-id="0faac-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="0faac-107">如需詳細資訊，請參閱 [Windows Forms DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0faac-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="0faac-108">程式設計排序</span><span class="sxs-lookup"><span data-stu-id="0faac-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="0faac-109">下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridView.SortOrder%2A> 和 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> 屬性的程式設計排序，以決定排序的方向和 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> 屬性來手動設定排序圖像。</span><span class="sxs-lookup"><span data-stu-id="0faac-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="0faac-110"><xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(DataGridViewColumn,ListSortDirection)` 多載只用於在單一資料行排序資料。</span><span class="sxs-lookup"><span data-stu-id="0faac-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="0faac-111">使用 SortCompare 事件的自訂排序</span><span class="sxs-lookup"><span data-stu-id="0faac-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="0faac-112">下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridView.SortCompare> 事件處理常式自訂排序 。</span><span class="sxs-lookup"><span data-stu-id="0faac-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="0faac-113">所選 <xref:System.Windows.Forms.DataGridViewColumn> 已排序，若資料行中有重複的值，則 ID 資料行會用於決定最終的順序。</span><span class="sxs-lookup"><span data-stu-id="0faac-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="0faac-114">使用 IComparer 介面的自訂排序</span><span class="sxs-lookup"><span data-stu-id="0faac-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="0faac-115">下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(IComparer)` 多載自訂排序，這會採用 <xref:System.Collections.IComparer> 介面的實作來執行多個資料行排序。</span><span class="sxs-lookup"><span data-stu-id="0faac-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0faac-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0faac-116">Compiling the Code</span></span>  
 <span data-ttu-id="0faac-117">這些範例需要：</span><span class="sxs-lookup"><span data-stu-id="0faac-117">These examples require:</span></span>  
  
-   <span data-ttu-id="0faac-118">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0faac-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0faac-119">Visual Basic 或 Visual C# 建置這些範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="0faac-119">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0faac-120">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0faac-120">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0faac-121">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="0faac-121">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faac-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0faac-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="0faac-123">在 Windows Forms DataGridView 控制項中排序資料</span><span class="sxs-lookup"><span data-stu-id="0faac-123">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0faac-124">Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="0faac-124">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0faac-125">操作說明：設定 Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="0faac-125">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)

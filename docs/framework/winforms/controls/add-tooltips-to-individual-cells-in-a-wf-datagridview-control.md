---
title: HOW TO：將工具提示新增至 Windows Forms DataGridView 控制項的個別儲存格
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: 3307c92a13e5730de6dce0fe45b924e44b7af554
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119635"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="f3fe0-102">HOW TO：將工具提示新增至 Windows Forms DataGridView 控制項的個別儲存格</span><span class="sxs-lookup"><span data-stu-id="f3fe0-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f3fe0-103">根據預設，工具提示用來顯示值<xref:System.Windows.Forms.DataGridView>太小，無法顯示其完整內容的儲存格。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="f3fe0-104">您可以覆寫這個行為，不過，設定個別資料格的工具提示文字值。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="f3fe0-105">這是要顯示給使用者的其他資訊的資料格，或為使用者提供的儲存格內容的其他說明很有用。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="f3fe0-106">比方說，如果您有顯示狀態圖示的資料列時，您可能想要提供使用工具提示的文字說明。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="f3fe0-107">您也可以停用的資料格層級的工具提示顯示設定<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="f3fe0-108">若要加入儲存格的工具提示</span><span class="sxs-lookup"><span data-stu-id="f3fe0-108">To add a ToolTip to a cell</span></span>  
  
-   <span data-ttu-id="f3fe0-109">設定 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3fe0-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f3fe0-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f3fe0-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f3fe0-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f3fe0-112">A<xref:System.Windows.Forms.DataGridView>控制項，名為`dataGridView1`，其中包含資料行，名為`Rating`顯示透過四個星號的字串值 ("\*") 符號。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="f3fe0-113"><xref:System.Windows.Forms.DataGridView.CellFormatting>控制項事件的範例所示的事件處理常式方法必須有關聯。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
-   <span data-ttu-id="f3fe0-114"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f3fe0-115">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="f3fe0-115">Robust Programming</span></span>  
 <span data-ttu-id="f3fe0-116">當您繫結<xref:System.Windows.Forms.DataGridView>控制權傳輸至外部資料來源或提供您自己的資料來源，藉由實作虛擬模式，您可能會遇到效能問題。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="f3fe0-117">若要使用的大量資料時，請避免對效能帶來負面影響，處理<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>事件，而不是設定<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>的多個資料格的屬性。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="f3fe0-118">當您處理這個事件，取得儲存格的值<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>屬性引發事件，並傳回值<xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>屬性做為事件中指定處理常式。</span><span class="sxs-lookup"><span data-stu-id="f3fe0-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fe0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3fe0-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f3fe0-120">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="f3fe0-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)

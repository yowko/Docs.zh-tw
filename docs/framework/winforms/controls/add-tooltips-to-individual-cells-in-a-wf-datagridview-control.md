---
title: 將工具提示加入至 DataGridView 控制項中的個別儲存格
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
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732188"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="8b6b3-102">如何：將工具提示加入至 Windows Form DataGridView 控制項中的個別儲存格</span><span class="sxs-lookup"><span data-stu-id="8b6b3-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8b6b3-103">根據預設，工具提示是用來顯示太小而無法顯示其全部內容的 <xref:System.Windows.Forms.DataGridView> 資料格的值。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="8b6b3-104">不過，您可以覆寫此行為，以設定個別資料格的工具提示文字值。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="8b6b3-105">這適用于向使用者顯示資料格的其他相關資訊，或為使用者提供資料格內容的替代描述。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="8b6b3-106">例如，如果您有一個顯示狀態圖示的資料列，您可能會想要使用工具提示來提供文字說明。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="8b6b3-107">您也可以將 [<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>] 屬性設定為 [`false`]，以停用資料格層級工具提示的顯示。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="8b6b3-108">若要將工具提示加入至資料格</span><span class="sxs-lookup"><span data-stu-id="8b6b3-108">To add a ToolTip to a cell</span></span>  
  
- <span data-ttu-id="8b6b3-109">設定 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b6b3-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8b6b3-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="8b6b3-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8b6b3-111">This example requires:</span></span>  
  
- <span data-ttu-id="8b6b3-112">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含名為 `Rating` 的資料行，可顯示一到四個星號（"\*"）符號的字串值。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="8b6b3-113">控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件必須與範例中所示的事件處理常式方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
- <span data-ttu-id="8b6b3-114"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8b6b3-115">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="8b6b3-115">Robust Programming</span></span>  
 <span data-ttu-id="8b6b3-116">當您將 <xref:System.Windows.Forms.DataGridView> 控制項系結到外部資料源，或藉由執行虛擬模式來提供自己的資料來源時，可能會遇到效能問題。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="8b6b3-117">若要避免使用大量資料時的效能損失，請處理 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> 事件，而不是設定多個儲存格的 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="8b6b3-118">當您處理這個事件時，取得資料格的值 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 屬性會引發事件，並傳回事件處理常式中所指定 <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8b6b3-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6b3-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b6b3-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8b6b3-120">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="8b6b3-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)

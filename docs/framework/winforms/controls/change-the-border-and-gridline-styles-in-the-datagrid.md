---
title: 變更 DataGridView 控制項中的框線和格線樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744706"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6fb40-102">如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式</span><span class="sxs-lookup"><span data-stu-id="6fb40-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6fb40-103">有了 <xref:System.Windows.Forms.DataGridView> 控制項，您就可以自訂控制項的框線和格線外觀，以改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="6fb40-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="6fb40-104">除了控制項內儲存格的框線樣式以外，您還可以修改格線色彩和控制項框線樣式。</span><span class="sxs-lookup"><span data-stu-id="6fb40-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="6fb40-105">您也可以針對一般資料格、資料列標頭儲存格和資料行標頭儲存格套用不同的儲存格框線樣式。</span><span class="sxs-lookup"><span data-stu-id="6fb40-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fb40-106">格線色彩僅適用于 <xref:System.Windows.Forms.DataGridViewCellBorderStyle> 列舉的 <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>、<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>和 <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> 值，以及 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> 列舉的 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> 值。</span><span class="sxs-lookup"><span data-stu-id="6fb40-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="6fb40-107">這些列舉的其他值會使用作業系統所指定的色彩。</span><span class="sxs-lookup"><span data-stu-id="6fb40-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="6fb40-108">此外，當您透過 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法在 Windows XP 和 Windows Server 2003 系列上啟用視覺化樣式時，不會使用 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="6fb40-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="6fb40-109">以程式設計方式變更格線色彩</span><span class="sxs-lookup"><span data-stu-id="6fb40-109">To change the gridline color programmatically</span></span>  
  
- <span data-ttu-id="6fb40-110">設定 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6fb40-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="6fb40-111">以程式設計方式變更整個 DataGridView 控制項的框線樣式</span><span class="sxs-lookup"><span data-stu-id="6fb40-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
- <span data-ttu-id="6fb40-112">將 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.BorderStyle> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="6fb40-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="6fb40-113">以程式設計方式變更 DataGridView 儲存格的框線樣式</span><span class="sxs-lookup"><span data-stu-id="6fb40-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
- <span data-ttu-id="6fb40-114">設定 [<xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>]、[<xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>] 和 [<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="6fb40-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="6fb40-115">範例</span><span class="sxs-lookup"><span data-stu-id="6fb40-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fb40-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6fb40-116">Compiling the Code</span></span>  
 <span data-ttu-id="6fb40-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6fb40-117">This example requires:</span></span>  
  
- <span data-ttu-id="6fb40-118">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="6fb40-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="6fb40-119"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6fb40-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb40-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fb40-120">See also</span></span>

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [<span data-ttu-id="6fb40-121">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="6fb40-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)

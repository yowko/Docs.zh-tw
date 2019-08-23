---
title: 作法：變更 Windows Forms DataGridView 控制項的框線和格線樣式
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
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917677"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f38b9-102">HOW TO：變更 Windows Forms DataGridView 控制項的框線和格線樣式</span><span class="sxs-lookup"><span data-stu-id="f38b9-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f38b9-103"><xref:System.Windows.Forms.DataGridView>使用控制項, 您可以自訂控制項的框線和格線外觀, 以改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="f38b9-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="f38b9-104">除了控制項內儲存格的框線樣式以外, 您還可以修改格線色彩和控制項框線樣式。</span><span class="sxs-lookup"><span data-stu-id="f38b9-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="f38b9-105">您也可以針對一般資料格、資料列標頭儲存格和資料行標頭儲存格套用不同的儲存格框線樣式。</span><span class="sxs-lookup"><span data-stu-id="f38b9-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f38b9-106"><xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>格線色彩僅適用于<xref:System.Windows.Forms.DataGridViewCellBorderStyle>列舉的、 <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>和<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical>值, 以及<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>列舉的值。</span><span class="sxs-lookup"><span data-stu-id="f38b9-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="f38b9-107">這些列舉的其他值會使用作業系統所指定的色彩。</span><span class="sxs-lookup"><span data-stu-id="f38b9-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="f38b9-108">此外, 當您透過<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法<xref:System.Windows.Forms.DataGridView.GridColor%2A>在 windows XP 和 windows Server 2003 系列上啟用視覺化樣式時, 不會使用屬性值。</span><span class="sxs-lookup"><span data-stu-id="f38b9-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="f38b9-109">以程式設計方式變更格線色彩</span><span class="sxs-lookup"><span data-stu-id="f38b9-109">To change the gridline color programmatically</span></span>  
  
- <span data-ttu-id="f38b9-110">設定 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f38b9-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="f38b9-111">以程式設計方式變更整個 DataGridView 控制項的框線樣式</span><span class="sxs-lookup"><span data-stu-id="f38b9-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
- <span data-ttu-id="f38b9-112">將 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.BorderStyle> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="f38b9-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="f38b9-113">以程式設計方式變更 DataGridView 儲存格的框線樣式</span><span class="sxs-lookup"><span data-stu-id="f38b9-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
- <span data-ttu-id="f38b9-114"><xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>設定、 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>和屬性。<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A></span><span class="sxs-lookup"><span data-stu-id="f38b9-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="f38b9-115">範例</span><span class="sxs-lookup"><span data-stu-id="f38b9-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f38b9-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f38b9-116">Compiling the Code</span></span>  
 <span data-ttu-id="f38b9-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f38b9-117">This example requires:</span></span>  
  
- <span data-ttu-id="f38b9-118">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f38b9-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f38b9-119"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f38b9-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38b9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f38b9-120">See also</span></span>

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [<span data-ttu-id="f38b9-121">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="f38b9-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)

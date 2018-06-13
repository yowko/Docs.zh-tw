---
title: 如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式
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
ms.openlocfilehash: 94e5ae11d7fb2b67e028f368183246f8d8543a08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528745"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="911c9-102">如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式</span><span class="sxs-lookup"><span data-stu-id="911c9-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="911c9-103">與<xref:System.Windows.Forms.DataGridView>控制項，您可以自訂控制項的框線和格線，以改善使用者體驗的外觀。</span><span class="sxs-lookup"><span data-stu-id="911c9-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="911c9-104">您可以修改格線的色彩和控制項的框線樣式，除了在控制項中的資料格的框線樣式。</span><span class="sxs-lookup"><span data-stu-id="911c9-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="911c9-105">您也可以套用不同的儲存格一般儲存格、 資料列標題儲存格和資料行首儲存格的框線樣式。</span><span class="sxs-lookup"><span data-stu-id="911c9-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="911c9-106">格線的色彩只會搭配使用<xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>， <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>，和<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical>值<xref:System.Windows.Forms.DataGridViewCellBorderStyle>列舉型別和<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single>值<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="911c9-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="911c9-107">這些列舉型別的其他值會使用作業系統所指定的色彩。</span><span class="sxs-lookup"><span data-stu-id="911c9-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="911c9-108">此外，當啟用視覺化樣式 Windows XP 和 Windows Server 2003 系列，透過<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法，<xref:System.Windows.Forms.DataGridView.GridColor%2A>不會使用屬性值。</span><span class="sxs-lookup"><span data-stu-id="911c9-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="911c9-109">若要以程式設計方式變更格線的色彩</span><span class="sxs-lookup"><span data-stu-id="911c9-109">To change the gridline color programmatically</span></span>  
  
-   <span data-ttu-id="911c9-110">設定 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="911c9-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="911c9-111">若要以程式設計方式變更整個 DataGridView 控制項的框線樣式</span><span class="sxs-lookup"><span data-stu-id="911c9-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
-   <span data-ttu-id="911c9-112">將 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.BorderStyle> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="911c9-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="911c9-113">若要以程式設計方式變更 DataGridView 儲存格的框線樣式</span><span class="sxs-lookup"><span data-stu-id="911c9-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
-   <span data-ttu-id="911c9-114">設定<xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>， <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>，和<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="911c9-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="911c9-115">範例</span><span class="sxs-lookup"><span data-stu-id="911c9-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="911c9-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="911c9-116">Compiling the Code</span></span>  
 <span data-ttu-id="911c9-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="911c9-117">This example requires:</span></span>  
  
-   <span data-ttu-id="911c9-118">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="911c9-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="911c9-119"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="911c9-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911c9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="911c9-120">See Also</span></span>  
 <xref:System.Windows.Forms.BorderStyle>  
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>  
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>  
 [<span data-ttu-id="911c9-121">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="911c9-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)

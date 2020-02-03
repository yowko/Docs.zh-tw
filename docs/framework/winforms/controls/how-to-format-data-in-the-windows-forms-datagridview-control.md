---
title: 格式化 DataGridView 控制項中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 9ee2869cf4085b5acfdf1f8c440151be506dbe3e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736782"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="285dc-102">如何：格式化 Windows Form DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="285dc-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="285dc-103">下列程式示範使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性和控制項中特定資料行的資料格值的基本格式。</span><span class="sxs-lookup"><span data-stu-id="285dc-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="285dc-104">如需有關 advanced data 格式的詳細資訊，請參閱[如何：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="285dc-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="285dc-105">若要格式化貨幣和日期值</span><span class="sxs-lookup"><span data-stu-id="285dc-105">To format currency and date values</span></span>  
  
- <span data-ttu-id="285dc-106">設定 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 的 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性。</span><span class="sxs-lookup"><span data-stu-id="285dc-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="285dc-107">下列程式碼範例會使用資料行的 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性來設定特定資料行的格式。</span><span class="sxs-lookup"><span data-stu-id="285dc-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="285dc-108">[`UnitPrice`] 資料行中的值會以目前的特定文化特性貨幣格式顯示，並以括弧括住負數值。</span><span class="sxs-lookup"><span data-stu-id="285dc-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="285dc-109">[`ShipDate`] 資料行中的值會以目前的特定文化特性簡短日期格式出現。</span><span class="sxs-lookup"><span data-stu-id="285dc-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="285dc-110">如需 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 值的詳細資訊，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="285dc-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="285dc-111">若要自訂 null 資料庫值的顯示</span><span class="sxs-lookup"><span data-stu-id="285dc-111">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="285dc-112">設定 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 的 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性。</span><span class="sxs-lookup"><span data-stu-id="285dc-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="285dc-113">下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性，在包含等於 <xref:System.DBNull.Value?displayProperty=nameWithType>之值的所有資料格中顯示「沒有專案」。</span><span class="sxs-lookup"><span data-stu-id="285dc-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="285dc-114">若要在以文字為基礎的資料格中啟用自動換行</span><span class="sxs-lookup"><span data-stu-id="285dc-114">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="285dc-115">將 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.DataGridViewTriState> 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="285dc-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="285dc-116">下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性來設定整個控制項的換行模式。</span><span class="sxs-lookup"><span data-stu-id="285dc-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="285dc-117">若要指定 DataGridView 儲存格的文字對齊方式</span><span class="sxs-lookup"><span data-stu-id="285dc-117">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="285dc-118">將 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.DataGridViewContentAlignment> 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="285dc-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="285dc-119">下列程式碼範例會使用資料行的 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性來設定特定資料行的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="285dc-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="285dc-120">範例</span><span class="sxs-lookup"><span data-stu-id="285dc-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="285dc-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="285dc-121">Compiling the Code</span></span>  
 <span data-ttu-id="285dc-122">這些範例需要：</span><span class="sxs-lookup"><span data-stu-id="285dc-122">These examples require:</span></span>  
  
- <span data-ttu-id="285dc-123">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含名為 `UnitPrice`的資料行、名為 `ShipDate`的資料行，以及名為 `CustomerName`的資料行。</span><span class="sxs-lookup"><span data-stu-id="285dc-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="285dc-124"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="285dc-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="285dc-125">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="285dc-125">Robust Programming</span></span>  
 <span data-ttu-id="285dc-126">為了達到最大的擴充性，您應該跨多個資料列、資料行或使用相同樣式的資料格共用 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個元素的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="285dc-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="285dc-127">如需詳細資訊，請參閱 [縮放 Windows Form DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="285dc-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285dc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="285dc-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="285dc-129">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="285dc-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="285dc-130">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="285dc-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="285dc-131">Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="285dc-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="285dc-132">操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="285dc-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="285dc-133">格式化類型</span><span class="sxs-lookup"><span data-stu-id="285dc-133">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

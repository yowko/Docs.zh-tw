---
title: 格式化 DataGridView 控制項中的資料
description: 瞭解如何使用 Windows Forms DataGridView 控制項的 Datagridviewband.defaultcellstyle 屬性和控制項中的特定資料行來格式化資料格值。
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
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622805"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ac969-103">如何：格式化 Windows Form DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="ac969-103">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ac969-104">下列程式示範如何使用控制項的 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性 <xref:System.Windows.Forms.DataGridView> 和控制項中特定資料行的屬性，來顯示資料格值的基本格式。</span><span class="sxs-lookup"><span data-stu-id="ac969-104">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="ac969-105">如需有關 advanced data 格式的詳細資訊，請參閱[如何：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ac969-105">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="ac969-106">若要格式化貨幣和日期值</span><span class="sxs-lookup"><span data-stu-id="ac969-106">To format currency and date values</span></span>  
  
- <span data-ttu-id="ac969-107">設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ac969-107">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="ac969-108">下列程式碼範例會使用資料行的屬性來設定特定資料行的格式 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ac969-108">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="ac969-109">資料行中的值 `UnitPrice` 會以目前的文化特性特定貨幣格式顯示，並以括弧括住負數值。</span><span class="sxs-lookup"><span data-stu-id="ac969-109">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="ac969-110">資料行中的值 `ShipDate` 會以目前的特定文化特性簡短日期格式出現。</span><span class="sxs-lookup"><span data-stu-id="ac969-110">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="ac969-111">如需有關值的詳細資訊 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> ，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ac969-111">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="ac969-112">若要自訂 null 資料庫值的顯示</span><span class="sxs-lookup"><span data-stu-id="ac969-112">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="ac969-113">設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ac969-113">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="ac969-114">下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性，在包含等於之值的所有資料格中顯示「沒有專案」 <xref:System.DBNull.Value?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ac969-114">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="ac969-115">若要在以文字為基礎的資料格中啟用自動換行</span><span class="sxs-lookup"><span data-stu-id="ac969-115">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="ac969-116">將的 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 屬性設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 為其中一個 <xref:System.Windows.Forms.DataGridViewTriState> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="ac969-116">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="ac969-117">下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性來設定整個控制項的換行模式。</span><span class="sxs-lookup"><span data-stu-id="ac969-117">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="ac969-118">若要指定 DataGridView 儲存格的文字對齊方式</span><span class="sxs-lookup"><span data-stu-id="ac969-118">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="ac969-119">將的 <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> 屬性設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 為其中一個 <xref:System.Windows.Forms.DataGridViewContentAlignment> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="ac969-119">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="ac969-120">下列程式碼範例會使用資料行的屬性來設定特定資料行的對齊方式 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ac969-120">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="ac969-121">範例</span><span class="sxs-lookup"><span data-stu-id="ac969-121">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac969-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ac969-122">Compiling the Code</span></span>  
 <span data-ttu-id="ac969-123">這些範例需要：</span><span class="sxs-lookup"><span data-stu-id="ac969-123">These examples require:</span></span>  
  
- <span data-ttu-id="ac969-124"><xref:System.Windows.Forms.DataGridView>名為 `dataGridView1` 的控制項，其中包含名為的資料行 `UnitPrice` 、名為的資料行 `ShipDate` ，以及名為的資料行 `CustomerName` 。</span><span class="sxs-lookup"><span data-stu-id="ac969-124">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="ac969-125"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ac969-125">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ac969-126">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="ac969-126">Robust Programming</span></span>  
 <span data-ttu-id="ac969-127">為了達到最大的擴充性，您應該 <xref:System.Windows.Forms.DataGridViewCellStyle> 跨多個資料列、資料行或資料格共用物件，而這些資料列使用相同的樣式，而不是分別設定每個元素的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="ac969-127">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="ac969-128">如需詳細資訊，請參閱 [縮放 Windows Form DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ac969-128">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac969-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac969-129">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="ac969-130">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="ac969-130">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ac969-131">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="ac969-131">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ac969-132">Windows Form DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="ac969-132">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ac969-133">如何：自訂 Windows Form DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="ac969-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ac969-134">格式化類型</span><span class="sxs-lookup"><span data-stu-id="ac969-134">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

---
title: "如何：格式化 Windows Form DataGridView 控制項中的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4be8ce245fdc17c55c03adb3d1e50f93b4e2a7e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1171e-102">如何：格式化 Windows Form DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="1171e-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1171e-103">下列程序示範基本的資料格的值使用的格式<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性<xref:System.Windows.Forms.DataGridView>控制項和控制項中的特定資料行。</span><span class="sxs-lookup"><span data-stu-id="1171e-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="1171e-104">如需進階的資料格式資訊，請參閱[How to： 在 Windows Form DataGridView 控制項中自訂格式化資料](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1171e-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="1171e-105">若要將貨幣格式化數值和日期值</span><span class="sxs-lookup"><span data-stu-id="1171e-105">To format currency and date values</span></span>  
  
-   <span data-ttu-id="1171e-106">設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1171e-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="1171e-107">下列程式碼範例會設定使用的特定資料行的格式<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>之資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="1171e-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="1171e-108">中的值`UnitPrice`資料行以目前的文化特性的貨幣格式顯示，並以括號括住的負數值。</span><span class="sxs-lookup"><span data-stu-id="1171e-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="1171e-109">中的值`ShipDate`目前文化特性的簡短日期格式顯示資料行。</span><span class="sxs-lookup"><span data-stu-id="1171e-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="1171e-110">如需有關<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>值，請參閱[格式化型別](../../../../docs/standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1171e-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="1171e-111">若要自訂資料庫 null 值的顯示</span><span class="sxs-lookup"><span data-stu-id="1171e-111">To customize the display of null database values</span></span>  
  
-   <span data-ttu-id="1171e-112">設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1171e-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="1171e-113">下列程式碼範例使用<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>屬性中包含值相等的所有資料格顯示 「 沒有項目 」 <xref:System.DBNull.Value?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1171e-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="1171e-114">若要啟用自動換行中以文字為基礎的資料格</span><span class="sxs-lookup"><span data-stu-id="1171e-114">To enable wordwrap in text-based cells</span></span>  
  
-   <span data-ttu-id="1171e-115">設定<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>的其中一個<xref:System.Windows.Forms.DataGridViewTriState>列舉值。</span><span class="sxs-lookup"><span data-stu-id="1171e-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="1171e-116">下列程式碼範例使用<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>屬性來設定整個控制項的自動換行模式。</span><span class="sxs-lookup"><span data-stu-id="1171e-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="1171e-117">若要指定 DataGridView 儲存格的文字對齊方式</span><span class="sxs-lookup"><span data-stu-id="1171e-117">To specify the text alignment of DataGridView cells</span></span>  
  
-   <span data-ttu-id="1171e-118">設定<xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>的其中一個<xref:System.Windows.Forms.DataGridViewContentAlignment>列舉值。</span><span class="sxs-lookup"><span data-stu-id="1171e-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="1171e-119">下列程式碼範例會設定特定資料行使用的對齊方式<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="1171e-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="1171e-120">範例</span><span class="sxs-lookup"><span data-stu-id="1171e-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1171e-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1171e-121">Compiling the Code</span></span>  
 <span data-ttu-id="1171e-122">這些範例需要：</span><span class="sxs-lookup"><span data-stu-id="1171e-122">These examples require:</span></span>  
  
-   <span data-ttu-id="1171e-123">A<xref:System.Windows.Forms.DataGridView>控制項，名為`dataGridView1`，其中包含名為資料行`UnitPrice`，名為資料行`ShipDate`，和名為資料行`CustomerName`。</span><span class="sxs-lookup"><span data-stu-id="1171e-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
-   <span data-ttu-id="1171e-124"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1171e-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1171e-125">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1171e-125">Robust Programming</span></span>  
 <span data-ttu-id="1171e-126">達到最大延展性，您應該共用<xref:System.Windows.Forms.DataGridViewCellStyle>跨多個資料列、 資料行或使用相同的樣式，而不是個別設定每個項目之樣式屬性的資料格的物件。</span><span class="sxs-lookup"><span data-stu-id="1171e-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="1171e-127">如需詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1171e-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1171e-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="1171e-128">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="1171e-129">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="1171e-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1171e-130">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="1171e-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1171e-131">Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="1171e-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1171e-132">操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="1171e-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1171e-133">格式化類型</span><span class="sxs-lookup"><span data-stu-id="1171e-133">Formatting Types</span></span>](../../../../docs/standard/base-types/formatting-types.md)

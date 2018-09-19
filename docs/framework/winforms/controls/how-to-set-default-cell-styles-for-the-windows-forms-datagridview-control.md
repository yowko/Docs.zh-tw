---
title: 如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 072a9ce7e28983683ac1104b70c160cf5eea12b7
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325582"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="0bb1f-102">如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="0bb1f-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0bb1f-103">您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項為整個控制項，以及為特定資料行和資料列，指定預設儲存格樣式。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="0bb1f-104">這些預設值會從控制項層級往下篩選至資料行層級，接著至資料列層級，然後至儲存格層級。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="0bb1f-105">如果在儲存格層級未設定特定 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性，則會使用資料列層級的預設屬性設定。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="0bb1f-106">如果在資料列層級也未設定這個屬性，則會使用預設資料行設定。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="0bb1f-107">最後，如果在資料行層級還是未設定這個屬性，則會使用預設 <xref:System.Windows.Forms.DataGridView> 設定。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="0bb1f-108">您可以利用這項設定，避免必須在多個層級重複設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="0bb1f-109">您只需要在每個層級指定不同於上一層級的樣式。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="0bb1f-110">如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="0bb1f-111">在 Visual Studio 中對於本工作有更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="0bb1f-112">另請參閱[如何： 設定預設的儲存格樣式和資料格式的 Windows Form DataGridView 控制項使用設計工具](https://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="0bb1f-113">以程式設計方式設定預設儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="0bb1f-113">To set the default cell styles programmatically</span></span>  
  
1.  <span data-ttu-id="0bb1f-114">設定透過 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性擷取之 <xref:System.Windows.Forms.DataGridViewCellStyle> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  <span data-ttu-id="0bb1f-115">建立並初始化新的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，以供多個資料列和資料行使用。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  <span data-ttu-id="0bb1f-116">設定特定資料列和資料行的 `DefaultCellStyle` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="0bb1f-117">範例</span><span class="sxs-lookup"><span data-stu-id="0bb1f-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0bb1f-118">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0bb1f-118">Compiling the Code</span></span>  
 <span data-ttu-id="0bb1f-119">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0bb1f-119">This example requires:</span></span>  
  
-   <span data-ttu-id="0bb1f-120">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="0bb1f-121"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0bb1f-122">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0bb1f-122">Robust Programming</span></span>  
 <span data-ttu-id="0bb1f-123">若要在您使用非常大量的資料集時達到最大延展性，您應該共用使用相同樣式的多個資料列、資料行或儲存格之間的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個項目的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="0bb1f-124">此外，您應該建立共用資料列，並使用 <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> 屬性來加以存取。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0bb1f-125">如需詳細資訊，請參閱 <<c0> [ 縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0bb1f-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb1f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bb1f-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0bb1f-127">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="0bb1f-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0bb1f-128">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="0bb1f-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0bb1f-129">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="0bb1f-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0bb1f-130">操作說明：設定 Windows Forms DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="0bb1f-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)

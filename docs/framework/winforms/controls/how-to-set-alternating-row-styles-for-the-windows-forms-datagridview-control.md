---
title: HOW TO：設定 Windows Form DataGridView 控制項中替代資料列樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: 56fe5de9c69d14368508a7f6ccdd6c3becd8ff5b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710247"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="6caf0-102">HOW TO：設定 Windows Form DataGridView 控制項中替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="6caf0-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6caf0-103">表格式資料通常會以類似 Ledger 的格式呈現給使用者，在這種格式中，交替資料列會有不同的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="6caf0-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="6caf0-104">這種格式可讓使用者輕鬆地指出每個資料列中有哪些儲存格，特別是具有許多資料行的寬資料表。</span><span class="sxs-lookup"><span data-stu-id="6caf0-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="6caf0-105">利用 <xref:System.Windows.Forms.DataGridView> 控制項，您可以指定替代資料列的完整樣式資訊。</span><span class="sxs-lookup"><span data-stu-id="6caf0-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="6caf0-106">這個控制項可讓您使用背景色彩以外的樣式特性 (例如前景色彩和字型)，來區分替代資料列。</span><span class="sxs-lookup"><span data-stu-id="6caf0-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="6caf0-107">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="6caf0-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="6caf0-108">另請參閱[How to:設定 Windows Form DataGridView 控制項使用設計工具的替代資料列樣式](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="6caf0-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="6caf0-109">以程式設計方式設定替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="6caf0-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="6caf0-110">設定由 <xref:System.Windows.Forms.DataGridView> 的 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> 屬性所傳回之 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6caf0-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="6caf0-111">使用 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> 屬性所指定的樣式，會覆寫在資料行和 <xref:System.Windows.Forms.DataGridView> 層級上所指定的樣式，但會由在個別資料列和儲存格層級設定的樣式所覆寫。</span><span class="sxs-lookup"><span data-stu-id="6caf0-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="6caf0-112">如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6caf0-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6caf0-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6caf0-113">Compiling the Code</span></span>  
 <span data-ttu-id="6caf0-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6caf0-114">This example requires:</span></span>  
  
-   <span data-ttu-id="6caf0-115">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="6caf0-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="6caf0-116">
  <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6caf0-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6caf0-117">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6caf0-117">Robust Programming</span></span>  
 <span data-ttu-id="6caf0-118">若要達到最大延展性，您應該在使用相同樣式的多個資料列、資料行或儲存格之間共用 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個項目的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="6caf0-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="6caf0-119">如需詳細資訊，請參閱 <<c0> [ 縮放 Windows Form DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6caf0-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6caf0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6caf0-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="6caf0-121">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="6caf0-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6caf0-122">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="6caf0-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6caf0-123">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="6caf0-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6caf0-124">如何：設定 Windows Form DataGridView 控制項中的 字型和色彩樣式</span><span class="sxs-lookup"><span data-stu-id="6caf0-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)

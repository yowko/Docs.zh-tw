---
title: Windows Form DataGridView 控制項中的基本格式化和樣式設定
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: 3d185b93f1e040ae320afbfd3e2b010bbf9ca624
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707075"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ba66d-102">Windows Form DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="ba66d-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ba66d-103">`DataGridView`控制項可讓您輕鬆地定義儲存格的基本外觀和顯示格式的資料格的值。</span><span class="sxs-lookup"><span data-stu-id="ba66d-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="ba66d-104">您可以定義外觀和格式樣式的個別儲存格、 特定的資料行和資料列中的資料格或控制項中的所有儲存格所設定的屬性`DataGridViewCellStyle`透過各種存取物件`DataGridView`控制屬性。</span><span class="sxs-lookup"><span data-stu-id="ba66d-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="ba66d-105">此外，您可以修改這些樣式，以動態方式會根據所處理的因素，例如儲存格的值`CellFormatting`事件。</span><span class="sxs-lookup"><span data-stu-id="ba66d-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba66d-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="ba66d-106">In This Section</span></span>  
 <span data-ttu-id="ba66d-107">[如何：變更 [框線] 及 Windows Form DataGridView 控制項中的格線樣式](change-the-border-and-gridline-styles-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="ba66d-107">[How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md)</span></span>  
 <span data-ttu-id="ba66d-108">描述如何設定`DataGridView`定義控制項的框線和儲存格之間的界限行的外觀屬性。</span><span class="sxs-lookup"><span data-stu-id="ba66d-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="ba66d-109">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="ba66d-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ba66d-110">描述`DataGridViewCellStyle`類別和該型別的屬性來定義儲存格控制項中顯示的方式互動的方式。</span><span class="sxs-lookup"><span data-stu-id="ba66d-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="ba66d-111">如何：為 Windows Form DataGridView 控制項中的預設儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="ba66d-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ba66d-112">描述如何使用`DataGridViewCellStyle`屬性，以定義特定的資料列和資料行中，並在整個控制項的儲存格的預設外觀。</span><span class="sxs-lookup"><span data-stu-id="ba66d-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="ba66d-113">如何：格式資料中的 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="ba66d-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ba66d-114">描述如何格式化使用的儲存格顯示值`DataGridViewCellStyle`屬性。</span><span class="sxs-lookup"><span data-stu-id="ba66d-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="ba66d-115">如何：設定 Windows Form DataGridView 控制項中的 字型和色彩樣式</span><span class="sxs-lookup"><span data-stu-id="ba66d-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ba66d-116">描述如何使用`DefaultCellStyle`屬性來設定基本控制項中顯示的所有儲存格的特性。</span><span class="sxs-lookup"><span data-stu-id="ba66d-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="ba66d-117">如何：設定 Windows Form DataGridView 控制項中替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="ba66d-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ba66d-118">描述如何使用替代的資料列會顯示不同的控制項中建立類似 ledger 的效果。</span><span class="sxs-lookup"><span data-stu-id="ba66d-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="ba66d-119">如何：使用資料列範本自訂 Windows Form DataGridView 控制項中的資料列</span><span class="sxs-lookup"><span data-stu-id="ba66d-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="ba66d-120">描述如何使用`RowTemplate`若要設定將用於在控制項中的所有資料列的資料列屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba66d-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ba66d-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="ba66d-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="ba66d-122">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="ba66d-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="ba66d-123">提供參考文件<xref:System.Windows.Forms.DataGridViewCellStyle>類別。</span><span class="sxs-lookup"><span data-stu-id="ba66d-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="ba66d-124">提供參考文件<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。</span><span class="sxs-lookup"><span data-stu-id="ba66d-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="ba66d-125">提供參考文件<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ba66d-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ba66d-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="ba66d-126">Related Sections</span></span>  
 [<span data-ttu-id="ba66d-127">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="ba66d-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ba66d-128">提供主題描述自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。</span><span class="sxs-lookup"><span data-stu-id="ba66d-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="ba66d-129">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="ba66d-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="ba66d-130">提供描述常用的主題使用的儲存格、 資料列和資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba66d-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba66d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba66d-131">See also</span></span>
- [<span data-ttu-id="ba66d-132">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="ba66d-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)

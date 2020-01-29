---
title: DataGridView 控制項中的基本格式化和樣式設定
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732005"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="da719-102">Windows Form DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="da719-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="da719-103">`DataGridView` 控制項可讓您輕鬆地定義資料格的基本外觀，以及儲存格值的顯示格式。</span><span class="sxs-lookup"><span data-stu-id="da719-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="da719-104">您可以針對特定資料行和資料列中的儲存格，或是針對控制項中的所有資料格，藉由設定透過各種 `DataGridView` 控制項屬性存取之 `DataGridViewCellStyle` 物件的屬性，來定義其外觀和格式設定樣式。</span><span class="sxs-lookup"><span data-stu-id="da719-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="da719-105">此外，您可以藉由處理 `CellFormatting` 事件，以動態方式根據因素（例如資料格值）來修改這些樣式。</span><span class="sxs-lookup"><span data-stu-id="da719-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da719-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="da719-106">In This Section</span></span>  
 [<span data-ttu-id="da719-107">操作說明：變更 Windows Forms DataGridView 控制項中的框線和格線樣式</span><span class="sxs-lookup"><span data-stu-id="da719-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="da719-108">描述如何設定 `DataGridView` 屬性，以定義控制項框線的外觀和儲存格之間的邊界線。</span><span class="sxs-lookup"><span data-stu-id="da719-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="da719-109">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="da719-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da719-110">描述 `DataGridViewCellStyle` 類別，以及該類型的屬性如何互動，以定義如何在控制項中顯示儲存格。</span><span class="sxs-lookup"><span data-stu-id="da719-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="da719-111">操作說明：設定 Windows Forms DataGridView 控制項的預設儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="da719-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da719-112">描述如何使用 `DataGridViewCellStyle` 屬性，在特定的資料列和資料行以及整個控制項中，定義儲存格的預設面板。</span><span class="sxs-lookup"><span data-stu-id="da719-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="da719-113">操作說明：格式化 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="da719-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da719-114">描述如何使用 `DataGridViewCellStyle` 屬性來格式化儲存格的顯示值。</span><span class="sxs-lookup"><span data-stu-id="da719-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="da719-115">操作說明：設定 Windows Forms DataGridView 控制項的字型和色彩樣式</span><span class="sxs-lookup"><span data-stu-id="da719-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da719-116">描述如何使用 [`DefaultCellStyle`] 屬性，為控制項中的所有儲存格設定基本顯示特性。</span><span class="sxs-lookup"><span data-stu-id="da719-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="da719-117">操作說明：設定 Windows Forms DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="da719-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da719-118">描述如何使用以不同方式顯示的交替資料列，在控制項中建立類似總帳的效果。</span><span class="sxs-lookup"><span data-stu-id="da719-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="da719-119">操作說明：在 Windows Forms DataGridView 控制項中使用資料列範本自訂資料列</span><span class="sxs-lookup"><span data-stu-id="da719-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="da719-120">描述如何使用 `RowTemplate` 屬性來設定將用於控制項中所有資料列的資料列屬性。</span><span class="sxs-lookup"><span data-stu-id="da719-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="da719-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="da719-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="da719-122">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="da719-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="da719-123">提供 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別的參考檔。</span><span class="sxs-lookup"><span data-stu-id="da719-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="da719-124">提供 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的參考檔。</span><span class="sxs-lookup"><span data-stu-id="da719-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="da719-125">提供 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> 屬性的參考檔。</span><span class="sxs-lookup"><span data-stu-id="da719-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da719-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="da719-126">Related Sections</span></span>  
 [<span data-ttu-id="da719-127">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="da719-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="da719-128">提供主題描述自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。</span><span class="sxs-lookup"><span data-stu-id="da719-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="da719-129">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="da719-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="da719-130">提供描述常用資料格、資料列和資料行屬性的主題。</span><span class="sxs-lookup"><span data-stu-id="da719-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da719-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="da719-131">See also</span></span>

- [<span data-ttu-id="da719-132">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="da719-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)

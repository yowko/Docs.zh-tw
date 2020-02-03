---
title: 自訂 DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744019"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="37f29-102">自訂 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="37f29-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="37f29-103">`DataGridView` 控制項提供數個屬性，可讓您用來調整其資料格、資料列和資料行的外觀和基本行為（外觀與風格）。</span><span class="sxs-lookup"><span data-stu-id="37f29-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="37f29-104">不過，如果您有超出 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別功能的特殊需求，您也可以透過建立自訂資料格、資料行和資料列的方式，為控制項執行主控描繪或擴充其功能。</span><span class="sxs-lookup"><span data-stu-id="37f29-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="37f29-105">若要自行繪製儲存格和資料列，您可以處理各種 `DataGridView` 繪製事件。</span><span class="sxs-lookup"><span data-stu-id="37f29-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="37f29-106">若要修改現有的功能或提供新的功能，您可以建立衍生自現有 `DataGridViewCell`、`DataGridViewColumn`和 `DataGridViewRow` 類型的專屬類型。</span><span class="sxs-lookup"><span data-stu-id="37f29-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="37f29-107">您也可以藉由建立衍生型別來提供新的編輯功能，以在儲存格處於編輯模式時，顯示您所選擇的控制項。</span><span class="sxs-lookup"><span data-stu-id="37f29-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37f29-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="37f29-108">In This Section</span></span>  
 [<span data-ttu-id="37f29-109">如何：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀</span><span class="sxs-lookup"><span data-stu-id="37f29-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="37f29-110">描述如何處理 <xref:System.Windows.Forms.DataGridView.CellPainting> 事件，以便手動繪製儲存格。</span><span class="sxs-lookup"><span data-stu-id="37f29-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="37f29-111">如何：在 Windows Forms DataGridView 控制項中自訂資料列的外觀</span><span class="sxs-lookup"><span data-stu-id="37f29-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="37f29-112">描述如何處理 <xref:System.Windows.Forms.DataGridView.RowPrePaint> 和 <xref:System.Windows.Forms.DataGridView.RowPostPaint> 事件，以便使用自訂的漸層背景和跨越多個資料行的內容繪製資料列。</span><span class="sxs-lookup"><span data-stu-id="37f29-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="37f29-113">操作說明：擴充儲存格和資料行的行為和外觀以自訂 Windows Forms DataGridView 控制項中的儲存格和資料行</span><span class="sxs-lookup"><span data-stu-id="37f29-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="37f29-114">描述如何建立從 `DataGridViewCell` 和 `DataGridViewColumn` 衍生的自訂類型，以便在滑鼠指標停留在資料格上時反白顯示。</span><span class="sxs-lookup"><span data-stu-id="37f29-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="37f29-115">操作說明：停用 Windows Forms DataGridView 控制項按鈕資料行中的按鈕</span><span class="sxs-lookup"><span data-stu-id="37f29-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="37f29-116">描述如何建立從 <xref:System.Windows.Forms.DataGridViewButtonCell> 和 <xref:System.Windows.Forms.DataGridViewButtonColumn> 衍生的自訂類型，以便在按鈕資料行中顯示已停用的按鈕。</span><span class="sxs-lookup"><span data-stu-id="37f29-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="37f29-117">操作說明：Windows Forms DataGridView 儲存格中的主控制項</span><span class="sxs-lookup"><span data-stu-id="37f29-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="37f29-118">描述如何執行 `IDataGridViewEditingControl` 介面，並建立從 `DataGridViewCell` 和 `DataGridViewColumn` 衍生的自訂類型，以便在儲存格處於編輯模式時顯示 <xref:System.Windows.Forms.DateTimePicker> 控制項。</span><span class="sxs-lookup"><span data-stu-id="37f29-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="37f29-119">參考</span><span class="sxs-lookup"><span data-stu-id="37f29-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="37f29-120">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="37f29-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="37f29-121">提供 <xref:System.Windows.Forms.DataGridViewCell> 類別的參考檔。</span><span class="sxs-lookup"><span data-stu-id="37f29-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="37f29-122">提供 <xref:System.Windows.Forms.DataGridViewRow> 類別的參考檔。</span><span class="sxs-lookup"><span data-stu-id="37f29-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="37f29-123">提供 <xref:System.Windows.Forms.DataGridViewColumn> 類別的參考檔。</span><span class="sxs-lookup"><span data-stu-id="37f29-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="37f29-124">提供 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面的參考檔。</span><span class="sxs-lookup"><span data-stu-id="37f29-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37f29-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="37f29-125">Related Sections</span></span>  
 [<span data-ttu-id="37f29-126">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="37f29-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="37f29-127">提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="37f29-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f29-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37f29-128">See also</span></span>

- [<span data-ttu-id="37f29-129">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="37f29-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="37f29-130">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="37f29-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)

---
title: 自訂 Windows Form DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 92bbace4d0869aca67025f1e4ac8c451fe073219
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529840"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="99068-102">自訂 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="99068-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="99068-103">`DataGridView`控制項也提供數個屬性可讓您調整的外觀和其資料格、 資料列和資料行的基本行為 （外觀及操作）。</span><span class="sxs-lookup"><span data-stu-id="99068-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="99068-104">如果您有特殊需求的功能，<xref:System.Windows.Forms.DataGridViewCellStyle>類別，不過，您也可以實作主控描繪控制項或建立自訂的資料格、 資料行和資料列來擴充其功能。</span><span class="sxs-lookup"><span data-stu-id="99068-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="99068-105">若要繪製儲存格和資料列自行，您可以處理各種`DataGridView`繪製事件。</span><span class="sxs-lookup"><span data-stu-id="99068-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="99068-106">若要修改現有的功能，或提供新功能，您可以建立自己的型別衍生自現有`DataGridViewCell`， `DataGridViewColumn`，和`DataGridViewRow`型別。</span><span class="sxs-lookup"><span data-stu-id="99068-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="99068-107">您也可以藉由建立衍生的類型中顯示您選擇的儲存格處於編輯模式的控制項，提供新的編輯功能。</span><span class="sxs-lookup"><span data-stu-id="99068-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99068-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="99068-108">In This Section</span></span>  
 [<span data-ttu-id="99068-109">操作說明：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀</span><span class="sxs-lookup"><span data-stu-id="99068-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="99068-110">描述如何處理<xref:System.Windows.Forms.DataGridView.CellPainting>事件才能繪製儲存格大小以手動方式。</span><span class="sxs-lookup"><span data-stu-id="99068-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="99068-111">操作說明：在 Windows Forms DataGridView 控制項中自訂資料列的外觀</span><span class="sxs-lookup"><span data-stu-id="99068-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="99068-112">描述如何處理<xref:System.Windows.Forms.DataGridView.RowPrePaint>和<xref:System.Windows.Forms.DataGridView.RowPostPaint>事件，以繪製自訂的漸層背景的資料列，並在此內容跨越多個資料行。</span><span class="sxs-lookup"><span data-stu-id="99068-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="99068-113">操作說明：擴充儲存格和資料行的行為和外觀以自訂 Windows Forms DataGridView 控制項中的儲存格和資料行</span><span class="sxs-lookup"><span data-stu-id="99068-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="99068-114">描述如何建立自訂型別衍生自`DataGridViewCell`和`DataGridViewColumn`才能將滑鼠指標停留在其上時，反白顯示資料格。</span><span class="sxs-lookup"><span data-stu-id="99068-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="99068-115">操作說明：停用 Windows Forms DataGridView 控制項按鈕資料行中的按鈕</span><span class="sxs-lookup"><span data-stu-id="99068-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="99068-116">描述如何建立自訂型別衍生自<xref:System.Windows.Forms.DataGridViewButtonCell>和<xref:System.Windows.Forms.DataGridViewButtonColumn>才能在按鈕資料行中顯示已停用的按鈕。</span><span class="sxs-lookup"><span data-stu-id="99068-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="99068-117">操作說明：Windows Forms DataGridView 儲存格中的主控制項</span><span class="sxs-lookup"><span data-stu-id="99068-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="99068-118">描述如何實作`IDataGridViewEditingControl`介面，並建立自訂型別衍生自`DataGridViewCell`和`DataGridViewColumn`才能顯示<xref:System.Windows.Forms.DateTimePicker>控制的儲存格位於編輯模式。</span><span class="sxs-lookup"><span data-stu-id="99068-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="99068-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="99068-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="99068-120">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="99068-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="99068-121">提供參考文件<xref:System.Windows.Forms.DataGridViewCell>類別。</span><span class="sxs-lookup"><span data-stu-id="99068-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="99068-122">提供參考文件<xref:System.Windows.Forms.DataGridViewRow>類別。</span><span class="sxs-lookup"><span data-stu-id="99068-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="99068-123">提供參考文件<xref:System.Windows.Forms.DataGridViewColumn>類別。</span><span class="sxs-lookup"><span data-stu-id="99068-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="99068-124">提供參考文件<xref:System.Windows.Forms.IDataGridViewEditingControl>介面。</span><span class="sxs-lookup"><span data-stu-id="99068-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99068-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="99068-125">Related Sections</span></span>  
 [<span data-ttu-id="99068-126">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="99068-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="99068-127">提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="99068-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99068-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99068-128">See Also</span></span>  
 [<span data-ttu-id="99068-129">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="99068-129">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="99068-130">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="99068-130">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)

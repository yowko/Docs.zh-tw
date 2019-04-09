---
title: 自訂 Windows Form DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: ab8d1f07c608aca4f14f5e73860f8c3e263a4610
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091378"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="5dd1c-102">自訂 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5dd1c-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5dd1c-103">`DataGridView`控制項提供您可用來調整的外觀和其資料格、 資料列和資料行的基本行為 （外觀及操作） 的數個屬性。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="5dd1c-104">如果您有特殊需求的功能之外<xref:System.Windows.Forms.DataGridViewCellStyle>類別中，不過，您也可以實作主控描繪控制項或擴充其功能，藉由建立自訂的資料格、 資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="5dd1c-105">若要繪製的儲存格和資料列自行，您可以處理各種`DataGridView`繪製事件。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="5dd1c-106">若要修改現有的功能，或提供新功能，您可以建立自己的型別衍生自現有`DataGridViewCell`， `DataGridViewColumn`，和`DataGridViewRow`型別。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="5dd1c-107">您也可以建立顯示您選擇的儲存格處於編輯模式的控制項的衍生型別，以提供新的編輯功能。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5dd1c-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="5dd1c-108">In This Section</span></span>  
 [<span data-ttu-id="5dd1c-109">HOW TO：自訂 Windows Forms DataGridView 控制項的儲存格外觀</span><span class="sxs-lookup"><span data-stu-id="5dd1c-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="5dd1c-110">描述如何處理<xref:System.Windows.Forms.DataGridView.CellPainting>手動事件，以繪製儲存格。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="5dd1c-111">HOW TO：自訂 Windows Forms DataGridView 控制項的資料列外觀</span><span class="sxs-lookup"><span data-stu-id="5dd1c-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="5dd1c-112">描述如何處理<xref:System.Windows.Forms.DataGridView.RowPrePaint>和<xref:System.Windows.Forms.DataGridView.RowPostPaint>事件以繪製自訂的漸層背景的資料列和內容，跨越多個資料行。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="5dd1c-113">HOW TO：擴充 Windows Forms DataGridView 控制項之儲存格和資料行的行為和外觀，以自訂儲存格和資料行</span><span class="sxs-lookup"><span data-stu-id="5dd1c-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="5dd1c-114">描述如何建立自訂的型別衍生自`DataGridViewCell`和`DataGridViewColumn`才能將滑鼠指標停留在其上時，反白顯示的資料格。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="5dd1c-115">HOW TO：停用 Windows Forms DataGridView 控制項按鈕資料行的按鈕</span><span class="sxs-lookup"><span data-stu-id="5dd1c-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="5dd1c-116">描述如何建立自訂的型別衍生自<xref:System.Windows.Forms.DataGridViewButtonCell>和<xref:System.Windows.Forms.DataGridViewButtonColumn>若要在按鈕資料行中顯示已停用的按鈕。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="5dd1c-117">HOW TO：Windows Forms DataGridView 儲存格的主控制項</span><span class="sxs-lookup"><span data-stu-id="5dd1c-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="5dd1c-118">描述如何實作`IDataGridViewEditingControl`介面，並建立自訂的型別衍生自`DataGridViewCell`並`DataGridViewColumn`以顯示<xref:System.Windows.Forms.DateTimePicker>控制當儲存格處於編輯模式。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5dd1c-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="5dd1c-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="5dd1c-120">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="5dd1c-121">提供參考文件<xref:System.Windows.Forms.DataGridViewCell>類別。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="5dd1c-122">提供參考文件<xref:System.Windows.Forms.DataGridViewRow>類別。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="5dd1c-123">提供參考文件<xref:System.Windows.Forms.DataGridViewColumn>類別。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="5dd1c-124">提供參考文件<xref:System.Windows.Forms.IDataGridViewEditingControl>介面。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5dd1c-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="5dd1c-125">Related Sections</span></span>  
 [<span data-ttu-id="5dd1c-126">Windows Form DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="5dd1c-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5dd1c-127">提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="5dd1c-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd1c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dd1c-128">See also</span></span>

- [<span data-ttu-id="5dd1c-129">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5dd1c-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="5dd1c-130">Windows Form DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="5dd1c-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)

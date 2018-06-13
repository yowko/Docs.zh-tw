---
title: 調整 Windows Form DataGridView 控制項中資料行和資料列的大小
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 1e501d124ccec749537d319b992c5caf00b025f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536951"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a14f4-102">調整 Windows Form DataGridView 控制項中資料行和資料列的大小</span><span class="sxs-lookup"><span data-stu-id="a14f4-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a14f4-103">`DataGridView`控制項提供許多自訂其資料行和資料列的調整大小行為的選項。</span><span class="sxs-lookup"><span data-stu-id="a14f4-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="a14f4-104">一般而言，`DataGridView`不調整大小的資料格根據其內容。</span><span class="sxs-lookup"><span data-stu-id="a14f4-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="a14f4-105">相反地，它們會裁剪任何大於儲存格的顯示值。</span><span class="sxs-lookup"><span data-stu-id="a14f4-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="a14f4-106">如果內容可以顯示為字串，則資料格會顯示其工具提示中。</span><span class="sxs-lookup"><span data-stu-id="a14f4-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="a14f4-107">根據預設，使用者可以拖曳資料列、 資料行和滑鼠來顯示詳細資訊的行首分割線。</span><span class="sxs-lookup"><span data-stu-id="a14f4-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="a14f4-108">使用者也可以按兩下分割線，自動調整大小的相關資料列、 資料行或標頭寬線根據其內容。</span><span class="sxs-lookup"><span data-stu-id="a14f4-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="a14f4-109">`DataGridView`控制項提供屬性、 方法和事件，可讓您自訂或停用所有這些使用者導向的行為。</span><span class="sxs-lookup"><span data-stu-id="a14f4-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="a14f4-110">此外，您也可以透過程式設計方式調整資料列、 資料行和標頭，以適合其內容，或者您可以將其設定為每當內容變更時自動調整本身大小。</span><span class="sxs-lookup"><span data-stu-id="a14f4-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="a14f4-111">您也可以設定自動分割中您所指定的比例控制項可用寬度的資料行。</span><span class="sxs-lookup"><span data-stu-id="a14f4-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a14f4-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="a14f4-112">In This Section</span></span>  
 [<span data-ttu-id="a14f4-113">Windows Forms DataGridView 控制項中的調整大小選項</span><span class="sxs-lookup"><span data-stu-id="a14f4-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a14f4-114">描述調整資料列、 資料行和標頭的選項。</span><span class="sxs-lookup"><span data-stu-id="a14f4-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="a14f4-115">也提供調整大小相關的屬性和方法的詳細資訊，並說明常見使用案例。</span><span class="sxs-lookup"><span data-stu-id="a14f4-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="a14f4-116">Windows Forms DataGridView 控制項中的資料行填入模式</span><span class="sxs-lookup"><span data-stu-id="a14f4-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a14f4-117">描述資料行填入模式中的詳細資料，並提供示範程式碼，可讓您試驗資料行填入模式與其他模式。</span><span class="sxs-lookup"><span data-stu-id="a14f4-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="a14f4-118">操作說明：設定 Windows Forms DataGridView 控制項的縮放模式</span><span class="sxs-lookup"><span data-stu-id="a14f4-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a14f4-119">描述如何設定一般用途的調整大小模式。</span><span class="sxs-lookup"><span data-stu-id="a14f4-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="a14f4-120">操作說明：以程式設計方式調整儲存格大小以符合 Windows Forms DataGridView 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="a14f4-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="a14f4-121">提供示範程式碼，可讓您試驗以程式設計方式調整大小。</span><span class="sxs-lookup"><span data-stu-id="a14f4-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="a14f4-122">操作說明：在 Windows Forms DataGridView 控制項的內容變更時自動調整儲存格大小</span><span class="sxs-lookup"><span data-stu-id="a14f4-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="a14f4-123">提供示範程式碼，可讓您試驗自動調整大小模式。</span><span class="sxs-lookup"><span data-stu-id="a14f4-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a14f4-124">參考資料</span><span class="sxs-lookup"><span data-stu-id="a14f4-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="a14f4-125">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="a14f4-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14f4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a14f4-126">See Also</span></span>  
 [<span data-ttu-id="a14f4-127">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="a14f4-127">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)

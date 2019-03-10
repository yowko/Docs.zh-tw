---
title: 調整 Windows Form DataGridView 控制項中資料行和資料列的大小
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8eae5dafa314bb293f55a780f6be67d06f376004
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709648"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b126f-102">調整 Windows Form DataGridView 控制項中資料行和資料列的大小</span><span class="sxs-lookup"><span data-stu-id="b126f-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b126f-103">`DataGridView`控制項提供許多選項可以自訂其資料行和資料列的調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="b126f-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="b126f-104">一般而言，`DataGridView`不調整大小的資料格根據其內容。</span><span class="sxs-lookup"><span data-stu-id="b126f-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="b126f-105">相反地，它們會裁剪掉任何大於資料格的顯示值。</span><span class="sxs-lookup"><span data-stu-id="b126f-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="b126f-106">如果內容可以顯示為字串，則資料格會顯示它在工具提示。</span><span class="sxs-lookup"><span data-stu-id="b126f-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="b126f-107">根據預設，使用者可以拖曳資料列、 資料行和標頭分隔線，使用滑鼠，以顯示詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b126f-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="b126f-108">使用者也可以按兩下分割線，以自動調整大小相關聯的資料列、 資料行或標頭群組列根據其內容。</span><span class="sxs-lookup"><span data-stu-id="b126f-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="b126f-109">`DataGridView`控制項提供屬性、 方法和事件可讓您自訂或停用所有這些使用者導向的行為。</span><span class="sxs-lookup"><span data-stu-id="b126f-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="b126f-110">此外，您也可以以程式設計方式調整資料列、 資料行和標頭，以適合其內容，或者您可以將其設定為每當內容變更時自動調整本身大小。</span><span class="sxs-lookup"><span data-stu-id="b126f-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="b126f-111">您也可以設定自動將您指定的比例控制項可用寬度的資料行。</span><span class="sxs-lookup"><span data-stu-id="b126f-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b126f-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="b126f-112">In This Section</span></span>  
 [<span data-ttu-id="b126f-113">Windows Forms DataGridView 控制項中的調整大小選項</span><span class="sxs-lookup"><span data-stu-id="b126f-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b126f-114">描述的選項，調整資料列、 資料行和標頭。</span><span class="sxs-lookup"><span data-stu-id="b126f-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="b126f-115">也提供調整大小相關的屬性和方法的詳細資訊，並描述常見使用案例。</span><span class="sxs-lookup"><span data-stu-id="b126f-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="b126f-116">Windows Forms DataGridView 控制項中的資料行填入模式</span><span class="sxs-lookup"><span data-stu-id="b126f-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b126f-117">描述資料行填入模式的詳細資訊，並提供示範程式碼，可供您試驗資料行填入模式與其他模式。</span><span class="sxs-lookup"><span data-stu-id="b126f-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="b126f-118">如何：設定 Windows Forms DataGridView 控制項的縮放模式</span><span class="sxs-lookup"><span data-stu-id="b126f-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b126f-119">描述如何設定一般用途的縮放模式。</span><span class="sxs-lookup"><span data-stu-id="b126f-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="b126f-120">如何：以程式設計方式調整大小以符合內容，在 Windows Form DataGridView 控制項中的資料格</span><span class="sxs-lookup"><span data-stu-id="b126f-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="b126f-121">提供示範程式碼，可供您試驗以程式設計方式調整大小。</span><span class="sxs-lookup"><span data-stu-id="b126f-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="b126f-122">如何：自動調整大小的資料格，當 Windows Form DataGridView 控制項中的內容變更</span><span class="sxs-lookup"><span data-stu-id="b126f-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="b126f-123">提供示範程式碼，可供您試驗自動調整大小模式。</span><span class="sxs-lookup"><span data-stu-id="b126f-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b126f-124">參考資料</span><span class="sxs-lookup"><span data-stu-id="b126f-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b126f-125">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="b126f-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b126f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b126f-126">See also</span></span>
- [<span data-ttu-id="b126f-127">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="b126f-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)

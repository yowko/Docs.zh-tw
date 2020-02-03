---
title: 調整 DataGridView 控制項中的資料行和資料列大小
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742407"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="26869-102">調整 Windows Form DataGridView 控制項中的資料行和資料列的大小</span><span class="sxs-lookup"><span data-stu-id="26869-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="26869-103">`DataGridView` 控制項提供許多選項，可讓您自訂其資料行和資料列的調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="26869-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="26869-104">一般來說，`DataGridView` 的資料格不會根據其內容調整大小。</span><span class="sxs-lookup"><span data-stu-id="26869-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="26869-105">相反地，它們會裁剪大於儲存格的任何顯示值。</span><span class="sxs-lookup"><span data-stu-id="26869-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="26869-106">如果內容可以顯示為字串，資料格就會顯示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="26869-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="26869-107">根據預設，使用者可以使用滑鼠拖曳資料列、資料行和標頭分隔線，以顯示詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="26869-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="26869-108">使用者也可以按兩下分隔線，根據其內容自動調整相關列、資料行或標頭的大小。</span><span class="sxs-lookup"><span data-stu-id="26869-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="26869-109">`DataGridView` 控制項提供屬性、方法和事件，可讓您自訂或停用所有這些使用者導向的行為。</span><span class="sxs-lookup"><span data-stu-id="26869-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="26869-110">此外，您可以透過程式設計的方式調整資料列、資料行和標頭的大小，以符合其內容，或者您可以設定它們在內容變更時自動調整其大小。</span><span class="sxs-lookup"><span data-stu-id="26869-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="26869-111">您也可以將資料行設定為自動將控制項的可用寬度除以您指定的比例。</span><span class="sxs-lookup"><span data-stu-id="26869-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26869-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="26869-112">In This Section</span></span>  
 [<span data-ttu-id="26869-113">Windows Forms DataGridView 控制項中的調整大小選項</span><span class="sxs-lookup"><span data-stu-id="26869-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="26869-114">描述調整資料列、資料行和標頭的選項。</span><span class="sxs-lookup"><span data-stu-id="26869-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="26869-115">也會提供有關調整大小相關屬性和方法的詳細資料，並說明常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="26869-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="26869-116">Windows Forms DataGridView 控制項中的資料行填入模式</span><span class="sxs-lookup"><span data-stu-id="26869-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="26869-117">詳細描述資料行填滿模式，並提供示範程式碼，可讓您用來試驗資料行填滿模式和其他模式。</span><span class="sxs-lookup"><span data-stu-id="26869-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="26869-118">操作說明：設定 Windows Forms DataGridView 控制項的縮放模式</span><span class="sxs-lookup"><span data-stu-id="26869-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="26869-119">說明如何設定一般用途的調整大小模式。</span><span class="sxs-lookup"><span data-stu-id="26869-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="26869-120">操作說明：以程式設計方式調整儲存格大小以符合 Windows Forms DataGridView 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="26869-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="26869-121">提供示範程式碼，可讓您用來試驗以程式設計方式調整大小。</span><span class="sxs-lookup"><span data-stu-id="26869-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="26869-122">操作說明：在 Windows Forms DataGridView 控制項的內容變更時自動調整儲存格大小</span><span class="sxs-lookup"><span data-stu-id="26869-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="26869-123">提供示範程式碼，可讓您用來試驗自動調整大小模式。</span><span class="sxs-lookup"><span data-stu-id="26869-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="26869-124">參考</span><span class="sxs-lookup"><span data-stu-id="26869-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="26869-125">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="26869-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26869-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26869-126">See also</span></span>

- [<span data-ttu-id="26869-127">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="26869-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)

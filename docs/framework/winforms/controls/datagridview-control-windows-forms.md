---
title: DataGridView 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: 86e96045b7de580b7cefd0262369ce860d00e234
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124315"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="addb9-102">DataGridView 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="addb9-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="addb9-103">`DataGridView` 控制項以表格式顯示資料，是一項功能強大、有彈性的方式。</span><span class="sxs-lookup"><span data-stu-id="addb9-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="addb9-104">您可以使用 `DataGridView` 控制來顯示少量資料的唯讀檢視，或者您可以調整它的大小，以顯示非常大的資料集之可編輯檢視。</span><span class="sxs-lookup"><span data-stu-id="addb9-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="addb9-105">您可以數種方式擴充 `DataGridView` 控制項，以建置自訂行為到您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="addb9-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="addb9-106">例如，您可以程式設計方式指定自己的排序演算法，而且也可以建立自己的儲存格類型。</span><span class="sxs-lookup"><span data-stu-id="addb9-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="addb9-107">您可以在數種屬性間做選擇，輕鬆自訂 `DataGridView` 控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="addb9-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="addb9-108">許多類型的資料儲存區可用來做為資料來源，不然 `DataGridView` 控制項可在不使用與其繫結的資料來源之情況下運作。</span><span class="sxs-lookup"><span data-stu-id="addb9-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="addb9-109">本節中的主題說明您可以用來將 `DataGridView` 功能建置在應用程式中的概念和技術。</span><span class="sxs-lookup"><span data-stu-id="addb9-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="addb9-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="addb9-110">In This Section</span></span>  
 [<span data-ttu-id="addb9-111">DataGridView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="addb9-111">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="addb9-112">提供描述 Windows Form `DataGridView` 控制項架構和核心概念的主題。</span><span class="sxs-lookup"><span data-stu-id="addb9-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="addb9-113">Windows Form DataGridView 控制項的預設功能</span><span class="sxs-lookup"><span data-stu-id="addb9-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-114">描述當 Windows Form `DataGridView` 控制項繫結至資料來源時的預設外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="addb9-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="addb9-115">Windows Form DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="addb9-115">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-116">描述在 Windows Form `DataGridView` 控制項中用於顯示資料，並允許使用者修改或加入資料的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="addb9-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="addb9-117">Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="addb9-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="addb9-118">提供描述常用的儲存格、資料列和資料行屬性的主題。</span><span class="sxs-lookup"><span data-stu-id="addb9-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="addb9-119">Windows Form DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="addb9-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-120">提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="addb9-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="addb9-121">在 Windows Form DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="addb9-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-122">提供主題描述如何以手動方式或從外部資料來源將資料填入控制項。</span><span class="sxs-lookup"><span data-stu-id="addb9-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="addb9-123">調整 Windows Form DataGridView 控制項中資料行和資料列的大小</span><span class="sxs-lookup"><span data-stu-id="addb9-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-124">提供主題描述資料列和資料行大小可如何自動調整，以符合儲存格內容，或調整控制項可用寬度。</span><span class="sxs-lookup"><span data-stu-id="addb9-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="addb9-125">在 Windows Forms DataGridView 控制項中排序資料</span><span class="sxs-lookup"><span data-stu-id="addb9-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-126">提供描述控制項中排序功能的主題。</span><span class="sxs-lookup"><span data-stu-id="addb9-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="addb9-127">Windows Form DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="addb9-127">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-128">提供主題描述如何變更使用者加入和修改控制項資料的方式。</span><span class="sxs-lookup"><span data-stu-id="addb9-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="addb9-129">選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="addb9-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-130">提供主題描述控制項中儲存格、資料列和資料行的選取功能。</span><span class="sxs-lookup"><span data-stu-id="addb9-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="addb9-131">在 Windows Form DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="addb9-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="addb9-132">提供主題描述如何使用儲存格、資料列和資料行物件進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="addb9-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="addb9-133">自訂 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="addb9-133">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-134">提供主題描述自訂繪製 `DataGridView` 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。</span><span class="sxs-lookup"><span data-stu-id="addb9-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="addb9-135">Windows Form DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="addb9-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-136">提供主題描述處理大量資料時，如何有效率地使用控制項來避免發生效能問題。</span><span class="sxs-lookup"><span data-stu-id="addb9-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="addb9-137">Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠控制</span><span class="sxs-lookup"><span data-stu-id="addb9-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="addb9-138">描述使用者可如何透過鍵盤和滑鼠與 `DataGridView` 控制項互動。</span><span class="sxs-lookup"><span data-stu-id="addb9-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="addb9-139">Windows Form DataGridView 和 DataGrid 控制項之間的差異</span><span class="sxs-lookup"><span data-stu-id="addb9-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="addb9-140">描述 `DataGridView` 控制項如何改良並取代 <xref:System.Windows.Forms.DataGrid> 控制項。</span><span class="sxs-lookup"><span data-stu-id="addb9-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="addb9-141">另請參閱[使用設計工具搭配 Windows Form DataGridView 控制項](using-the-designer-with-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="addb9-141">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="addb9-142">參考資料</span><span class="sxs-lookup"><span data-stu-id="addb9-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="addb9-143">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="addb9-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="addb9-144">提供 <xref:System.Windows.Forms.BindingSource> 元件的參考文件。</span><span class="sxs-lookup"><span data-stu-id="addb9-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="addb9-145"><xref:System.Windows.Forms.DataGridView> 控制項和 <xref:System.Windows.Forms.BindingSource> 元件設計為可密切合作。</span><span class="sxs-lookup"><span data-stu-id="addb9-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="addb9-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="addb9-146">See also</span></span>

- [<span data-ttu-id="addb9-147">在 Windows Form 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="addb9-147">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)

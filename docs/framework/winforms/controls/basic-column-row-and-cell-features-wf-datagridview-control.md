---
title: DataGridView 控制項中的基本資料行、資料列和儲存格功能
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
ms.openlocfilehash: 02f8ad7e11a61e9434748a8b3b2f853f98b013d1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746225"
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e36d7-102">Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="e36d7-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e36d7-103">您可以藉由設定單一屬性來修改 `DataGridView` 資料格、資料列和資料行的許多基本行為。</span><span class="sxs-lookup"><span data-stu-id="e36d7-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="e36d7-104">本節中的主題將說明這些功能最常使用的幾個。</span><span class="sxs-lookup"><span data-stu-id="e36d7-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e36d7-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="e36d7-105">In This Section</span></span>  
 [<span data-ttu-id="e36d7-106">操作說明：隱藏 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="e36d7-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e36d7-107">描述如何防止特定資料行出現在控制項中。</span><span class="sxs-lookup"><span data-stu-id="e36d7-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="e36d7-108">操作說明：隱藏 Windows Forms DataGridView 控制項中的資料行行首</span><span class="sxs-lookup"><span data-stu-id="e36d7-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e36d7-109">描述如何防止資料行標頭出現在控制項中。</span><span class="sxs-lookup"><span data-stu-id="e36d7-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="e36d7-110">操作說明：啟用 Windows Forms DataGridView 控制項中的資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="e36d7-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e36d7-111">說明如何讓使用者重新排列控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="e36d7-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="e36d7-112">操作說明：凍結 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="e36d7-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e36d7-113">描述如何防止一或多個連續的資料行進行滾動。</span><span class="sxs-lookup"><span data-stu-id="e36d7-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="e36d7-114">操作說明：使 Windows Forms DataGridView 控制項中的資料行成為唯讀</span><span class="sxs-lookup"><span data-stu-id="e36d7-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e36d7-115">描述如何防止使用者編輯控制項中的特定資料行。</span><span class="sxs-lookup"><span data-stu-id="e36d7-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="e36d7-116">操作說明：防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="e36d7-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="e36d7-117">描述如何移除控制項底部新記錄的資料列，以防止使用者加入資料列。</span><span class="sxs-lookup"><span data-stu-id="e36d7-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="e36d7-118">同時說明如何防止使用者刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="e36d7-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="e36d7-119">操作說明：取得和設定 Windows Forms DataGridView 控制項中目前的儲存格</span><span class="sxs-lookup"><span data-stu-id="e36d7-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="e36d7-120">描述如何存取目前焦點在控制項中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="e36d7-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="e36d7-121">操作說明：顯示 Windows Form DataGridView 控制項的儲存格影像</span><span class="sxs-lookup"><span data-stu-id="e36d7-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e36d7-122">描述如何建立在每個資料格中顯示圖示的影像資料行。</span><span class="sxs-lookup"><span data-stu-id="e36d7-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e36d7-123">參考</span><span class="sxs-lookup"><span data-stu-id="e36d7-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="e36d7-124">提供控制項的參考檔。</span><span class="sxs-lookup"><span data-stu-id="e36d7-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e36d7-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="e36d7-125">Related Sections</span></span>  
 [<span data-ttu-id="e36d7-126">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="e36d7-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e36d7-127">提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="e36d7-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="e36d7-128">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="e36d7-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="e36d7-129">提供主題描述如何使用儲存格、資料列和資料行物件進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="e36d7-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36d7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e36d7-130">See also</span></span>

- [<span data-ttu-id="e36d7-131">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="e36d7-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="e36d7-132">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="e36d7-132">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)

---
title: Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
ms.openlocfilehash: 4c755d5f0c2e134b83beb27ebbd06080bad620b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115228"
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8e18f-102">Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="8e18f-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8e18f-103">許多的基本行為的`DataGridView`藉由設定單一屬性，則可以修改資料格、 資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="8e18f-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="8e18f-104">在本節中的主題會說明幾個最常使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="8e18f-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e18f-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="8e18f-105">In This Section</span></span>  
 [<span data-ttu-id="8e18f-106">如何：隱藏 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="8e18f-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8e18f-107">若要防止特定資料行出現在控制項中的說明。</span><span class="sxs-lookup"><span data-stu-id="8e18f-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="8e18f-108">如何：隱藏 Windows Form DataGridView 控制項中的資料行標頭</span><span class="sxs-lookup"><span data-stu-id="8e18f-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8e18f-109">描述如何顯示在控制項時，防止資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="8e18f-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="8e18f-110">如何：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="8e18f-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8e18f-111">描述如何讓使用者能夠重新排列控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="8e18f-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="8e18f-112">如何：凍結 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="8e18f-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8e18f-113">描述如何防止捲動的一或多個相鄰的資料行。</span><span class="sxs-lookup"><span data-stu-id="8e18f-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="8e18f-114">如何：讓唯讀的 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="8e18f-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8e18f-115">描述如何防止使用者編輯控制項中的特定資料行。</span><span class="sxs-lookup"><span data-stu-id="8e18f-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="8e18f-116">如何：防止資料列新增與 Windows Form DataGridView 控制項中刪除</span><span class="sxs-lookup"><span data-stu-id="8e18f-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="8e18f-117">描述如何移除底部的 加入資料列時，防止使用者控制項的新記錄的資料列。</span><span class="sxs-lookup"><span data-stu-id="8e18f-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="8e18f-118">同時描述如何防止使用者刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="8e18f-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="8e18f-119">如何：取得和設定 Windows Form DataGridView 控制項中的目前儲存格</span><span class="sxs-lookup"><span data-stu-id="8e18f-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="8e18f-120">描述如何存取目前焦點在控制項中的資料格。</span><span class="sxs-lookup"><span data-stu-id="8e18f-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="8e18f-121">如何：Windows Forms DataGridView 控制項的儲存格的顯示影像</span><span class="sxs-lookup"><span data-stu-id="8e18f-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8e18f-122">描述如何建立影像資料行，顯示每個資料格中的圖示。</span><span class="sxs-lookup"><span data-stu-id="8e18f-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8e18f-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="8e18f-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="8e18f-124">提供控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="8e18f-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8e18f-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="8e18f-125">Related Sections</span></span>  
 [<span data-ttu-id="8e18f-126">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="8e18f-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8e18f-127">提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="8e18f-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="8e18f-128">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="8e18f-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="8e18f-129">提供主題描述如何使用儲存格、資料列和資料行物件進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="8e18f-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e18f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e18f-130">See also</span></span>

- [<span data-ttu-id="8e18f-131">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="8e18f-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="8e18f-132">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="8e18f-132">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)

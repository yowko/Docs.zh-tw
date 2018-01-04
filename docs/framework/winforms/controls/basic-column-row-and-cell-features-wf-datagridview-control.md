---
title: "Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c70e1a88384041a2a1d958e48c672a961752202b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="87033-102">Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="87033-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="87033-103">許多的基本行為的`DataGridView`藉由設定單一屬性，則可以修改資料格、 列和資料行。</span><span class="sxs-lookup"><span data-stu-id="87033-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="87033-104">本節中的主題會說明有幾個最常使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="87033-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87033-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="87033-105">In This Section</span></span>  
 [<span data-ttu-id="87033-106">操作說明：隱藏 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="87033-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="87033-107">若要防止特定資料行出現在控制項中的說明。</span><span class="sxs-lookup"><span data-stu-id="87033-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="87033-108">操作說明：隱藏 Windows Forms DataGridView 控制項中的資料行行首</span><span class="sxs-lookup"><span data-stu-id="87033-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="87033-109">描述如何顯示在控制項時，防止資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="87033-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="87033-110">操作說明：啟用 Windows Forms DataGridView 控制項中的資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="87033-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="87033-111">描述如何讓使用者在控制項中的資料行重新排列。</span><span class="sxs-lookup"><span data-stu-id="87033-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="87033-112">操作說明：凍結 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="87033-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="87033-113">描述如何防止一個或多個相鄰的資料行捲動。</span><span class="sxs-lookup"><span data-stu-id="87033-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="87033-114">操作說明：使 Windows Forms DataGridView 控制項中的資料行成為唯讀</span><span class="sxs-lookup"><span data-stu-id="87033-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="87033-115">描述如何防止使用者編輯控制項中的特定資料行。</span><span class="sxs-lookup"><span data-stu-id="87033-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="87033-116">操作說明：防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="87033-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="87033-117">描述如何移除底部的控制項，以防止使用者加入資料列的新記錄的資料列。</span><span class="sxs-lookup"><span data-stu-id="87033-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="87033-118">同時描述如何防止使用者刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="87033-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="87033-119">操作說明：取得和設定 Windows Forms DataGridView 控制項中目前的儲存格</span><span class="sxs-lookup"><span data-stu-id="87033-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="87033-120">描述如何存取目前擁有焦點在控制項中的資料格。</span><span class="sxs-lookup"><span data-stu-id="87033-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="87033-121">操作說明：顯示 Windows Form DataGridView 控制項的儲存格影像</span><span class="sxs-lookup"><span data-stu-id="87033-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="87033-122">描述如何建立影像資料行，顯示每個資料格中的圖示。</span><span class="sxs-lookup"><span data-stu-id="87033-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="87033-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="87033-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="87033-124">提供控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="87033-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="87033-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="87033-125">Related Sections</span></span>  
 [<span data-ttu-id="87033-126">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="87033-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="87033-127">提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="87033-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="87033-128">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="87033-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="87033-129">提供主題描述如何使用儲存格、資料列和資料行物件進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="87033-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87033-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="87033-130">See Also</span></span>  
 [<span data-ttu-id="87033-131">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="87033-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="87033-132">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="87033-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)

---
title: "選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 888fb1cbd960c006dc2705a2b0bd66c038a926f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="69e04-102">選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="69e04-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="69e04-103">`DataGridView`控制讓您為不同的選項，以設定使用者可以如何選取儲存格、 列和資料行。</span><span class="sxs-lookup"><span data-stu-id="69e04-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="69e04-104">例如，您可以啟用單一或多個選取項目、 選取整個資料列或資料行，當使用者按一下資料格或選取整個資料列或資料行只有當使用者按一下其標頭，可讓儲存格選取範圍。</span><span class="sxs-lookup"><span data-stu-id="69e04-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="69e04-105">如果您想要提供讓您選取的使用者介面，您可以停用一般的選取項目，並以程式設計方式處理所有選取項目。</span><span class="sxs-lookup"><span data-stu-id="69e04-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="69e04-106">此外，您可以讓使用者選取的值複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="69e04-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69e04-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="69e04-107">In This Section</span></span>  
 [<span data-ttu-id="69e04-108">Windows Forms DataGridView 控制項中的選取模式</span><span class="sxs-lookup"><span data-stu-id="69e04-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="69e04-109">描述使用者與控制項中的以程式設計方式選取的選項。</span><span class="sxs-lookup"><span data-stu-id="69e04-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="69e04-110">操作說明：設定 Windows Forms DataGridView 控制項的選取模式</span><span class="sxs-lookup"><span data-stu-id="69e04-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="69e04-111">描述如何設定單一資料列選取控制項，當使用者按一下資料格。</span><span class="sxs-lookup"><span data-stu-id="69e04-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="69e04-112">操作說明：取得 Windows Forms DataGridView 控制項中選取的儲存格、資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="69e04-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="69e04-113">描述如何使用選取的資料格、 列和資料行集合。</span><span class="sxs-lookup"><span data-stu-id="69e04-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="69e04-114">操作說明：讓使用者從 Windows Forms DataGridView 控制項將多個儲存格複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="69e04-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="69e04-115">描述如何啟用控制項中的剪貼簿支援。</span><span class="sxs-lookup"><span data-stu-id="69e04-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="69e04-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="69e04-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="69e04-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="69e04-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="69e04-118">提供參考文件<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="69e04-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="69e04-119">提供參考文件<xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="69e04-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="69e04-120">提供參考文件<xref:System.Windows.Forms.DataGridViewSelectedCellCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="69e04-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="69e04-121">提供參考文件<xref:System.Windows.Forms.DataGridViewSelectedRowCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="69e04-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="69e04-122">提供參考文件<xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="69e04-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e04-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69e04-123">See Also</span></span>  
 [<span data-ttu-id="69e04-124">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="69e04-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="69e04-125">Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理</span><span class="sxs-lookup"><span data-stu-id="69e04-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)

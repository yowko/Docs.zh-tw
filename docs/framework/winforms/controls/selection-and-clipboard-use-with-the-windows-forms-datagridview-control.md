---
title: 選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 61f3eee6f4690e9bd9141f2eeb6de330bac87550
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715369"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="f1f3d-102">選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="f1f3d-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f1f3d-103">`DataGridView`控制項可為您提供各種不同的設定方式的使用者可以選取資料格、 資料列和資料行的選項。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="f1f3d-104">例如，您可以啟用單一或多個選取項目、 選取整個資料列或資料行，當使用者按一下資料格或選取整個資料列或資料行只有在使用者按一下其標頭時，才可讓儲存格選取範圍。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="f1f3d-105">如果您想要提供您自己的使用者介面選取項目，您可以停用一般的選取項目，並以程式設計方式處理所有選取項目。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="f1f3d-106">此外，您可以讓使用者選取的值複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1f3d-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="f1f3d-107">In This Section</span></span>  
 [<span data-ttu-id="f1f3d-108">Windows Forms DataGridView 控制項中的選取模式</span><span class="sxs-lookup"><span data-stu-id="f1f3d-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f1f3d-109">說明使用者和以程式設計方式在控制項中的選取的選項。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="f1f3d-110">如何：設定 Windows Forms DataGridView 控制項的選取模式</span><span class="sxs-lookup"><span data-stu-id="f1f3d-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f1f3d-111">描述如何設定適用於單一資料列選取範圍的控制項，當使用者按一下資料格。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="f1f3d-112">如何：取得 Windows Form DataGridView 控制項中的 選取的資料格、 資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="f1f3d-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="f1f3d-113">描述如何使用選取的資料格、 資料列和資料行集合。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="f1f3d-114">如何：讓使用者能夠將多個儲存格複製到剪貼簿中，從 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="f1f3d-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="f1f3d-115">描述如何啟用控制項中的剪貼簿支援。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1f3d-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="f1f3d-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="f1f3d-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="f1f3d-118">提供參考文件<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="f1f3d-119">提供參考文件<xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="f1f3d-120">提供參考文件<xref:System.Windows.Forms.DataGridViewSelectedCellCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="f1f3d-121">提供參考文件<xref:System.Windows.Forms.DataGridViewSelectedRowCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="f1f3d-122">提供參考文件<xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="f1f3d-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f3d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1f3d-123">See also</span></span>
- [<span data-ttu-id="f1f3d-124">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="f1f3d-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="f1f3d-125">Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理</span><span class="sxs-lookup"><span data-stu-id="f1f3d-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)

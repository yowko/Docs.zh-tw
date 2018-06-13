---
title: 使用設計工具搭配 Windows Form DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 618e422c893d0f0c1870d5b9bf2360eb946dd3c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539821"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="4954d-102">使用設計工具搭配 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="4954d-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4954d-103">Visual Studio 提供的設計工具支援`DataGridView`控制項，可讓您無須撰寫程式碼執行安裝程式工作。</span><span class="sxs-lookup"><span data-stu-id="4954d-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="4954d-104">這些工作包括繫結控制項至資料來源，修改的資料行用來顯示資料，以及調整的外觀和基本行為的控制項。</span><span class="sxs-lookup"><span data-stu-id="4954d-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4954d-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="4954d-105">In This Section</span></span>  
 [<span data-ttu-id="4954d-106">操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="4954d-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-107">描述如何使用**加入資料行**和**編輯資料行**對話方塊，以填入和修改資料行集合。</span><span class="sxs-lookup"><span data-stu-id="4954d-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="4954d-108">操作說明：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="4954d-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-109">描述如何使用**選擇資料來源**控制項的智慧標籤上選項，可連接至資料。</span><span class="sxs-lookup"><span data-stu-id="4954d-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="4954d-110">操作說明：使用設計工具變更 Windows Forms DataGridView 控制項中資料行的順序</span><span class="sxs-lookup"><span data-stu-id="4954d-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-111">描述如何使用**編輯資料行**對話方塊來重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="4954d-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="4954d-112">操作說明：使用設計工具變更 Windows Forms DataGridView 資料行的類型</span><span class="sxs-lookup"><span data-stu-id="4954d-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="4954d-113">描述如何使用**編輯資料行**對話方塊來變更資料行類型。</span><span class="sxs-lookup"><span data-stu-id="4954d-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="4954d-114">操作說明：使用設計工具在 Windows Forms DataGridView 控制項中啟用資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="4954d-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-115">描述如何使用控制項的智慧標籤，讓使用者重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="4954d-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="4954d-116">操作說明：使用設計工具凍結 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="4954d-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-117">描述如何使用**編輯資料行**對話方塊，即可防止特定資料行捲動。</span><span class="sxs-lookup"><span data-stu-id="4954d-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="4954d-118">操作說明：使用設計工具隱藏 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="4954d-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-119">描述如何使用**編輯資料行**隱藏特定的資料行 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4954d-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="4954d-120">操作說明：使用設計工具將 Windows Forms DataGridView 控制項中的資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="4954d-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-121">描述如何使用**編輯資料行**特定資料行中值的對話方塊，即可防止使用者編輯。</span><span class="sxs-lookup"><span data-stu-id="4954d-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="4954d-122">操作說明：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="4954d-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-123">描述如何使用控制項的智慧標籤來防止使用者加入或刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="4954d-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="4954d-124">操作說明：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="4954d-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="4954d-125">描述如何使用**CellStyle 產生器**對話方塊來建立控制項中的類似 ledger 的外觀。</span><span class="sxs-lookup"><span data-stu-id="4954d-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="4954d-126">操作說明：使用設計工具設定 Windows Forms DataGridView 控制項的預設儲存格樣式和資料格式</span><span class="sxs-lookup"><span data-stu-id="4954d-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="4954d-127">描述如何使用**CellStyle 產生器**控制項的對話方塊來設定基本外觀和資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="4954d-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4954d-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="4954d-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="4954d-129">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="4954d-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4954d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4954d-130">See Also</span></span>  
 [<span data-ttu-id="4954d-131">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="4954d-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)

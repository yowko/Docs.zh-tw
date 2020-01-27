---
title: 使用設計工具搭配 DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 50e8bddb97c2dfb84cebdbb2ca4d42a6c5743304
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728363"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="1a47d-102">使用設計工具搭配 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="1a47d-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1a47d-103">Visual Studio 提供 `DataGridView` 控制項的設計工具支援，讓您不需要撰寫程式碼，就能執行許多設定工作。</span><span class="sxs-lookup"><span data-stu-id="1a47d-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="1a47d-104">這些工作包括將控制項系結至資料來源、修改用來顯示資料的資料行，以及調整控制項的外觀和基本行為。</span><span class="sxs-lookup"><span data-stu-id="1a47d-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a47d-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1a47d-105">In This Section</span></span>  
 [<span data-ttu-id="1a47d-106">操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="1a47d-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-107">描述如何使用 [**加入資料行**] 和 [**編輯資料行**] 對話方塊來填入和修改資料行集合。</span><span class="sxs-lookup"><span data-stu-id="1a47d-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="1a47d-108">操作說明：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="1a47d-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-109">描述如何在控制項的智慧標籤上使用 [**選擇資料來源**] 選項，以連接到資料。</span><span class="sxs-lookup"><span data-stu-id="1a47d-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="1a47d-110">操作說明：使用設計工具變更 Windows Forms DataGridView 控制項中資料行的順序</span><span class="sxs-lookup"><span data-stu-id="1a47d-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-111">描述如何使用 [**編輯資料行**] 對話方塊來重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="1a47d-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="1a47d-112">操作說明：使用設計工具變更 Windows Forms DataGridView 資料行的類型</span><span class="sxs-lookup"><span data-stu-id="1a47d-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="1a47d-113">描述如何使用 [**編輯資料行**] 對話方塊來變更資料行類型。</span><span class="sxs-lookup"><span data-stu-id="1a47d-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="1a47d-114">操作說明：使用設計工具在 Windows Forms DataGridView 控制項中啟用資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="1a47d-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-115">描述如何使用控制項的智慧標籤，讓使用者重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="1a47d-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="1a47d-116">操作說明：使用設計工具凍結 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="1a47d-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-117">描述如何使用 [**編輯資料行**] 對話方塊來防止特定資料行進行滾動。</span><span class="sxs-lookup"><span data-stu-id="1a47d-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="1a47d-118">操作說明：使用設計工具隱藏 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="1a47d-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-119">描述如何使用 [**編輯資料行**] 對話方塊來隱藏特定資料行。</span><span class="sxs-lookup"><span data-stu-id="1a47d-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="1a47d-120">操作說明：使用設計工具將 Windows Forms DataGridView 控制項中的資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="1a47d-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-121">描述如何使用 [**編輯資料行**] 對話方塊，防止使用者編輯特定資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="1a47d-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="1a47d-122">操作說明：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="1a47d-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-123">描述如何使用控制項的智慧標籤來防止使用者加入或刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="1a47d-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="1a47d-124">操作說明：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="1a47d-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="1a47d-125">描述如何使用 [ **CellStyle**產生器] 對話方塊，在控制項中建立類似總帳的外觀。</span><span class="sxs-lookup"><span data-stu-id="1a47d-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="1a47d-126">操作說明：使用設計工具設定 Windows Forms DataGridView 控制項的預設儲存格樣式和資料格式</span><span class="sxs-lookup"><span data-stu-id="1a47d-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](default-cell-styles-datagridview.md)  
 <span data-ttu-id="1a47d-127">描述如何使用 [ **CellStyle**產生器] 對話方塊來設定控制項的基本外觀和資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="1a47d-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1a47d-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="1a47d-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="1a47d-129">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="1a47d-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a47d-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a47d-130">See also</span></span>

- [<span data-ttu-id="1a47d-131">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="1a47d-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)

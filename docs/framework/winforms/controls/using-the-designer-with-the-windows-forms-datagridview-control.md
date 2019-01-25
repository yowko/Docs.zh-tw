---
title: 使用設計工具搭配 Windows Form DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 588db8b2f66bbfd58ea6197a7b5a65bb8ecbfd19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644804"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="36502-102">使用設計工具搭配 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="36502-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="36502-103">Visual Studio 提供的設計工具支援`DataGridView`可讓您執行許多設定工作，而不需要撰寫程式碼的控制項。</span><span class="sxs-lookup"><span data-stu-id="36502-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="36502-104">這些工作包括繫結至資料來源，修改的資料行控制項用來顯示資料，並調整的外觀和控制項的基本行為。</span><span class="sxs-lookup"><span data-stu-id="36502-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36502-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="36502-105">In This Section</span></span>  
 [<span data-ttu-id="36502-106">如何：新增和移除使用設計工具的 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="36502-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-107">描述如何使用**加入資料行**並**編輯資料行**對話方塊來填入和修改資料行集合。</span><span class="sxs-lookup"><span data-stu-id="36502-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="36502-108">如何：資料繫結至 Windows Form DataGridView 控制項中使用設計工具</span><span class="sxs-lookup"><span data-stu-id="36502-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-109">描述如何使用**選擇資料來源**連接至資料控制項的智慧標籤選項。</span><span class="sxs-lookup"><span data-stu-id="36502-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="36502-110">如何：變更 Windows Form DataGridView 控制項中使用設計工具中的資料行的順序</span><span class="sxs-lookup"><span data-stu-id="36502-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-111">描述如何使用**編輯資料行**對話方塊，即可重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="36502-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="36502-112">如何：使用設計工具的 Windows Forms DataGridView 資料行的類型變更</span><span class="sxs-lookup"><span data-stu-id="36502-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="36502-113">描述如何使用**編輯資料行**對話方塊來變更資料行類型。</span><span class="sxs-lookup"><span data-stu-id="36502-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="36502-114">如何：啟用 Windows Form DataGridView 控制項中使用設計工具中的資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="36502-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-115">描述如何使用控制項的智慧標籤，讓使用者能夠重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="36502-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="36502-116">如何：凍結 Windows Form DataGridView 控制項中使用設計工具中的資料行</span><span class="sxs-lookup"><span data-stu-id="36502-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-117">描述如何使用**編輯資料行**對話方塊中，若要避免的特定資料行捲動。</span><span class="sxs-lookup"><span data-stu-id="36502-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="36502-118">如何：隱藏 Windows Form DataGridView 控制項中使用設計工具中的資料行</span><span class="sxs-lookup"><span data-stu-id="36502-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-119">描述如何使用**編輯資料行**對話方塊，即可隱藏特定的資料行。</span><span class="sxs-lookup"><span data-stu-id="36502-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="36502-120">如何：讓唯讀使用設計工具的 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="36502-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-121">描述如何使用**編輯資料行**特定資料行中值的對話方塊，即可防止使用者編輯。</span><span class="sxs-lookup"><span data-stu-id="36502-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="36502-122">如何：防止資料列新增和刪除使用設計工具的 Windows Form DataGridView 控制項中</span><span class="sxs-lookup"><span data-stu-id="36502-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-123">描述如何使用控制項的智慧標籤，以防止使用者加入或刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="36502-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="36502-124">如何：設定為使用設計工具在 Windows Form DataGridView 控制項中替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="36502-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="36502-125">描述如何使用**CellStyle 產生器**對話方塊，即可建立在控制項中的類似 ledger 的外觀。</span><span class="sxs-lookup"><span data-stu-id="36502-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="36502-126">如何：為 Windows Form DataGridView 控制項中使用設計工具中的預設儲存格樣式和資料格式</span><span class="sxs-lookup"><span data-stu-id="36502-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="36502-127">描述如何使用**CellStyle 產生器**控制項的對話方塊，即可設定基本的外觀和資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="36502-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="36502-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="36502-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="36502-129">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="36502-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36502-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36502-130">See also</span></span>
- [<span data-ttu-id="36502-131">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="36502-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)

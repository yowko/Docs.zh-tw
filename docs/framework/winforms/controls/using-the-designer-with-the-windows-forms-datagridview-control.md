---
title: 使用設計工具搭配 Windows Form DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: daac7dca27ac5dca8df4db24c9a3e22dae831377
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231470"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="0b596-102">使用設計工具搭配 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="0b596-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0b596-103">Visual Studio 提供的設計工具支援`DataGridView`可讓您執行許多設定工作，而不需要撰寫程式碼的控制項。</span><span class="sxs-lookup"><span data-stu-id="0b596-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="0b596-104">這些工作包括繫結至資料來源，修改的資料行控制項用來顯示資料，並調整的外觀和控制項的基本行為。</span><span class="sxs-lookup"><span data-stu-id="0b596-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b596-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="0b596-105">In This Section</span></span>  
 [<span data-ttu-id="0b596-106">HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="0b596-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-107">描述如何使用**加入資料行**並**編輯資料行**對話方塊來填入和修改資料行集合。</span><span class="sxs-lookup"><span data-stu-id="0b596-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="0b596-108">HOW TO：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="0b596-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-109">描述如何使用**選擇資料來源**連接至資料控制項的智慧標籤選項。</span><span class="sxs-lookup"><span data-stu-id="0b596-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="0b596-110">HOW TO：使用設計工具變更 Windows Forms DataGridView 控制項的資料行順序</span><span class="sxs-lookup"><span data-stu-id="0b596-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-111">描述如何使用**編輯資料行**對話方塊，即可重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="0b596-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="0b596-112">HOW TO：使用設計工具變更 Windows Forms DataGridView 資料行的類型</span><span class="sxs-lookup"><span data-stu-id="0b596-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="0b596-113">描述如何使用**編輯資料行**對話方塊來變更資料行類型。</span><span class="sxs-lookup"><span data-stu-id="0b596-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="0b596-114">HOW TO：使用設計工具重新調整 Windows Forms DataGridView 控制項的資料行順序</span><span class="sxs-lookup"><span data-stu-id="0b596-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-115">描述如何使用控制項的智慧標籤，讓使用者能夠重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="0b596-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="0b596-116">HOW TO：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行</span><span class="sxs-lookup"><span data-stu-id="0b596-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-117">描述如何使用**編輯資料行**對話方塊中，若要避免的特定資料行捲動。</span><span class="sxs-lookup"><span data-stu-id="0b596-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="0b596-118">HOW TO：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行</span><span class="sxs-lookup"><span data-stu-id="0b596-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-119">描述如何使用**編輯資料行**對話方塊，即可隱藏特定的資料行。</span><span class="sxs-lookup"><span data-stu-id="0b596-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="0b596-120">HOW TO：使用設計工具將 Windows Forms DataGridView 控制項的資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="0b596-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-121">描述如何使用**編輯資料行**特定資料行中值的對話方塊，即可防止使用者編輯。</span><span class="sxs-lookup"><span data-stu-id="0b596-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="0b596-122">HOW TO：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="0b596-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-123">描述如何使用控制項的智慧標籤，以防止使用者加入或刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="0b596-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="0b596-124">HOW TO：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="0b596-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="0b596-125">描述如何使用**CellStyle 產生器**對話方塊，即可建立在控制項中的類似 ledger 的外觀。</span><span class="sxs-lookup"><span data-stu-id="0b596-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="0b596-126">HOW TO：使用設計工具設定 Windows Forms DataGridView 控制項的預設儲存格樣式和資料格式</span><span class="sxs-lookup"><span data-stu-id="0b596-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](default-cell-styles-datagridview.md)  
 <span data-ttu-id="0b596-127">描述如何使用**CellStyle 產生器**控制項的對話方塊，即可設定基本的外觀和資料顯示格式。</span><span class="sxs-lookup"><span data-stu-id="0b596-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0b596-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="0b596-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="0b596-129">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="0b596-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b596-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b596-130">See also</span></span>

- [<span data-ttu-id="0b596-131">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="0b596-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)

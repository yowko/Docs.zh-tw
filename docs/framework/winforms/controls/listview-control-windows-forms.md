---
title: "ListView 控制項 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lists
- checked list items [Windows Forms], Windows Forms controls
- user interface [Windows Forms], creating
- lists [Windows Forms], items with icons
- icons [Windows Forms], listing with items
- list views
- ListView control [Windows Forms]
- list controls [Windows Forms], List view
ms.assetid: 9f71cf5c-82da-488a-a04e-ef52c0817187
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bc771b81e1db87f3d881dc2a0ab84f7aad93247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="966d5-102">ListView 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="966d5-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="966d5-103">Windows Form `ListView` 控制項顯示具有圖示的項目清單。</span><span class="sxs-lookup"><span data-stu-id="966d5-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="966d5-104">若要建立像 Windows 檔案總管右窗格的使用者介面，您可以使用清單檢視。</span><span class="sxs-lookup"><span data-stu-id="966d5-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="966d5-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="966d5-105">In This Section</span></span>  
 [<span data-ttu-id="966d5-106">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="966d5-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="966d5-107">描述此控制項及其重要功能與屬性。</span><span class="sxs-lookup"><span data-stu-id="966d5-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="966d5-108">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="966d5-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-109">描述如何新增或移除清單檢視中的項目。</span><span class="sxs-lookup"><span data-stu-id="966d5-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="966d5-110">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="966d5-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-111">描述如何建立資料行來顯示每個清單項目的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="966d5-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="966d5-112">操作說明：顯示 Windows Forms ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="966d5-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-113">描述如何將清單檢視與顯示大型或小型圖示的適當影像清單產生關聯。</span><span class="sxs-lookup"><span data-stu-id="966d5-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="966d5-114">操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="966d5-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-115">描述如何在資料行中顯示每個清單項目的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="966d5-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="966d5-116">操作說明：選取 Windows Forms ListView 控制項中的項目</span><span class="sxs-lookup"><span data-stu-id="966d5-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-117">描述如何以程式設計方式選取項目。</span><span class="sxs-lookup"><span data-stu-id="966d5-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="966d5-118">操作說明：在 Windows Forms ListView 控制項中群組項目</span><span class="sxs-lookup"><span data-stu-id="966d5-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-119">描述如何建立顯示分類的群組，以及如何將項目指派給每個群組。</span><span class="sxs-lookup"><span data-stu-id="966d5-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="966d5-120">這項功能只能在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="966d5-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="966d5-121">操作說明：在 Windows Forms ListView 控制項中啟用並排顯示</span><span class="sxs-lookup"><span data-stu-id="966d5-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-122">描述如何顯示項目為並排顯示，其中每個項目由大型圖示和多行文字組成。</span><span class="sxs-lookup"><span data-stu-id="966d5-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="966d5-123">這項功能只能在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="966d5-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="966d5-124">操作說明：在 Windows Forms ListView 控制項中顯示插入標記</span><span class="sxs-lookup"><span data-stu-id="966d5-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="966d5-125">描述如何實作拖放作業的使用者意見，其中插入標記表示每個滑鼠指標位置的置放位置。</span><span class="sxs-lookup"><span data-stu-id="966d5-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="966d5-126">這項功能只能在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="966d5-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="966d5-127">操作說明：將搜尋能力加入至 ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="966d5-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="966d5-128">描述如何使用文字搜尋或螢幕座標，以程式設計的方式尋找項目。</span><span class="sxs-lookup"><span data-stu-id="966d5-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   <span data-ttu-id="966d5-129">[操作說明：使用設計工具在 Windows Forms ListView 控制項中啟用並排顯示](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="966d5-129">[How to: Enable Tile View in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="966d5-130">[操作說明：使用設計工具搭配 Windows Forms ListView 控制項加入和移除項目](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="966d5-130">[How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="966d5-131">[操作說明：使用設計工具在 Windows Forms ListView 控制項中加入資料行](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="966d5-131">[How to: Add Columns to the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="966d5-132">[操作說明：使用設計工具群組 Windows Forms ListView 控制項中的項目](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="966d5-132">[How to: Group Items in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="966d5-133">[逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="966d5-133">[Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="966d5-134">參考資料</span><span class="sxs-lookup"><span data-stu-id="966d5-134">Reference</span></span>  
 <span data-ttu-id="966d5-135"><xref:System.Windows.Forms.ListView> 類別</span><span class="sxs-lookup"><span data-stu-id="966d5-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="966d5-136">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="966d5-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="966d5-137">相關章節</span><span class="sxs-lookup"><span data-stu-id="966d5-137">Related Sections</span></span>  
 [<span data-ttu-id="966d5-138">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="966d5-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="966d5-139">描述如何自清單檢閱中繼承項目或自樹狀檢閱中繼承節點，以加入任何您需要的欄位、方法或建構函式。</span><span class="sxs-lookup"><span data-stu-id="966d5-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="966d5-140">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="966d5-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="966d5-141">說明影像清單是什麼，並說明其重要功能與屬性。</span><span class="sxs-lookup"><span data-stu-id="966d5-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="966d5-142">逐步解說：利用 Windows Forms 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="966d5-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="966d5-143">提供配置具有多個窗格的 Windows Form 的指示。</span><span class="sxs-lookup"><span data-stu-id="966d5-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="966d5-144">Windows XP 功能和 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="966d5-144">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="966d5-145">說明如何利用適用於 <xref:System.Windows.Forms.ListView> 控制項的 Windows XP 特定功能。</span><span class="sxs-lookup"><span data-stu-id="966d5-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966d5-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="966d5-146">See Also</span></span>  
 [<span data-ttu-id="966d5-147">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="966d5-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)

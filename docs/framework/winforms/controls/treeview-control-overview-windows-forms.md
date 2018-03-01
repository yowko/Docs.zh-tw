---
title: "TreeView 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bbe8549268c2b67b67184966e938f7d62b766a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="treeview-control-overview-windows-forms"></a><span data-ttu-id="a214b-102">TreeView 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="a214b-102">TreeView Control Overview (Windows Forms)</span></span>
<span data-ttu-id="a214b-103">使用 Windows Form <xref:System.Windows.Forms.TreeView> 控制項，您可以向使用者顯示節點階層，就像 Windows 作業系統中 Windows 檔案總管功能左窗格顯示檔案和資料夾的方式。</span><span class="sxs-lookup"><span data-stu-id="a214b-103">With the Windows Forms <xref:System.Windows.Forms.TreeView> control, you can display a hierarchy of nodes to users, like the way files and folders are displayed in the left pane of the Windows Explorer feature of the Windows operating system.</span></span> <span data-ttu-id="a214b-104">樹狀檢視中的每個節點都可能包含其他節點，稱為*子節點*。</span><span class="sxs-lookup"><span data-stu-id="a214b-104">Each node in the tree view might contain other nodes, called *child nodes*.</span></span> <span data-ttu-id="a214b-105">您可以顯示父節點或包含子節點的節點為展開或摺疊。</span><span class="sxs-lookup"><span data-stu-id="a214b-105">You can display parent nodes, or nodes that contain child nodes, as expanded or collapsed.</span></span> <span data-ttu-id="a214b-106">您也可以藉由設定樹狀檢視的 <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> 屬性為 `true`來顯示節點旁邊核取方塊的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="a214b-106">You can also display a tree view with check boxes next to the nodes by setting the tree view's <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> property to `true`.</span></span> <span data-ttu-id="a214b-107">藉由設定節點的 <xref:System.Windows.Forms.TreeNode.Checked%2A> 屬性為 `true` 或 `false`，您可以程式設計的方式選取或清除節點。</span><span class="sxs-lookup"><span data-stu-id="a214b-107">You can then programmatically select or clear nodes by setting the node's <xref:System.Windows.Forms.TreeNode.Checked%2A> property to `true` or `false`.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="a214b-108">主要屬性</span><span class="sxs-lookup"><span data-stu-id="a214b-108">Key Properties</span></span>  
 <span data-ttu-id="a214b-109"><xref:System.Windows.Forms.TreeView> 控制項的索引鍵屬性為 <xref:System.Windows.Forms.TreeView.Nodes%2A> 和 <xref:System.Windows.Forms.TreeView.SelectedNode%2A>。</span><span class="sxs-lookup"><span data-stu-id="a214b-109">The key properties of the <xref:System.Windows.Forms.TreeView> control are <xref:System.Windows.Forms.TreeView.Nodes%2A> and <xref:System.Windows.Forms.TreeView.SelectedNode%2A>.</span></span> <span data-ttu-id="a214b-110"><xref:System.Windows.Forms.TreeView.Nodes%2A> 屬性包含樹狀檢視中最上層節點的清單。</span><span class="sxs-lookup"><span data-stu-id="a214b-110">The <xref:System.Windows.Forms.TreeView.Nodes%2A> property contains the list of top-level nodes in the tree view.</span></span> <span data-ttu-id="a214b-111"><xref:System.Windows.Forms.TreeView.SelectedNode%2A> 屬性會設定目前選取的節點。</span><span class="sxs-lookup"><span data-stu-id="a214b-111">The <xref:System.Windows.Forms.TreeView.SelectedNode%2A> property sets the currently selected node.</span></span> <span data-ttu-id="a214b-112">您可以在節點旁邊顯示圖示。</span><span class="sxs-lookup"><span data-stu-id="a214b-112">You can display icons next to the nodes.</span></span> <span data-ttu-id="a214b-113">此控制項會使用來自樹狀檢視的 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性中命名的 <xref:System.Windows.Forms.ImageList> 影像。</span><span class="sxs-lookup"><span data-stu-id="a214b-113">The control uses images from the <xref:System.Windows.Forms.ImageList> named in the tree view's <xref:System.Windows.Forms.TreeView.ImageList%2A> property.</span></span> <span data-ttu-id="a214b-114"><xref:System.Windows.Forms.TreeView.ImageIndex%2A> 屬性會設定樹狀檢視節點中的預設影像。</span><span class="sxs-lookup"><span data-stu-id="a214b-114">The <xref:System.Windows.Forms.TreeView.ImageIndex%2A> property sets the default image for nodes in the tree view.</span></span> <span data-ttu-id="a214b-115">如需有關顯示影像的詳細資訊，請參閱[How to： 設定 Windows Form TreeView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a214b-115">For more information about displaying images, see [How to: Set Icons for the Windows Forms TreeView Control](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md).</span></span> <span data-ttu-id="a214b-116">如果您使用 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]，則具有可搭配 <xref:System.Windows.Forms.TreeView> 控制項使用之大型標準影像程式庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="a214b-116">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use with the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a214b-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a214b-117">See Also</span></span>  
 <xref:System.Windows.Forms.TreeView>  
 [<span data-ttu-id="a214b-118">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="a214b-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="a214b-119">操作說明：設定 Windows Forms TreeView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="a214b-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="a214b-120">操作說明：使用 Windows Forms TreeView 控制項加入和移除節點</span><span class="sxs-lookup"><span data-stu-id="a214b-120">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="a214b-121">操作說明：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="a214b-121">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="a214b-122">操作說明：判斷按下哪個 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="a214b-122">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="a214b-123">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a214b-123">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)

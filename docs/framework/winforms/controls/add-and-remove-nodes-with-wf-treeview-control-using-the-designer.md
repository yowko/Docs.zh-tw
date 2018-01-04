---
title: "如何：使用設計工具搭配 Windows Form TreeView 控制項加入和移除節點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6067302fd603b53ee075da837a29a3ebc05cc346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="2c5e1-102">如何：使用設計工具搭配 Windows Form TreeView 控制項加入和移除節點</span><span class="sxs-lookup"><span data-stu-id="2c5e1-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="2c5e1-103">因為 Windows Form<xref:System.Windows.Forms.TreeView>控制項會顯示節點階層的方式，加入節點，您必須注意到其父節點時。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="2c5e1-104">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="2c5e1-105">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-105">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c5e1-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2c5e1-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2c5e1-108">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="2c5e1-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="2c5e1-109">若要加入或移除節點，在設計工具</span><span class="sxs-lookup"><span data-stu-id="2c5e1-109">To add or remove nodes in the designer</span></span>  
  
1.  <span data-ttu-id="2c5e1-110">選取 <xref:System.Windows.Forms.TreeView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="2c5e1-111">在**屬性**視窗中，按一下**省略**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="2c5e1-112">**TreeNode 編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-112">The **TreeNode Editor** appears.</span></span>  
  
3.  <span data-ttu-id="2c5e1-113">若要加入的節點，必須要有一個根節點;如果不存在的話，您必須先按一下 [新增根**新增根**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="2c5e1-114">然後您可以加入子節點選取根節點或任何其他節點，然後按一下**新增子系** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4.  <span data-ttu-id="2c5e1-115">若要刪除的節點，選取要刪除，然後按一下 [節點**刪除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2c5e1-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5e1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c5e1-116">See Also</span></span>  
 [<span data-ttu-id="2c5e1-117">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="2c5e1-117">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="2c5e1-118">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2c5e1-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="2c5e1-119">操作說明：設定 Windows Forms TreeView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="2c5e1-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="2c5e1-120">操作說明：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="2c5e1-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="2c5e1-121">操作說明：判斷按下哪個 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="2c5e1-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="2c5e1-122">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2c5e1-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)

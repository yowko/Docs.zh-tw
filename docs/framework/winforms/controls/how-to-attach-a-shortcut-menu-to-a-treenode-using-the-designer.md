---
title: "如何：使用設計工具將捷徑功能表附加至 TreeNode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1ec1b0236aab0f4ac61cb58d4fe006d17594e17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="9e85b-102">如何：使用設計工具將捷徑功能表附加至 TreeNode</span><span class="sxs-lookup"><span data-stu-id="9e85b-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="9e85b-103">Windows Form<xref:System.Windows.Forms.TreeView>控制項會顯示節點階層，類似於檔案和資料夾顯示在 Windows 作業系統中 Windows 檔案總管功能左窗格中。</span><span class="sxs-lookup"><span data-stu-id="9e85b-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="9e85b-104">藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性，您可以向使用者提供即時線上作業，當它們以滑鼠右鍵按一下<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="9e85b-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="9e85b-105">透過建立關聯<xref:System.Windows.Forms.ContextMenuStrip>具有個別元件<xref:System.Windows.Forms.TreeNode>項目，您可以加入自訂層級的快顯功能表功能，以您<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="9e85b-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e85b-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="9e85b-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9e85b-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="9e85b-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9e85b-108">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="9e85b-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="9e85b-109">在設計階段與 TreeNode 的捷徑功能表</span><span class="sxs-lookup"><span data-stu-id="9e85b-109">To associate a shortcut menu with a TreeNode at design time</span></span>  
  
1.  <span data-ttu-id="9e85b-110">新增<xref:System.Windows.Forms.TreeView>控制項加入表單，並再將節點加入<xref:System.Windows.Forms.TreeView>視。</span><span class="sxs-lookup"><span data-stu-id="9e85b-110">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="9e85b-111">如需詳細資訊，請參閱[如何： 新增和移除節點與 Windows Form TreeView 控制項](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="9e85b-111">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>  
  
2.  <span data-ttu-id="9e85b-112">新增<xref:System.Windows.Forms.ContextMenuStrip>元件加入至表單，然後將功能表項目新增至代表您想要在執行階段提供節點層級作業的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="9e85b-112">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="9e85b-113">如需詳細資訊，請參閱[How to： 將功能表項目加入 ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)。</span><span class="sxs-lookup"><span data-stu-id="9e85b-113">For more information, see [How to: Add Menu Items to a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>  
  
3.  <span data-ttu-id="9e85b-114">重新開啟**TreeNodeEditor**對話方塊的 <xref:System.Windows.Forms.TreeView>控制，請選取該節點來編輯，並設定其<xref:System.Windows.Forms.ContextMenuStrip>您新增的快顯功能表的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e85b-114">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>  
  
4.  <span data-ttu-id="9e85b-115">當設定這個屬性時，當您以滑鼠右鍵按一下節點將顯示的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="9e85b-115">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
     <span data-ttu-id="9e85b-116">此外，您會想要撰寫程式碼以處理<xref:System.Windows.Forms.ToolStripItem.Click>事件的這些功能表項目。</span><span class="sxs-lookup"><span data-stu-id="9e85b-116">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e85b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e85b-117">See Also</span></span>  
 [<span data-ttu-id="9e85b-118">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="9e85b-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="9e85b-119">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="9e85b-119">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="9e85b-120">ContextMenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="9e85b-120">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)

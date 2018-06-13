---
title: 如何：將捷徑功能表附加至 TreeView 節點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: 737e74184b0763ed84b4e585f2508d69944d0e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528216"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a><span data-ttu-id="b5a65-102">如何：將捷徑功能表附加至 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="b5a65-102">How to: Attach a ShortCut Menu to a TreeView Node</span></span>
<span data-ttu-id="b5a65-103">Windows Form<xref:System.Windows.Forms.TreeView>控制項會顯示節點階層，類似於檔案和資料夾顯示在 Windows 檔案總管 的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="b5a65-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of Windows Explorer.</span></span> <span data-ttu-id="b5a65-104">藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性，您可以向使用者提供即時線上作業，當它們以滑鼠右鍵按一下<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="b5a65-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="b5a65-105">透過建立關聯<xref:System.Windows.Forms.ContextMenuStrip>具有個別元件<xref:System.Windows.Forms.TreeNode>項目，您可以加入自訂層級的快顯功能表功能，以您<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="b5a65-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a><span data-ttu-id="b5a65-106">以程式設計的方式與樹狀結構節點的捷徑功能表</span><span class="sxs-lookup"><span data-stu-id="b5a65-106">To associate a shortcut menu with a TreeNode programmatically</span></span>  
  
1.  <span data-ttu-id="b5a65-107">具現化<xref:System.Windows.Forms.TreeView>控制項具有適當的屬性設定，建立根目錄<xref:System.Windows.Forms.TreeNode>，然後再加入子節點。</span><span class="sxs-lookup"><span data-stu-id="b5a65-107">Instantiate a <xref:System.Windows.Forms.TreeView> control with the appropriate property settings, create a root <xref:System.Windows.Forms.TreeNode>, and then add subnodes.</span></span>  
  
2.  <span data-ttu-id="b5a65-108">具現化<xref:System.Windows.Forms.ContextMenuStrip>元件，然後再加入<xref:System.Windows.Forms.ToolStripMenuItem>您想要在執行階段提供每一項作業。</span><span class="sxs-lookup"><span data-stu-id="b5a65-108">Instantiate a <xref:System.Windows.Forms.ContextMenuStrip> component, and then add a <xref:System.Windows.Forms.ToolStripMenuItem> for each operation you want to make available at run time.</span></span>  
  
3.  <span data-ttu-id="b5a65-109">設定<xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A>屬性的適當<xref:System.Windows.Forms.TreeNode>您所建立的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="b5a65-109">Set the <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> property of the appropriate <xref:System.Windows.Forms.TreeNode> to the shortcut menu you create.</span></span>  
  
4.  <span data-ttu-id="b5a65-110">當設定這個屬性時，當您以滑鼠右鍵按一下節點將顯示的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="b5a65-110">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
 <span data-ttu-id="b5a65-111">下列程式碼範例會建立基本<xref:System.Windows.Forms.TreeView>和<xref:System.Windows.Forms.ContextMenuStrip>根相關聯<xref:System.Windows.Forms.TreeNode>的<xref:System.Windows.Forms.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="b5a65-111">The following code example creates a basic <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ContextMenuStrip> associated with the root <xref:System.Windows.Forms.TreeNode> of the <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="b5a65-112">您必須自訂功能表選項，以符合<xref:System.Windows.Forms.TreeView>您所開發。</span><span class="sxs-lookup"><span data-stu-id="b5a65-112">You will need to customize the menu choices to those that fit the <xref:System.Windows.Forms.TreeView> you are developing.</span></span> <span data-ttu-id="b5a65-113">此外，您會想要撰寫程式碼以處理<xref:System.Windows.Forms.ToolStripItem.Click>事件的這些功能表項目。</span><span class="sxs-lookup"><span data-stu-id="b5a65-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b5a65-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5a65-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [<span data-ttu-id="b5a65-115">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="b5a65-115">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)

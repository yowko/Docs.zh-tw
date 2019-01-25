---
title: HOW TO：將捷徑功能表附加至 TreeView 節點
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
ms.openlocfilehash: 7c9e2a2fc51628116a7762e343f36f9f7e93fe67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685200"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a><span data-ttu-id="97d17-102">HOW TO：將捷徑功能表附加至 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="97d17-102">How to: Attach a ShortCut Menu to a TreeView Node</span></span>
<span data-ttu-id="97d17-103">Windows Form<xref:System.Windows.Forms.TreeView>控制項顯示的節點，類似於檔案和資料夾顯示在 Windows 檔案總管的左窗格中的階層。</span><span class="sxs-lookup"><span data-stu-id="97d17-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of Windows Explorer.</span></span> <span data-ttu-id="97d17-104">藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性，您可以向使用者提供即時線上作業，當他們以滑鼠右鍵按一下<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="97d17-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="97d17-105">產生關聯<xref:System.Windows.Forms.ContextMenuStrip>元件的個別<xref:System.Windows.Forms.TreeNode>項目，您可以加入自訂的層級的快顯功能表功能，以您<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="97d17-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a><span data-ttu-id="97d17-106">若要以程式設計方式關聯樹狀結構節點的捷徑功能表</span><span class="sxs-lookup"><span data-stu-id="97d17-106">To associate a shortcut menu with a TreeNode programmatically</span></span>  
  
1.  <span data-ttu-id="97d17-107">具現化<xref:System.Windows.Forms.TreeView>控制項的適當屬性設定，建立根<xref:System.Windows.Forms.TreeNode>，然後新增子節點。</span><span class="sxs-lookup"><span data-stu-id="97d17-107">Instantiate a <xref:System.Windows.Forms.TreeView> control with the appropriate property settings, create a root <xref:System.Windows.Forms.TreeNode>, and then add subnodes.</span></span>  
  
2.  <span data-ttu-id="97d17-108">具現化<xref:System.Windows.Forms.ContextMenuStrip>元件，然後新增<xref:System.Windows.Forms.ToolStripMenuItem>針對您想要在執行階段提供每個作業。</span><span class="sxs-lookup"><span data-stu-id="97d17-108">Instantiate a <xref:System.Windows.Forms.ContextMenuStrip> component, and then add a <xref:System.Windows.Forms.ToolStripMenuItem> for each operation you want to make available at run time.</span></span>  
  
3.  <span data-ttu-id="97d17-109">設定<xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A>適當屬性<xref:System.Windows.Forms.TreeNode>您所建立的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="97d17-109">Set the <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> property of the appropriate <xref:System.Windows.Forms.TreeNode> to the shortcut menu you create.</span></span>  
  
4.  <span data-ttu-id="97d17-110">當設定這個屬性時，當您以滑鼠右鍵按一下節點時將顯示快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="97d17-110">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
 <span data-ttu-id="97d17-111">下列程式碼範例會建立基本<xref:System.Windows.Forms.TreeView>並<xref:System.Windows.Forms.ContextMenuStrip>根目錄相關聯<xref:System.Windows.Forms.TreeNode>的<xref:System.Windows.Forms.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="97d17-111">The following code example creates a basic <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ContextMenuStrip> associated with the root <xref:System.Windows.Forms.TreeNode> of the <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="97d17-112">您必須自訂功能表選項，以符合<xref:System.Windows.Forms.TreeView>您正在開發。</span><span class="sxs-lookup"><span data-stu-id="97d17-112">You will need to customize the menu choices to those that fit the <xref:System.Windows.Forms.TreeView> you are developing.</span></span> <span data-ttu-id="97d17-113">此外，您會想要撰寫程式碼來處理<xref:System.Windows.Forms.ToolStripItem.Click>事件的這些功能表項目。</span><span class="sxs-lookup"><span data-stu-id="97d17-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97d17-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97d17-114">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="97d17-115">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="97d17-115">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)

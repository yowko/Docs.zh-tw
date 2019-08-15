---
title: 作法：使用設計工具將捷徑功能表附加至 TreeNode
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040451"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="affea-102">作法：使用設計工具將捷徑功能表附加至 TreeNode</span><span class="sxs-lookup"><span data-stu-id="affea-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="affea-103">[Windows Forms <xref:System.Windows.Forms.TreeView> ] 控制項會顯示節點的階層, 類似于 windows 作業系統中 windows Explorer 功能的左窗格中顯示的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="affea-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="affea-104">藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性, 您可以在使用者以滑鼠右鍵<xref:System.Windows.Forms.TreeView>按一下控制項時, 提供內容相關的作業。</span><span class="sxs-lookup"><span data-stu-id="affea-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="affea-105">藉由建立<xref:System.Windows.Forms.ContextMenuStrip>元件與個別<xref:System.Windows.Forms.TreeNode>專案的關聯, 您可以在<xref:System.Windows.Forms.TreeView>控制項中加入自訂的快捷方式功能表功能層級。</span><span class="sxs-lookup"><span data-stu-id="affea-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="affea-106">在設計階段將快捷方式功能表與 TreeNode 產生關聯</span><span class="sxs-lookup"><span data-stu-id="affea-106">To associate a shortcut menu with a TreeNode at design time</span></span>

1. <span data-ttu-id="affea-107">將控制項新增至表單, 然後<xref:System.Windows.Forms.TreeView>視需要將節點加入至。 <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="affea-107">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="affea-108">如需詳細資訊，請參閱[如何：使用 Windows Forms TreeView 控制項](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)加入和移除節點。</span><span class="sxs-lookup"><span data-stu-id="affea-108">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>

2. <span data-ttu-id="affea-109"><xref:System.Windows.Forms.ContextMenuStrip>將元件加入至表單, 然後將功能表項目加入至快捷方式功能表, 表示您想要在執行時間提供的節點層級作業。</span><span class="sxs-lookup"><span data-stu-id="affea-109">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="affea-110">如需詳細資訊，請參閱[如何：將功能表項目新增至 CoNtextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md)。</span><span class="sxs-lookup"><span data-stu-id="affea-110">For more information, see [How to: Add Menu Items to a ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>

3. <span data-ttu-id="affea-111">重新開啟 <xref:System.Windows.Forms.TreeView>控制項的 [TreeNodeEditor] 對話方塊, 選取要編輯的節點, 並將其<xref:System.Windows.Forms.ContextMenuStrip>屬性設定為您加入的快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="affea-111">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>

4. <span data-ttu-id="affea-112">設定此屬性時, 當您以滑鼠右鍵按一下節點時, 將會顯示快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="affea-112">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>

     <span data-ttu-id="affea-113">此外, 您也會想要撰寫程式碼來<xref:System.Windows.Forms.ToolStripItem.Click>處理這些功能表項目的事件。</span><span class="sxs-lookup"><span data-stu-id="affea-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>

## <a name="see-also"></a><span data-ttu-id="affea-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="affea-114">See also</span></span>

- [<span data-ttu-id="affea-115">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="affea-115">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="affea-116">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="affea-116">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="affea-117">ContextMenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="affea-117">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)

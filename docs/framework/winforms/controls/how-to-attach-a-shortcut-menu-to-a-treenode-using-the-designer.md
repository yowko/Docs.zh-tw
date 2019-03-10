---
title: HOW TO：將捷徑功能表附加至 TreeNode 使用設計工具
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: aa161af65b7e8e1f3636398cd02139b5623eb154
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721979"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="283f7-102">HOW TO：將捷徑功能表附加至 TreeNode 使用設計工具</span><span class="sxs-lookup"><span data-stu-id="283f7-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="283f7-103">Windows Form<xref:System.Windows.Forms.TreeView>控制項顯示的節點，類似於檔案和資料夾顯示在 Windows 作業系統中 Windows 檔案總管功能左窗格中的階層。</span><span class="sxs-lookup"><span data-stu-id="283f7-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="283f7-104">藉由設定<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性，您可以向使用者提供即時線上作業，當他們以滑鼠右鍵按一下<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="283f7-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="283f7-105">產生關聯<xref:System.Windows.Forms.ContextMenuStrip>元件的個別<xref:System.Windows.Forms.TreeNode>項目，您可以加入自訂的層級的快顯功能表功能，以您<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="283f7-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="283f7-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="283f7-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="283f7-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="283f7-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="283f7-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="283f7-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="283f7-109">在設計階段相關聯的樹狀結構節點的捷徑功能表</span><span class="sxs-lookup"><span data-stu-id="283f7-109">To associate a shortcut menu with a TreeNode at design time</span></span>  
  
1.  <span data-ttu-id="283f7-110">新增<xref:System.Windows.Forms.TreeView>控制項至表單，並再將節點加入到<xref:System.Windows.Forms.TreeView>視。</span><span class="sxs-lookup"><span data-stu-id="283f7-110">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="283f7-111">如需詳細資訊，請參閱[如何：新增和移除節點與 Windows Form TreeView 控制項](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="283f7-111">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>  
  
2.  <span data-ttu-id="283f7-112">新增<xref:System.Windows.Forms.ContextMenuStrip>元件至表單，然後加入代表您想要在執行階段提供節點層級作業的捷徑功能表中的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="283f7-112">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="283f7-113">如需詳細資訊，請參閱[如何：將功能表項目加入 ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md)。</span><span class="sxs-lookup"><span data-stu-id="283f7-113">For more information, see [How to: Add Menu Items to a ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>  
  
3.  <span data-ttu-id="283f7-114">重新開啟**TreeNodeEditor**  對話方塊<xref:System.Windows.Forms.TreeView>控制項，選取該節點來編輯，並設定其<xref:System.Windows.Forms.ContextMenuStrip>屬性，以您所新增的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="283f7-114">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>  
  
4.  <span data-ttu-id="283f7-115">當設定這個屬性時，當您以滑鼠右鍵按一下節點時將顯示快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="283f7-115">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
     <span data-ttu-id="283f7-116">此外，您會想要撰寫程式碼來處理<xref:System.Windows.Forms.ToolStripItem.Click>事件的這些功能表項目。</span><span class="sxs-lookup"><span data-stu-id="283f7-116">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="283f7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="283f7-117">See also</span></span>
- [<span data-ttu-id="283f7-118">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="283f7-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="283f7-119">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="283f7-119">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="283f7-120">ContextMenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="283f7-120">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)

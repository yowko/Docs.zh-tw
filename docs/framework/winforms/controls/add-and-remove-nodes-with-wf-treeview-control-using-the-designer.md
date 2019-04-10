---
title: HOW TO：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ecf0b758a9c45a0354a68b6cbfecdb1c49ab390f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322624"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="e27e6-102">HOW TO：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點</span><span class="sxs-lookup"><span data-stu-id="e27e6-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="e27e6-103">因為 Windows Form<xref:System.Windows.Forms.TreeView>控制項會顯示節點階層的方式，新增節點，您必須注意其父節點的功能時。</span><span class="sxs-lookup"><span data-stu-id="e27e6-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="e27e6-104">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.TreeView>控制項。</span><span class="sxs-lookup"><span data-stu-id="e27e6-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="e27e6-105">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e27e6-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e27e6-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="e27e6-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e27e6-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="e27e6-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e27e6-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="e27e6-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="e27e6-109">若要新增或移除節點，在設計工具</span><span class="sxs-lookup"><span data-stu-id="e27e6-109">To add or remove nodes in the designer</span></span>  
  
1. <span data-ttu-id="e27e6-110">選取 <xref:System.Windows.Forms.TreeView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e27e6-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2. <span data-ttu-id="e27e6-111">在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e27e6-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="e27e6-112">**TreeNode 編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e27e6-112">The **TreeNode Editor** appears.</span></span>  
  
3. <span data-ttu-id="e27e6-113">若要新增節點，必須要有一個根節點;如果不存在的話，您必須先按一下 [新增根**新增根**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e27e6-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="e27e6-114">然後您可以加入子節點選取根節點或任何其他節點，然後按一下**新增子系** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e27e6-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4. <span data-ttu-id="e27e6-115">若要刪除節點，選取要刪除，然後按一下 [節點**刪除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e27e6-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27e6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e27e6-116">See also</span></span>

- [<span data-ttu-id="e27e6-117">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="e27e6-117">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="e27e6-118">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e27e6-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="e27e6-119">HOW TO：設定 Windows Forms TreeView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="e27e6-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="e27e6-120">HOW TO：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="e27e6-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="e27e6-121">HOW TO：判斷按下了哪個 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="e27e6-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="e27e6-122">HOW TO：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e27e6-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

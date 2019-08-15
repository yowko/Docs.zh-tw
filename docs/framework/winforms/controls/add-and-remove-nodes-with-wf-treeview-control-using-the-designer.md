---
title: HOW TO：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040069"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="f8134-102">作法：使用設計工具以 Windows Forms TreeView 控制項新增和移除節點</span><span class="sxs-lookup"><span data-stu-id="f8134-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="f8134-103">由於 Windows Forms <xref:System.Windows.Forms.TreeView>控制項會以階層方式顯示節點, 因此當加入節點時, 您必須注意其父節點為何。</span><span class="sxs-lookup"><span data-stu-id="f8134-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="f8134-104">下列程式需要具有包含<xref:System.Windows.Forms.TreeView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="f8134-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="f8134-105">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="f8134-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="f8134-106">若要在設計工具中加入或移除節點</span><span class="sxs-lookup"><span data-stu-id="f8134-106">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="f8134-107">選取 <xref:System.Windows.Forms.TreeView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f8134-107">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="f8134-108">在 [**屬性**] 視窗中<xref:System.Windows.Forms.TreeView.Nodes%2A> , 按一下屬性![旁邊的**省略號**([Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8134-108">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="f8134-109">[ **TreeNode 編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f8134-109">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="f8134-110">若要加入節點, 根節點必須存在;如果其中一個不存在, 您必須先按一下 [**新增根**] 按鈕來新增根。</span><span class="sxs-lookup"><span data-stu-id="f8134-110">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="f8134-111">然後, 您可以選取根節點或任何其他節點, 然後按一下 [**新增子**系] 按鈕, 以新增子節點。</span><span class="sxs-lookup"><span data-stu-id="f8134-111">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="f8134-112">若要刪除節點, 請選取要刪除的節點, 然後按一下 [**刪除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8134-112">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8134-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8134-113">See also</span></span>

- [<span data-ttu-id="f8134-114">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="f8134-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="f8134-115">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f8134-115">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="f8134-116">如何：設定 Windows Forms TreeView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="f8134-116">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="f8134-117">如何：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="f8134-117">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="f8134-118">如何：判斷按一下哪個 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="f8134-118">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="f8134-119">如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f8134-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

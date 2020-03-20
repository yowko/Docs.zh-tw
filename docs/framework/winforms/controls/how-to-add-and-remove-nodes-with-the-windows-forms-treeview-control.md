---
title: 使用樹狀檢視控制項添加和刪除節點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: f1e74e6d2f827167c32a6955b3010b59cb2f85b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142208"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="2cdf6-102">如何：使用 Windows Form TreeView 控制項加入和移除節點</span><span class="sxs-lookup"><span data-stu-id="2cdf6-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="2cdf6-103">Windows 表單<xref:System.Windows.Forms.TreeView>控制項在其<xref:System.Windows.Forms.TreeView.Nodes%2A>集合中存儲頂級節點。</span><span class="sxs-lookup"><span data-stu-id="2cdf6-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="2cdf6-104">每個<xref:System.Windows.Forms.TreeNode>都有自己的<xref:System.Windows.Forms.TreeNode.Nodes%2A>集合來存儲其子節點。</span><span class="sxs-lookup"><span data-stu-id="2cdf6-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="2cdf6-105">這兩個集合屬性都是<xref:System.Windows.Forms.TreeNodeCollection>類型的 ，它提供標準集合成員，使您能夠在節點層次結構的單個級別添加、刪除和重新排列節點。</span><span class="sxs-lookup"><span data-stu-id="2cdf6-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="2cdf6-106">以程式設計方式添加節點</span><span class="sxs-lookup"><span data-stu-id="2cdf6-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="2cdf6-107">使用樹<xref:System.Windows.Forms.TreeNodeCollection.Add%2A>視圖<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="2cdf6-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="2cdf6-108">以程式設計方式刪除節點</span><span class="sxs-lookup"><span data-stu-id="2cdf6-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="2cdf6-109">使用樹<xref:System.Windows.Forms.TreeNodeCollection.Remove%2A>視圖<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性的方法刪除單個節點，或者<xref:System.Windows.Forms.TreeNodeCollection.Clear%2A>使用 方法清除所有節點。</span><span class="sxs-lookup"><span data-stu-id="2cdf6-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2cdf6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cdf6-110">See also</span></span>

- [<span data-ttu-id="2cdf6-111">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="2cdf6-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="2cdf6-112">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2cdf6-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="2cdf6-113">操作說明：設定 Windows Forms TreeView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="2cdf6-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="2cdf6-114">操作說明：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="2cdf6-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="2cdf6-115">操作說明：判斷按下哪個 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="2cdf6-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="2cdf6-116">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2cdf6-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

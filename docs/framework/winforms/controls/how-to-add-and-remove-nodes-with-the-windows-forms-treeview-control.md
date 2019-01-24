---
title: HOW TO：新增和移除節點，而在 Windows Form TreeView 控制項
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
ms.openlocfilehash: 30dbe55711d92ea1fdbbbfd147a65b27d0dc9a50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711497"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>HOW TO：新增和移除節點，而在 Windows Form TreeView 控制項
Windows Forms<xref:System.Windows.Forms.TreeView>控制存放區中的最上層節點及其<xref:System.Windows.Forms.TreeView.Nodes%2A>集合。 每個<xref:System.Windows.Forms.TreeNode>也有自己<xref:System.Windows.Forms.TreeNode.Nodes%2A>來儲存其所有子節點的集合。 這兩個集合屬性都屬於型別<xref:System.Windows.Forms.TreeNodeCollection>，以提供標準集合的成員，可讓您加入、 移除及重新排列節點階層架構的單一層級的節點。  
  
### <a name="to-add-nodes-programmatically"></a>若要以程式設計方式加入節點  
  
1.  使用<xref:System.Windows.Forms.TreeNodeCollection.Add%2A>樹狀檢視的方法<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性。  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>若要以程式設計方式移除節點  
  
1.  使用<xref:System.Windows.Forms.TreeNodeCollection.Remove%2A>樹狀檢視的方法<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性，以移除單一節點，或<xref:System.Windows.Forms.TreeNodeCollection.Clear%2A>方法，以清除所有節點。  
  
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
  
## <a name="see-also"></a>另請參閱
- [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [TreeView 控制項概觀](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)
- [如何：設定 Windows Form TreeView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [如何：逐一查看 Windows Forms TreeView 控制項的所有節點](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [如何：判斷按下哪個 TreeView 節點](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)

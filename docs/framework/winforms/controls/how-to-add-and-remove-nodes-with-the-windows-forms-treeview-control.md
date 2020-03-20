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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>如何：使用 Windows Form TreeView 控制項加入和移除節點
Windows 表單<xref:System.Windows.Forms.TreeView>控制項在其<xref:System.Windows.Forms.TreeView.Nodes%2A>集合中存儲頂級節點。 每個<xref:System.Windows.Forms.TreeNode>都有自己的<xref:System.Windows.Forms.TreeNode.Nodes%2A>集合來存儲其子節點。 這兩個集合屬性都是<xref:System.Windows.Forms.TreeNodeCollection>類型的 ，它提供標準集合成員，使您能夠在節點層次結構的單個級別添加、刪除和重新排列節點。  
  
### <a name="to-add-nodes-programmatically"></a>以程式設計方式添加節點  
  
1. 使用樹<xref:System.Windows.Forms.TreeNodeCollection.Add%2A>視圖<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性的方法。  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>以程式設計方式刪除節點  
  
1. 使用樹<xref:System.Windows.Forms.TreeNodeCollection.Remove%2A>視圖<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性的方法刪除單個節點，或者<xref:System.Windows.Forms.TreeNodeCollection.Clear%2A>使用 方法清除所有節點。  
  
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

- [TreeView 控制項](treeview-control-windows-forms.md)
- [TreeView 控制項概觀](treeview-control-overview-windows-forms.md)
- [操作說明：設定 Windows Forms TreeView 控制項的圖示](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [操作說明：逐一查看 Windows Forms TreeView 控制項的所有節點](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [操作說明：判斷按下哪個 TreeView 節點](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

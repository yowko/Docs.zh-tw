---
title: "如何：使用 Windows Form TreeView 控制項加入和移除節點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], TreeView 控制項"
  - "TreeView 控制項中的樹狀節點"
  - "TreeView 控制項 [Windows Form], 加入節點"
  - "TreeView 控制項 [Windows Form], 移除節點"
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用 Windows Form TreeView 控制項加入和移除節點
Windows Form <xref:System.Windows.Forms.TreeView> 控制項會在其 <xref:System.Windows.Forms.TreeView.Nodes%2A> 集合中儲存最上層節點。  每個 <xref:System.Windows.Forms.TreeNode> 也有其自己的 <xref:System.Windows.Forms.TreeNode.Nodes%2A> 集合以儲存子節點。  這兩種集合的屬性都是 <xref:System.Windows.Forms.TreeNodeCollection> 型別，可以提供標準的集合成員讓您在節點階層架構的單一層級中加入、移除和重新整理節點。  
  
### 若要以程式設計方式加入節點  
  
1.  使用樹狀檢視的 <xref:System.Windows.Forms.TreeView.Nodes%2A> 屬性的 <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> 方法。  
  
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
  
### 若要以程式設計方式移除節點  
  
1.  使用樹狀檢視的 <xref:System.Windows.Forms.TreeView.Nodes%2A> 屬性的 <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> 方法，移除單一節點，或使用 <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> 方法，清除所有節點。  
  
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
  
## 請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [TreeView 控制項概觀](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [如何：設定 Windows Form TreeView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)   
 [如何：逐一查看 Windows Form TreeView 控制項的所有節點](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [如何：判斷按下哪個 TreeView 節點](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
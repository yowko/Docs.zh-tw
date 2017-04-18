---
title: "如何：逐一查看 Windows Form TreeView 控制項的所有節點 | Microsoft Docs"
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
  - "TreeView 控制項中的樹狀節點, 逐一查看"
  - "TreeView 控制項 [Windows Form], 重複節點"
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：逐一查看 Windows Form TreeView 控制項的所有節點
有時候這在檢查 Windows Form <xref:System.Windows.Forms.TreeView> 控制項的每個節點，以便對節點值進行某些計算時非常有用。  這項作業可以利用逐一查看每個樹狀集合物件 \(Collection\) 中每個節點的遞迴程序 \(C\# 和 C\+\+ 中為遞迴方法\) 來完成。  
  
 樹狀檢視中的每個 <xref:System.Windows.Forms.TreeNode> 物件都有屬性，您可以使用這些屬性來巡覽樹狀檢視：<xref:System.Windows.Forms.TreeNode.FirstNode%2A>、<xref:System.Windows.Forms.TreeNode.LastNode%2A>、<xref:System.Windows.Forms.TreeNode.NextNode%2A>、<xref:System.Windows.Forms.TreeNode.PrevNode%2A> 和 <xref:System.Windows.Forms.TreeNode.Parent%2A>。  <xref:System.Windows.Forms.TreeNode.Parent%2A> 屬性的值是目前節點的父節點。  如果有子節點時，目前節點的子節點將列於 <xref:System.Windows.Forms.TreeNode.Nodes%2A> 屬性中。  <xref:System.Windows.Forms.TreeView> 控制項本身具有 <xref:System.Windows.Forms.TreeView.TopNode%2A> 屬性，這是整個樹狀檢視的根 \(Root\) 節點。  
  
### 若要逐一查看 TreeView 控制項的所有節點  
  
1.  建立測試每個節點的遞迴程序 \(C\# 和 C\+\+ 中為遞迴方法\)。  
  
2.  呼叫此程序。  
  
     下列範例顯示如何列印每個 <xref:System.Windows.Forms.TreeNode> 物件的 <xref:System.Windows.Forms.TreeNode.Text%2A> 屬性：  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## 請參閱  
 [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [Recursive Procedures](../Topic/Recursive%20Procedures%20\(Visual%20Basic\).md)
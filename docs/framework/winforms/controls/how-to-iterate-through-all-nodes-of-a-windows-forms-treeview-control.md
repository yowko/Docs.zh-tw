---
title: 作法：逐一查看 Windows Forms TreeView 控制項的所有節點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
ms.openlocfilehash: 00a0f19803967f02795e3eade767786eecc1f4dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966552"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>HOW TO：逐一查看 Windows Forms TreeView 控制項的所有節點
檢查 Windows Forms <xref:System.Windows.Forms.TreeView>控制項中的每個節點, 以便對節點值執行一些計算, 有時會很有用。 使用遞迴程序 (採用 C# 和 C++ 的遞迴方法) 來逐一查看每個樹狀集合中的每個節點，即可完成這項作業。  
  
 樹<xref:System.Windows.Forms.TreeNode>視圖中的每個物件都有屬性, 可讓您用來導覽樹<xref:System.Windows.Forms.TreeNode.FirstNode%2A>視圖<xref:System.Windows.Forms.TreeNode.LastNode%2A>: <xref:System.Windows.Forms.TreeNode.NextNode%2A>、 <xref:System.Windows.Forms.TreeNode.PrevNode%2A>、、 <xref:System.Windows.Forms.TreeNode.Parent%2A>和。 <xref:System.Windows.Forms.TreeNode.Parent%2A>屬性的值是目前節點的父節點。 目前節點的子節點 (如果有的話) 會列在其<xref:System.Windows.Forms.TreeNode.Nodes%2A>屬性中。 <xref:System.Windows.Forms.TreeView>控制項本身<xref:System.Windows.Forms.TreeView.TopNode%2A>具有屬性, 這是整個樹狀檢視的根節點。  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>逐一查看 TreeView 控制項的所有節點  
  
1. 建立用以測試每個節點的遞迴程序 (採用 C# 和 C++ 的遞迴方法)。  
  
2. 呼叫此程序。  
  
     下列範例顯示如何列印每個<xref:System.Windows.Forms.TreeNode>物件的<xref:System.Windows.Forms.TreeNode.Text%2A>屬性:  
  
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
  
## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)
- [遞迴程序](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)

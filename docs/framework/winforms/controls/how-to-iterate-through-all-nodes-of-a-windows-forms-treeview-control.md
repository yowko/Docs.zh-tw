---
title: HOW TO：逐一查看 Windows Forms TreeView 控制項的所有節點
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
ms.openlocfilehash: c6345ab5e5d4f4e480bb2724e7a1d795de2bef5d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651847"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>HOW TO：逐一查看 Windows Forms TreeView 控制項的所有節點
可能會很有用來檢查 Windows Forms 中的每個節點<xref:System.Windows.Forms.TreeView>才能執行一些計算節點值上的控制項。 使用遞迴程序 (採用 C# 和 C++ 的遞迴方法) 來逐一查看每個樹狀集合中的每個節點，即可完成這項作業。  
  
 每個<xref:System.Windows.Forms.TreeNode>樹狀檢視中的物件具有可供您瀏覽樹狀檢視中的屬性： <xref:System.Windows.Forms.TreeNode.FirstNode%2A>， <xref:System.Windows.Forms.TreeNode.LastNode%2A>， <xref:System.Windows.Forms.TreeNode.NextNode%2A>， <xref:System.Windows.Forms.TreeNode.PrevNode%2A>，和<xref:System.Windows.Forms.TreeNode.Parent%2A>。 值<xref:System.Windows.Forms.TreeNode.Parent%2A>屬性是目前節點的父節點。 子節點的目前節點中，如果有的話，會列在其<xref:System.Windows.Forms.TreeNode.Nodes%2A>屬性。 <xref:System.Windows.Forms.TreeView>控制項本身具有<xref:System.Windows.Forms.TreeView.TopNode%2A>屬性，這是整個樹狀結構檢視的根節點。  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>逐一查看 TreeView 控制項的所有節點  
  
1.  建立用以測試每個節點的遞迴程序 (採用 C# 和 C++ 的遞迴方法)。  
  
2.  呼叫此程序。  
  
     下列範例示範如何列印每個<xref:System.Windows.Forms.TreeNode>物件的<xref:System.Windows.Forms.TreeNode.Text%2A>屬性：  
  
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
- [TreeView 控制項](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [遞迴程序](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)

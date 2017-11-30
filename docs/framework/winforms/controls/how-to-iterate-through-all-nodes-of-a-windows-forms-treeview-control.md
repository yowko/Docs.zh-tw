---
title: "如何：逐一查看 Windows Forms TreeView 控制項的所有節點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 057612bfb28333df0aebaa5ca19555f4c4951687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="72de7-102">如何：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="72de7-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="72de7-103">可能會很有用，檢查 Windows Form 中的每個節點<xref:System.Windows.Forms.TreeView>才能執行某些計算節點值上的控制項。</span><span class="sxs-lookup"><span data-stu-id="72de7-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="72de7-104">使用遞迴程序 (採用 C# 和 C++ 的遞迴方法) 來逐一查看每個樹狀集合中的每個節點，即可完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="72de7-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="72de7-105">每個<xref:System.Windows.Forms.TreeNode>樹狀檢視中的物件具有屬性可讓您瀏覽樹狀目錄檢視： <xref:System.Windows.Forms.TreeNode.FirstNode%2A>， <xref:System.Windows.Forms.TreeNode.LastNode%2A>， <xref:System.Windows.Forms.TreeNode.NextNode%2A>， <xref:System.Windows.Forms.TreeNode.PrevNode%2A>，和<xref:System.Windows.Forms.TreeNode.Parent%2A>。</span><span class="sxs-lookup"><span data-stu-id="72de7-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="72de7-106">值<xref:System.Windows.Forms.TreeNode.Parent%2A>屬性是目前節點的父節點。</span><span class="sxs-lookup"><span data-stu-id="72de7-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="72de7-107">子節點的目前節點中，如果有的話，會列出其<xref:System.Windows.Forms.TreeNode.Nodes%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="72de7-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="72de7-108"><xref:System.Windows.Forms.TreeView>控制項本身具有<xref:System.Windows.Forms.TreeView.TopNode%2A>屬性，這是整個樹狀結構檢視的根節點。</span><span class="sxs-lookup"><span data-stu-id="72de7-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="72de7-109">逐一查看 TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="72de7-109">To iterate through all nodes of the TreeView control</span></span>  
  
1.  <span data-ttu-id="72de7-110">建立用以測試每個節點的遞迴程序 (採用 C# 和 C++ 的遞迴方法)。</span><span class="sxs-lookup"><span data-stu-id="72de7-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2.  <span data-ttu-id="72de7-111">呼叫此程序。</span><span class="sxs-lookup"><span data-stu-id="72de7-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="72de7-112">下列範例示範如何列印每個<xref:System.Windows.Forms.TreeNode>物件的<xref:System.Windows.Forms.TreeNode.Text%2A>屬性：</span><span class="sxs-lookup"><span data-stu-id="72de7-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72de7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72de7-113">See Also</span></span>  
 [<span data-ttu-id="72de7-114">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="72de7-114">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="72de7-115">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="72de7-115">Recursive Procedures</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)

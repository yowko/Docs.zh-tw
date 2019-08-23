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
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="1c201-102">HOW TO：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="1c201-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="1c201-103">檢查 Windows Forms <xref:System.Windows.Forms.TreeView>控制項中的每個節點, 以便對節點值執行一些計算, 有時會很有用。</span><span class="sxs-lookup"><span data-stu-id="1c201-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="1c201-104">使用遞迴程序 (採用 C# 和 C++ 的遞迴方法) 來逐一查看每個樹狀集合中的每個節點，即可完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="1c201-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="1c201-105">樹<xref:System.Windows.Forms.TreeNode>視圖中的每個物件都有屬性, 可讓您用來導覽樹<xref:System.Windows.Forms.TreeNode.FirstNode%2A>視圖<xref:System.Windows.Forms.TreeNode.LastNode%2A>: <xref:System.Windows.Forms.TreeNode.NextNode%2A>、 <xref:System.Windows.Forms.TreeNode.PrevNode%2A>、、 <xref:System.Windows.Forms.TreeNode.Parent%2A>和。</span><span class="sxs-lookup"><span data-stu-id="1c201-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="1c201-106"><xref:System.Windows.Forms.TreeNode.Parent%2A>屬性的值是目前節點的父節點。</span><span class="sxs-lookup"><span data-stu-id="1c201-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="1c201-107">目前節點的子節點 (如果有的話) 會列在其<xref:System.Windows.Forms.TreeNode.Nodes%2A>屬性中。</span><span class="sxs-lookup"><span data-stu-id="1c201-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="1c201-108"><xref:System.Windows.Forms.TreeView>控制項本身<xref:System.Windows.Forms.TreeView.TopNode%2A>具有屬性, 這是整個樹狀檢視的根節點。</span><span class="sxs-lookup"><span data-stu-id="1c201-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="1c201-109">逐一查看 TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="1c201-109">To iterate through all nodes of the TreeView control</span></span>  
  
1. <span data-ttu-id="1c201-110">建立用以測試每個節點的遞迴程序 (採用 C# 和 C++ 的遞迴方法)。</span><span class="sxs-lookup"><span data-stu-id="1c201-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2. <span data-ttu-id="1c201-111">呼叫此程序。</span><span class="sxs-lookup"><span data-stu-id="1c201-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="1c201-112">下列範例顯示如何列印每個<xref:System.Windows.Forms.TreeNode>物件的<xref:System.Windows.Forms.TreeNode.Text%2A>屬性:</span><span class="sxs-lookup"><span data-stu-id="1c201-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c201-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c201-113">See also</span></span>

- [<span data-ttu-id="1c201-114">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="1c201-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="1c201-115">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="1c201-115">Recursive Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)

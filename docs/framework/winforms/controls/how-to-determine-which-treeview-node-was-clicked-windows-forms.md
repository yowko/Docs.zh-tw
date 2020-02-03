---
title: 如何：判斷按下哪個 TreeView 節點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 7a0e2b69bbec0eb03d40bee2c8e2d4bc9c3558f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742008"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="e6ba5-102">如何：判斷按下哪個 TreeView 節點 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e6ba5-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="e6ba5-103">使用 Windows Forms <xref:System.Windows.Forms.TreeView> 控制項時，常見的工作是判斷按一下的節點，並適當地回應。</span><span class="sxs-lookup"><span data-stu-id="e6ba5-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="e6ba5-104">判斷按一下的 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="e6ba5-104">To determine which TreeView node was clicked</span></span>  
  
1. <span data-ttu-id="e6ba5-105">使用 <xref:System.EventArgs> 物件，以傳回所按下節點物件的參考。</span><span class="sxs-lookup"><span data-stu-id="e6ba5-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2. <span data-ttu-id="e6ba5-106">檢查 <xref:System.Windows.Forms.TreeViewEventArgs> 類別（其中包含與事件相關的資料），以判斷按一下哪一個節點。</span><span class="sxs-lookup"><span data-stu-id="e6ba5-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="e6ba5-107">或者，您可以使用 <xref:System.Windows.Forms.Control.MouseDown> 或 <xref:System.Windows.Forms.Control.MouseUp> 事件的 <xref:System.Windows.Forms.MouseEventArgs> 來取得 <xref:System.Drawing.Point.X%2A> 和 <xref:System.Drawing.Point.Y%2A> 座標值，這是發生點擊的 <xref:System.Drawing.Point>。</span><span class="sxs-lookup"><span data-stu-id="e6ba5-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="e6ba5-108">然後，使用 <xref:System.Windows.Forms.TreeView> 控制項的 <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> 方法來判斷按一下的節點。</span><span class="sxs-lookup"><span data-stu-id="e6ba5-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ba5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6ba5-109">See also</span></span>

- [<span data-ttu-id="e6ba5-110">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="e6ba5-110">TreeView Control</span></span>](treeview-control-windows-forms.md)

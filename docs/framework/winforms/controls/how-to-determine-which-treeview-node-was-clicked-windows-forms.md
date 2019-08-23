---
title: 作法：判斷按一下哪個 TreeView 節點 (Windows Forms)
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
ms.openlocfilehash: ab93158daf987e2f19516b8fb3abf80bfe79a12c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967336"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="131a8-102">作法：判斷按一下哪個 TreeView 節點 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="131a8-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="131a8-103">使用 Windows Forms <xref:System.Windows.Forms.TreeView>控制項時, 常見的工作是判斷按一下的節點, 並適當地回應。</span><span class="sxs-lookup"><span data-stu-id="131a8-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="131a8-104">判斷按一下的 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="131a8-104">To determine which TreeView node was clicked</span></span>  
  
1. <span data-ttu-id="131a8-105"><xref:System.EventArgs>使用物件來傳回所按節點物件的參考。</span><span class="sxs-lookup"><span data-stu-id="131a8-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2. <span data-ttu-id="131a8-106">檢查<xref:System.Windows.Forms.TreeViewEventArgs>類別 (其中包含與事件相關的資料), 以判斷按一下哪一個節點。</span><span class="sxs-lookup"><span data-stu-id="131a8-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    > <span data-ttu-id="131a8-107"><xref:System.Windows.Forms.MouseEventArgs> <xref:System.Windows.Forms.Control.MouseUp> 或者,<xref:System.Drawing.Point.Y%2A>您可以使用或事件<xref:System.Drawing.Point>的來取得的和座標值,這是按一下發生的位置。<xref:System.Drawing.Point.X%2A> <xref:System.Windows.Forms.Control.MouseDown></span><span class="sxs-lookup"><span data-stu-id="131a8-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="131a8-108">然後, 使用<xref:System.Windows.Forms.TreeView>控制項的<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>方法來判斷按一下的節點。</span><span class="sxs-lookup"><span data-stu-id="131a8-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131a8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="131a8-109">See also</span></span>

- [<span data-ttu-id="131a8-110">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="131a8-110">TreeView Control</span></span>](treeview-control-windows-forms.md)

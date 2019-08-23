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
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>作法：判斷按一下哪個 TreeView 節點 (Windows Forms)
使用 Windows Forms <xref:System.Windows.Forms.TreeView>控制項時, 常見的工作是判斷按一下的節點, 並適當地回應。  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>判斷按一下的 TreeView 節點  
  
1. <xref:System.EventArgs>使用物件來傳回所按節點物件的參考。  
  
2. 檢查<xref:System.Windows.Forms.TreeViewEventArgs>類別 (其中包含與事件相關的資料), 以判斷按一下哪一個節點。  
  
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
    > <xref:System.Windows.Forms.MouseEventArgs> <xref:System.Windows.Forms.Control.MouseUp> 或者,<xref:System.Drawing.Point.Y%2A>您可以使用或事件<xref:System.Drawing.Point>的來取得的和座標值,這是按一下發生的位置。<xref:System.Drawing.Point.X%2A> <xref:System.Windows.Forms.Control.MouseDown> 然後, 使用<xref:System.Windows.Forms.TreeView>控制項的<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>方法來判斷按一下的節點。  
  
## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)

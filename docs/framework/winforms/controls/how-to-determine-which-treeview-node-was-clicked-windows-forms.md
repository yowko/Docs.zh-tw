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
ms.openlocfilehash: d960eaae2aa479e0be74e9a5e4fdbfec8ff411c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182181"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>如何：判斷按下哪個 TreeView 節點 (Windows Form)
使用 Windows 表單<xref:System.Windows.Forms.TreeView>控制項時，常見任務是確定按一下了哪個節點，並適當地回應。  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>確定按一下了哪個樹狀檢視節點  
  
1. 使用<xref:System.EventArgs>物件返回對按一下的節點物件的引用。  
  
2. 通過檢查包含與事件相關的資料的類<xref:System.Windows.Forms.TreeViewEventArgs>確定按一下了哪個節點。  
  
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
    > <xref:System.Windows.Forms.MouseEventArgs>作為替代方法，可以使用<xref:System.Windows.Forms.Control.MouseDown>或<xref:System.Windows.Forms.Control.MouseUp>事件獲取發生按一下<xref:System.Drawing.Point.X%2A><xref:System.Drawing.Point.Y%2A><xref:System.Drawing.Point>的位置的 和 座標值。 然後，<xref:System.Windows.Forms.TreeView>使用控制項<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>的方法確定按一下了哪個節點。  
  
## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)

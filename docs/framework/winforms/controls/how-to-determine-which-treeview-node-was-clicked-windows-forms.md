---
title: HOW TO：判斷按下哪個 TreeView 節點 (Windows Form)
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
ms.openlocfilehash: 71f13c7b160822c92475d4d03e923b40d4f0454d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771042"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>HOW TO：判斷按下哪個 TreeView 節點 (Windows Form)
使用 Windows Form 時<xref:System.Windows.Forms.TreeView>控制，常見的工作是要判斷哪一個節點已按下，並適當地回應。  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>若要判斷按下哪個 TreeView 節點  
  
1. 使用<xref:System.EventArgs>来傳回的已按下 的節點物件的參考物件。  
  
2. 判斷哪一個節點已按下藉由檢查<xref:System.Windows.Forms.TreeViewEventArgs>類別，其中包含與事件相關資料。  
  
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
    >  或者，您可以使用<xref:System.Windows.Forms.MouseEventArgs>的<xref:System.Windows.Forms.Control.MouseDown>或是<xref:System.Windows.Forms.Control.MouseUp>事件，以取得<xref:System.Drawing.Point.X%2A>並<xref:System.Drawing.Point.Y%2A>座標值的<xref:System.Drawing.Point>發生按一下。 然後，使用<xref:System.Windows.Forms.TreeView>控制項的<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>方法，以判斷按下哪一個節點。  
  
## <a name="see-also"></a>另請參閱

- [TreeView 控制項](treeview-control-windows-forms.md)

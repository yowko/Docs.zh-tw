---
title: 逐步解說：執行拖放作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 265e6d4f9e3370d28a18b86dea983bb0b556be41
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746788"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>逐步解說：在 Windows Form 中執行拖放作業
若要在以 Windows 為基礎的應用程式內執行拖放作業，您必須處理一系列的事件，尤其是 <xref:System.Windows.Forms.Control.DragEnter>、<xref:System.Windows.Forms.Control.DragLeave>和 <xref:System.Windows.Forms.Control.DragDrop> 事件。 使用這些事件的事件引數中所提供的資訊，即可輕鬆地運用拖放作業。  
  
## <a name="dragging-data"></a>拖曳資料  
 所有拖放作業都是從拖曳開始。 當拖曳開始時，用來啟用收集資料的功能會在 <xref:System.Windows.Forms.Control.DoDragDrop%2A> 方法中執行。  
  
 在下列範例中，會使用 <xref:System.Windows.Forms.Control.MouseDown> 事件來啟動拖曳作業，因為它是最直覺化的（大部分的拖放動作都是以按下滑鼠按鍵的方式開始）。 不過，請記住，可以使用任何事件來啟始拖放程序。  
  
> [!NOTE]
> 特定控制項會有自訂拖曳特定事件。 例如，<xref:System.Windows.Forms.ListView> 和 <xref:System.Windows.Forms.TreeView> 控制項都有 <xref:System.Windows.Forms.TreeView.ItemDrag> 事件。  
  
#### <a name="to-start-a-drag-operation"></a>啟動拖曳作業  
  
1. 在將開始拖曳之控制項的 <xref:System.Windows.Forms.Control.MouseDown> 事件中，使用 `DoDragDrop` 方法來設定要拖曳的資料，而允許的效果將會有。 如需詳細資訊，請參閱<xref:System.Windows.Forms.DragEventArgs.Data%2A>和<xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。  
  
     下列範例示範如何啟始拖曳作業。 拖曳開始位置為 <xref:System.Windows.Forms.Button> 控制項的控制項，所拖曳的資料是代表 <xref:System.Windows.Forms.Button> 控制項之 <xref:System.Windows.Forms.Control.Text%2A> 屬性的字串，而允許的效果是複製或移動。  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > 任何資料都可用來做為 `DoDragDrop` 方法中的參數;在上述範例中，會使用 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性（而不是將值硬式編碼或從資料集抓取資料），因為屬性與從拖曳的位置（<xref:System.Windows.Forms.Button> 控制項）有關。 當您將拖放作業併入 Windows 應用程式時，請記住這點。  
  
 當拖曳操作生效時，您可以處理 <xref:System.Windows.Forms.Control.QueryContinueDrag> 事件，這會「要求許可權」系統繼續拖曳作業。 處理這個方法時，您也可以呼叫將會影響拖曳作業的方法，例如，當游標停留在 <xref:System.Windows.Forms.TreeView> 控制項中時，展開 <xref:System.Windows.Forms.TreeNode>。  
  
## <a name="dropping-data"></a>卸除資料  
 當您開始將資料從某個位置拖曳至 Windows Forms 或控制項時，當然會想要將它卸除到某個位置。 游標在通過已正確設定可卸除資料的表單或控制項的某個區域時會變更。 Windows Form 或控制項內的任何區域都可以藉由設定 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性和處理 <xref:System.Windows.Forms.Control.DragEnter> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件，來接受捨棄的資料。  
  
#### <a name="to-perform-a-drop"></a>執行卸除  
  
1. 將 [<xref:System.Windows.Forms.Control.AllowDrop%2A>] 屬性設定為 [true]。  
  
2. 在將發生卸載之控制項的 `DragEnter` 事件中，請確定所拖曳的資料屬於可接受的類型（在此案例中為 <xref:System.Windows.Forms.Control.Text%2A>）。 然後，程式碼會設定當 <xref:System.Windows.Forms.DragDropEffects> 列舉中的值發生卸載時，將會發生的效果。 如需詳細資訊，請參閱<xref:System.Windows.Forms.DragEventArgs.Effect%2A>。  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > 您可以指定自己的物件做為 <xref:System.Windows.Forms.DataObject.SetData%2A> 方法的 <xref:System.Object> 參數，以定義您自己的 <xref:System.Windows.Forms.DataFormats>。 這麼做時，請確定可序列化所指定的物件。 如需詳細資訊，請參閱<xref:System.Runtime.Serialization.ISerializable>。  
  
3. 在將發生卸載之控制項的 <xref:System.Windows.Forms.Control.DragDrop> 事件中，使用 <xref:System.Windows.Forms.DataObject.GetData%2A> 方法來抓取要拖曳的資料。 如需詳細資訊，請參閱<xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。  
  
     在下列範例中，<xref:System.Windows.Forms.TextBox> 控制項是要拖曳至的控制項（將會在其中進行卸載）。 程式碼會將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為等於所拖曳的資料。  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > 此外，您可以使用 [<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>] 屬性，如此一來，根據拖放作業期間所按下的按鍵，就會發生某些效果（例如，在按 CTRL 鍵時複製拖曳的資料）。  
  
## <a name="see-also"></a>請參閱

- [操作說明：將資料新增至剪貼簿](how-to-add-data-to-the-clipboard.md)
- [操作說明：從剪貼簿擷取資料](how-to-retrieve-data-from-the-clipboard.md)
- [拖放作業和剪貼簿支援](drag-and-drop-operations-and-clipboard-support.md)

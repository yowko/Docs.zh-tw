---
title: 演練：執行拖放操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182436"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>逐步解說：在 Windows Form 中執行拖放作業
要在基於 Windows 的應用程式中執行拖放操作，必須處理一系列事件，其中最著名的是<xref:System.Windows.Forms.Control.DragEnter>，<xref:System.Windows.Forms.Control.DragLeave>和<xref:System.Windows.Forms.Control.DragDrop>事件。 使用這些事件的事件引數中所提供的資訊，即可輕鬆地運用拖放作業。  
  
## <a name="dragging-data"></a>拖曳資料  
 所有拖放作業都是從拖曳開始。 在<xref:System.Windows.Forms.Control.DoDragDrop%2A>方法中實現了在方法中實現在拖動開始時啟用收集資料的功能。  
  
 在下面的示例中，<xref:System.Windows.Forms.Control.MouseDown>該事件用於啟動拖動操作，因為它是最直觀的（大多數拖放操作從按下滑鼠按鍵開始）。 不過，請記住，可以使用任何事件來啟始拖放程序。  
  
> [!NOTE]
> 特定控制項會有自訂拖曳特定事件。 <xref:System.Windows.Forms.ListView>和<xref:System.Windows.Forms.TreeView>控制項，例如，有一個<xref:System.Windows.Forms.TreeView.ItemDrag>事件。  
  
#### <a name="to-start-a-drag-operation"></a>啟動拖曳作業  
  
1. 對於將開始<xref:System.Windows.Forms.Control.MouseDown>拖動的控制項，使用`DoDragDrop`方法設置要拖動的資料，並且允許的效果拖動將具有。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 和 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。  
  
     下列範例示範如何啟始拖曳作業。 拖動開始的控制項是<xref:System.Windows.Forms.Button>控制項，要拖動的資料是表示控制項<xref:System.Windows.Forms.Control.Text%2A>屬性的<xref:System.Windows.Forms.Button>字串，允許的效果是複製或移動。  
  
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
    > 任何資料都可以用作`DoDragDrop`方法中的參數;在上面的示例中，使用了<xref:System.Windows.Forms.Control.Text%2A><xref:System.Windows.Forms.Button>控制項的屬性（而不是硬編碼值或從資料集檢索資料），因為該屬性與從中拖動的位置（<xref:System.Windows.Forms.Button>控制項）相關。 當您將拖放作業併入 Windows 應用程式時，請記住這點。  
  
 當拖動操作有效時，您可以處理<xref:System.Windows.Forms.Control.QueryContinueDrag>事件，該事件"請求"系統的許可權以繼續拖動操作。 處理此方法時，調用對拖動操作有影響的方法也是適當的點，例如當游標懸停在<xref:System.Windows.Forms.TreeNode><xref:System.Windows.Forms.TreeView>控制項上時展開 控制項中的 。  
  
## <a name="dropping-data"></a>卸除資料  
 當您開始將資料從某個位置拖曳至 Windows Forms 或控制項時，當然會想要將它卸除到某個位置。 游標在通過已正確設定可卸除資料的表單或控制項的某個區域時會變更。 可以通過設置<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性和處理<xref:System.Windows.Forms.Control.DragEnter>和<xref:System.Windows.Forms.Control.DragDrop>事件來使 Windows 表單或控制項中的任何區域接受丟棄的資料。  
  
#### <a name="to-perform-a-drop"></a>執行卸除  
  
1. 將<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設置為 true。  
  
2. 對於`DragEnter`發生丟棄的控制項，請確保拖動的資料是可接受的類型（在本例中為<xref:System.Windows.Forms.Control.Text%2A>）。 然後，代碼設置在枚舉中<xref:System.Windows.Forms.DragDropEffects>放置到值時將發生的效果。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.DragEventArgs.Effect%2A>。  
  
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
    > 可以通過將自己的物件指定<xref:System.Windows.Forms.DataFormats>為方法的<xref:System.Object>參數來<xref:System.Windows.Forms.DataObject.SetData%2A>定義您自己的物件。 這麼做時，請確定可序列化所指定的物件。 如需詳細資訊，請參閱 <xref:System.Runtime.Serialization.ISerializable>。  
  
3. 對於<xref:System.Windows.Forms.Control.DragDrop>發生放置的控制項，使用 方法<xref:System.Windows.Forms.DataObject.GetData%2A>檢索要拖動的資料。 如需詳細資訊，請參閱 <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。  
  
     在下面的示例中，<xref:System.Windows.Forms.TextBox>控制項是拖動到（將發生丟棄的位置）的控制項。 代碼設置控制項<xref:System.Windows.Forms.Control.Text%2A>的屬性<xref:System.Windows.Forms.TextBox>等於要拖動的資料。  
  
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
    > 此外，您可以使用 該<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>屬性，以便根據拖放操作期間按下的鍵，會發生某些效果（例如，在按下 CTRL 鍵時複製拖動的資料是標準）。  
  
## <a name="see-also"></a>另請參閱

- [如何：將資料加入至剪貼簿](how-to-add-data-to-the-clipboard.md)
- [如何：從剪貼簿擷取資料](how-to-retrieve-data-from-the-clipboard.md)
- [拖放作業和剪貼簿支援](drag-and-drop-operations-and-clipboard-support.md)
